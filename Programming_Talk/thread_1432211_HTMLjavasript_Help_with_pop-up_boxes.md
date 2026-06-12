---
title: "HTML/javasript Help with pop-up boxes"
date: 2010-03-17
forum: Programming Talk
---

### Post by hakermania on 2010-03-17
Hi, I' ve made this```
<html>
<body>
<head>
<script type="text/javascript">
function disp_prompt()
{
var fname=prompt("Please enter your name:","Your name Here")
{
alert("Hello (fname);! I am an alert box!");
}
}
</script>


<input type="button" onclick="disp_prompt()" value="Display a prompt box" />
<br /><br />

<div id="msg"></div>
</head>
</body>
</html> 
```
How can I show the variable fname to the alert box???
It says (fname); normally and not the setted name!

---

### Post by sxn on 2010-03-17
You need to change this:
```
alert("Hello (fname);! I am an alert box!");
```
to this:
```
alert("Hello " + fname + "! I am an alert box!");
```

---

### Post by Hellkeepa on 2010-03-17
HELLo!

You shoud also remove the curly brackets aroudn the alert statement, since "prompt()" is not a control structure.
Most of all, I'd recommend you to find a good JS tutorial, which explains the syntax of the language, and read through it. It will give you lots of useful information, and help avoid simple syntax errors like this.

Happy codin'!

---

### Post by era86 on 2010-03-17
w3schools

---

### Post by hakermania on 2010-03-19
> **era86 said:**
> w3schools

OK thx I found it!
GREAT TUTORIAL
Great work!
thx!

---

