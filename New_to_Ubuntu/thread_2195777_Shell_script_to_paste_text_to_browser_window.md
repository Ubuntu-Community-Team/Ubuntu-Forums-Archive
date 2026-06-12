---
title: "Shell script to paste text to browser window"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by frogwarrior on 2013-12-26
The password manager keepassx lets you hit a hotkey (I use CTRL+\) then it will log you into a website automatically. What it does is you click on the username field of the login page so that the cursor is in it, then when you hit your hotkey, keepassx will do the sequence {USERNAME}{TAB}{PASSWORD}{RETURN}. It lets you add custom sequences (i.e. {USERNAME}{TAB}{PASSWORD}{OTHER FIELD}{WHATEVER} but the problem is it only lets you add a handful of fields (title, username and password) so its not of any use if you wanna automatically fill out a registration form. So I wanna make a program that does this. I add a list of fields for each web page then it will fill in the application form (but not submit it since I need to enter the captcha manually). Can I do this with a bash script? The only programming language I'm really good with is PHP but I don't know if a PHP app could do this.

---

### Post by whitesmith on 2013-12-26
KeePassX's Tools->AutoType->Customize lets you do almost anything. If you can't make this work, hop on the official site and see if the developers can help you. This forum is for general Ubuntu questions, not help on specific languages. Cheers.

---

### Post by frogwarrior on 2013-12-27
I figured out a simple way to do this, I just wrote a javascript event listener and installed it as a user script with greasemonkey. Heres the script if anyone wants to take a look:
[http://pastebin.com/d8xNHvSu](http://pastebin.com/d8xNHvSu)

---

