---
title: "does javascript allow taking keystrokes"
date: 2009-06-24
forum: Programming Talk
---

### Post by dracule on 2009-06-24
Hey all, 

I was writing a plug-in for firefox and I thought I remembered a long time ago that javascript allowed for the taking of keystrokes when not focused on a text field.

I was just wondering if it is still a common practice or not because my plugin would take key strokes when users were not focused on text fields and I didnt want to break compatibility

---

### Post by jespdj on 2009-06-25
You can set a function on the keydown event of the document. I don't know how this will work in a Firefox plug-in.
[html]<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	<title>Test</title>
</head>
<body>
<script type="text/javascript">
document.onkeydown = function(event) {
	alert(event.keyCode);
};
</script>
</body>
</html>
[/html]

---

