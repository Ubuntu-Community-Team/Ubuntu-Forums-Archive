---
title: "$_POST doesn't return anything (noob question on PHP and forms)"
date: 2008-12-27
forum: Programming Talk
---

### Post by Sprax on 2008-12-27
Hi

I can't seem to get $_POST to return anything. This *should* echo anything put in the text field, right? Well it returns nothing. It reloads the page but  doesn't echo anything. :confused:

All ideas much appreciated.

```
<?
echo $_POST['something'];
?>

<html>
<body>
<form name="test" action=<?$_SERVER['PHP_self']?>>
Write something: 
<input type="text" name="something">
<br>
<input type="submit" value="Send">
</form>
</body>
</html>
```

---

### Post by Sprax on 2008-12-27
oooooohh.... you have to inlude *method="post"* :idea:

well, nevermind... thanks

Dammit I've been staring at that for an hour and I come up with the solution a few min after I post the question. :)

---

