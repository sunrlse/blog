---
title: 节流
date: 2018-09-05 16:55:58
tags: js
---
### 节流函数

``` Javascript
    function throttle(fn, param, context, delay, mustApplyTime) {
		clearTimeout(fn.timer);
        var param = param || {},
            context = context || null,
            delay = delay || 500,
            mustApplyTime = mustApplyTime || 1000;
		fn._cur = Date.now();
		if (!fn._start) {
			fn._start = fn._cur;
		}
		if (fn._cur - fn._start > mustApplyTime) { 
			fn.call(context, param);
			fn._start = fn._cur;
		} else {
			fn.timer = setTimeout(function() {
			fn.call(context, param);
			}, delay);
		}
	}
```