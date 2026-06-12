---
title: "intel 4000 gma update issues"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by tnyfgr3 on 2013-07-15
hello,
total linux noob here, after much research settled on Xubuntu13.04 64bit to learn on. my issue is the intel 4000 gma driver which i got installed fine, and is running beautifally, but i'm getting a update notification i'm unable to do any thing with, here's what i'm seeing:
[ATTACH=CONFIG]244768[/ATTACH][ATTACH=CONFIG]244767[/ATTACH]

any help is greatly appreciated!

---

### Post by hansdown on 2013-07-15
Welcome to the forum, tnyfgr3.

Are you not able to click on the "O.K" button?

This is just a warning, that the source is not approved by......someone.

It's generally o.k.

---

### Post by tnyfgr3 on 2013-07-16
No, when i click the "OK" button it terminates the whole proccess and i still get the update notification, i understand that some mysteroius "they" somewhere haven't aproved the driver i just don't know how to install anyway, with the base driver it was easy to figure out but this update isnt leaving me with any clues.

---

### Post by Bashing-om on 2013-07-16
tnyfgr3; Hi !
Let's get some more clues as to what is going on:
Post back the out puts of Terminal codes (desk top, key combo ctl+alt+t yields a terminal)
```
sudo apt-get update
sudo apt-get upgrade
```

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by tnyfgr3 on 2013-07-16
"sudo apt-get upgrade"  this command fixed the problem i got a propt to install w/o verification and then it says successful install! THX BUNCHES!

---

### Post by Bashing-om on 2013-07-16
tnyfgr3; Good deal !

Simpler is better, let the package manager do it's job.

Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

