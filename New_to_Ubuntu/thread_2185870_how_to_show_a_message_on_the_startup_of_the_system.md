---
title: "how to show a message on the startup of the system??"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by angiengel on 2013-11-04
Hi! I have  a small question about system startup on ubuntu.

I need to show a message when the system is starting anda say "Welcome, The system is booting", but i can't do this!!, i've heard about configure /etc/inittab on the line that controls control/alt/del but i don't know how to do this. Any suggestion please??

---

### Post by Bashing-om on 2013-11-04
angiengel; Hi !

Depending on the Desktop Environment you are using, there are a number of files that one may place an echo statement into to print the output back to the screen. Perhaps the easier thing to do is to use tools that are already in place to perform that function.
How about the Message Of The Day (??)
How To Customize Ubuntu’s Message of the Day
[http://www.howtogeek.com/104708/](http://www.howtogeek.com/104708/)

Does this work for ya ?

[INDENT][INDENT]ubuntu, many ways to do the same thing
[/INDENT][/INDENT]

---

### Post by squakie on 2013-11-04
Love  MOTD.  Many, many years ago used that to tell jokes, 1 line a day until the punchline, plus whatever "news" needed to be out for that day.

---

### Post by ian-weisser on 2013-11-04
I thought MOTD runs after boot is (almost) complete, and the system is ready for login.

For an early-bootup text message, I suggest going through grub.
For an early-bootup graphical message, you may need to change the Plymouth splash screen.

---

