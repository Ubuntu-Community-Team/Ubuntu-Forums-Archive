---
title: "PHPBB Active box has blue border"
date: 2008-10-22
forum: Programming Talk
---

### Post by Tux.Ice on 2008-10-22
Anybody ever used PHPBB/a website that adds a color border on the box your cursor is currently in (also happens with the webkit engine)

anybody know how to make this happen with PHP/CSS/JAVASCRIPT?

Thanks.

---

### Post by Tux.Ice on 2008-10-23
bump

---

### Post by Paul41 on 2008-10-23
You could do something like this.

```
<html>
<head>
<style>
.shaded {
	border-color: #FF0000;
}
.normal {
	border: 1px solid  #c0c0c0;
}
</style>
<script type="text/javascript">
function changeClass(ele,classType) {
	document.getElementById([ele]).className = classType;
}

</script>
</head>
<body>
<input type="text" id="box" onmouseover="changeClass('box', 'shaded');" onmouseout="changeClass('box', 'normal');">
</body>
</html>
```

---

