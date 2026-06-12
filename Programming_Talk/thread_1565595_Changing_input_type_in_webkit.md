---
title: "Changing input type in webkit"
date: 2010-09-01
forum: Programming Talk
---

### Post by durand on 2010-09-01
Hi,

Webkit seems to have a bug where you can't change the input type with javascript. Does anyone know of a solution for this?

```

<html>
<body>
<form action="/">
<input id="form" type="text" /></form>
<script type="text/javascript">
alert(document.getElementById('form').type);
document.getElementById('form').setAttribute('type', 'file');
alert(document.getElementById('form').type);
</script>
</body>
</html>

```

The only alternative I can think of is to replace the input box with a new one but thats a bad workaround in my opinion.

---

