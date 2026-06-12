---
title: "automated javascript function reference creation"
date: 2016-02-05
forum: Programming Talk
---

### Post by maclenin on 2016-02-05
I would like to automatically create 3 javascript function references...
```
f0();
f1();
f2();
```
...and assign them to DOM elements in this manner...
```
var i;
for (i = 0; i < 3; i += 1) {
document.getElementById("d" + i).onclick = (function (i) {return function () {"f" + i + "();"};})(i);
}
```
..to yield:
```
<div id = "d0" onclick = "f0();"></div>
<div id = "d1" onclick = "f1();"></div>
<div id = "d2" onclick = "f2();"></div>
```
No luck thus far. 

Thanks for any guidance!

---

### Post by Occasionally Correct on 2016-02-07
The problem is that the value of *onclick* needs to be something callable, and you're just returning a string from an anonymous function. Functions in Javascript are [first class citizens]("https://en.wikipedia.org/wiki/First-class_function"), so you could do something like this:

```
var funcs = [f0, f1, f2];

for (var i = 0; i < funcs.length; ++i) {
   document.getElementById("d" + i).onclick = funcs[i];
}
```

---

