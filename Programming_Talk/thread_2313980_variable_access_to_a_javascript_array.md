---
title: "variable access to a javascript array"
date: 2016-02-17
forum: Programming Talk
---

### Post by maclenin on 2016-02-17
Is there a way to access the value of a javascript array using variables?

```
var a;

var b;

var ab = [1, 2, 3];

var c = a + b;

alert(c);
```

alert(c); yields NaN and not 1, 2, 3!

Is there a way to combine a and b to create a valid reference to the array ab?

Thanks for any guidance!

---

### Post by DaviesX on 2016-02-20
Sorry, not clear of what you are saying and what you want to achieve. What are a and b? And what you want them to refer to in your example? Both be arrays or strings?

---

### Post by maclenin on 2016-02-20
Essentially, this is what I was / am trying to achieve:

```
var ab = [1,2,3];

var c = window["a" + "b"];

alert(c);
```

...yielding 1,2,3 - with [thanks]("http://stackoverflow.com/questions/8836265/using-a-variable-value-to-call-an-array-element")!

---

