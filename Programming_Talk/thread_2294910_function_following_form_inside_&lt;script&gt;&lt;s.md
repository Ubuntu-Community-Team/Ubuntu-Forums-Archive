---
title: "function following form inside &lt;script&gt;&lt;/script&gt;"
date: 2015-09-14
forum: Programming Talk
---

### Post by maclenin on 2015-09-14
Essentially, I am trying to get two functions to fire onresize from within a single <script> tag(s).

Given:
```
<!DOCTYPE html>
<html>
<head>
<script src = "ab.js"></script>
<!-- insert sample a or sample b-->
</head>
```

sample a: function b fires onresize, function a does not
```
<script>onresize = a</script>
<script>onresize = b</script>
```

sample b: function a fires onresize, function b does not
```
<script>onresize = a, b</script>
```
How do I get BOTH functions a and b to fire onresize from within the <script> tag?

Both a and b fire onload from within <body>:
```
<body onload = "a(); b();">
```

In a separate ab.js file I have:
```
function a() {
}

function b() {
}
```

Thanks for any guidance!

---

### Post by mreq on 2015-09-14
Use an anonymous function :)

```

onresize = function(){ a(); b(); } 

```

---

### Post by maclenin on 2015-09-15
**mreq!**

That'll play!

Thanks!

---

