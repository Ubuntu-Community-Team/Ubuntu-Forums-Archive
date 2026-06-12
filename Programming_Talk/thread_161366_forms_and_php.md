---
title: "forms and php"
date: 2006-04-16
forum: Programming Talk
---

### Post by orlox on 2006-04-16
Hi, I'm trying to write a login form with php, but I can't get it to work. Right now I'm simply trying to make that the php script, after logging in doesn't write the login form. It doesn't check that the fields are valid, or do a real login at all. Basically, my script has this statement to handle that:

[PHP]
<?php

print_login(){...}
print_logged(){...}

if (empty ($action))
    $action = 0;
swicth ($action)
{
case 0
    print_login ();
    break;
case 1
    print_logged ();
    break;
}
?>
[/PHP] 
where print_login() prints the login form, and print_logged() prints a "logged as username" instead. the login form that's printed is defined as this:
[HTML]
...
<form method="post" action="?action=1">
...
[/HTML]

so that when the user submits the form, $action is equal to 1 and the script prints the corresponding "logged" page. But it simply wont work, because the $action variable remains as zero after submitting the form, and the script just prints the page with the login form...

Is there anything wrong with what I show here?
Or should it work like that, and maybe I have a problem elsewhere...?

---

### Post by LordHunter317 on 2006-04-16
You need to read a basic PHP tutorial and a basic HTTP tutorial:[list][*]Unless you have register_globals enabled, a variable of the form $name will never be set in response to the values of the HTTP request.  This is intentional as a security protection.   They will be in the $POST, $GET, and $REQUEST global associative arrays.[*]You're attempting to pass a value in GET fashion to a POST form.  This can work if you know what you're doing, but it's clear here it's not desirable.[*]You don't want to be passing the action to perform anyway, *because it can be spoofed by the user.*  The only thing you want returned from the user is the username and password (or whatever credentials you're using).  You then attempt the login and print out whatever response is correct based on that action.  Your page design is totally wrong.[/list]

---

### Post by orlox on 2006-04-17
jeje, thanks for that answer. I know what i'm doing is totally not correct, but i'm just trying to learn how to use this things...I'll be sure to check on those things you said...

---

### Post by LordHunter317 on 2006-04-17
[QUOTE=orlox]jeje, thanks for that answer. I know what i'm doing is totally not correct,[ but i'm just trying to learn how to use this things...[/quote]And frankly, if you're not going to learn the right way, it'd be better to not learn at all.

---

