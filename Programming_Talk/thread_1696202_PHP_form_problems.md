---
title: "PHP form problems"
date: 2011-02-27
forum: Programming Talk
---

### Post by Nova 107 on 2011-02-27
A friend and I are working on a web project. We have a working upload script but we need to restrict who can use it. I wrote a program that takes a "username" and "password" from a HTML form, but when I run it it gives me a 500 error. The script looks like this:
[PHP]<?php
$username = $_POST["uname"];
$password = $_POST["password"];

if(($username == "user")
&&($password == "1234"))
{
echo "The HTML upload form would apear here.";
} 
else
{
echo "Invalid userrname or password";
}
?>

[/PHP]
I've been checking the documentation and I can't find anything that would suggest the program is written wrong and my IDE doesnt catch anything either. The idea of the program is that if the "uname" from the form is equal to the predetermined username in the script and the "password" is also equal to the predetermined password in the script, it would echo the html upload form.

---

