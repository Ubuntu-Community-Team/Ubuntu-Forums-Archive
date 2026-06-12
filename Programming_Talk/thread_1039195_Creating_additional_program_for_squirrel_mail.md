---
title: "Creating additional program for squirrel mail"
date: 2009-01-14
forum: Programming Talk
---

### Post by xiaomahe on 2009-01-14
Hai there, 

i have been trying to create an email system which can encrypt and decrypt the message send by the users. user can login to their mail by webmail (as it will be using SquirrelMail)

I am just wondering, is it possible for me to write an encryption program (in which it will be done in c++) and then later plug the program itself to the webmail system..

In plain words, i want to put an encryption function in the webmail which run this encryption program.

---

### Post by opscure on 2009-01-14
There is already a plugin for openPGP here:
[http://www.squirrelmail.org/plugin_view.php?id=153]("http://www.squirrelmail.org/plugin_view.php?id=153")

---

### Post by xiaomahe on 2009-01-14
i am trying to do my own for now..

i am just trying to study on how to create one of my own prgram

thnks for the help..

i just want to create a program whereby i don't need any installation to use the program

---

### Post by xiaomahe on 2009-01-14
Come on,, anyone can help me?

---

### Post by slavik on 2009-01-14
I don't see a problem with this ... you will have to check squirrelmail to be able to detect when it needs to call your C++ program. squirrelmail is written in PHP

---

### Post by xiaomahe on 2009-01-15
thnks slavik.

stil, is there any other way to do this? i just started on learning to integrate all the language together. Last time, i only wrote a program use in one language only.
but now, this is something new to me, as i have to integrate C++ program to my mail server..

any answers will be very helpful for me. thnks

---

