---
title: "Form submit button open a new window"
date: 2010-09-29
forum: Programming Talk
---

### Post by psycho5 on 2010-09-29
Very noob question cause I see it everywhere on websites, anyways...
 
I want to ask, how do I make a "submit" button on a form open a page in a new window? I've got

 <form method="link" action="page.html"><type="submit" value="Submit></form>

but it doesn't open in a new window. I read that I need to use javascript for that, but then how to put that into a form submit link?

<SCRIPT LANGUAGE="javascript">
<!--
window.open ('page.html', 'newwindow', config='height=100,
width=400, toolbar=no, menubar=no, scrollbars=no, resizable=no,
location=no, directories=no, status=no')
-->
</SCRIPT>

ty for your help

---

### Post by s.fox on 2010-09-29
Hello,

I would do something like this:

```
<form>
<input type="button" value="Button Link" onClick="parent.location='http://www.ubuntu.com'"/>
</form>
```-Silver Fox

---

### Post by psycho5 on 2010-09-29
Would that open the link in a new window?

```

<form>
<input type="button" value="Button Link" onClick="window.open ('page.html', 'newwindow', config='height=100,
width=400, toolbar=no, menubar=no, scrollbars=no, resizable=no,
location=no, directories=no, status=no')"/>
</form>

```

---

