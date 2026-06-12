---
title: "escape the onclick!"
date: 2015-08-29
forum: Programming Talk
---

### Post by maclenin on 2015-08-29
I have always fought (with) this one. Not certain how to (properly) deploy....

Given:

1. html
```
<div id = "a"></div>
<div id = "b" onclick = "change(?);"></div>
```
2. javascript
```
function change(id) {
document.getElementById(id).style.background = "orange";
}
```

How can I (properly) deploy onlick via <div> b to change the background color of <div> a?

I think it has to do with how I "escape" the a in the onclick call, but I am not certain how to wield my "\"'s and "'"'s....

NB: onclick = "change(id);" would work from within <div> a if I wished to click <div> a to change <div> a....

Thanks for any guidance!

---

### Post by Dimarchi on 2015-08-29
Is this what you were after? Note: *getElementById*, not *getElementBy*.

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<title>Background colour change</title>

<script>
function change(id)
{
    document.getElementById(id).style.background = "orange";
}
</script>

</head>

<body>

<div id = "a">A</div>
<div id = "b" onclick = "change('a');">B</div>

</body>
</html>
```
This is how I understood your question. If I misunderstood it, please let me know.

---

### Post by maclenin on 2015-08-29
**Dimarchi.**

Wow.

Yes, you understood, perfectly well (despite my (now corrected) typo).

Yep - that's, exactly, what I was after....

Pretty simple...um...it seems....

Thanks for the save.

---

