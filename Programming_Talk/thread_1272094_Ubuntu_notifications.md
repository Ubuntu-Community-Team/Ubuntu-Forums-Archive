---
title: "Ubuntu notifications"
date: 2009-09-21
forum: Programming Talk
---

### Post by SigmaSanti on 2009-09-21
Hi, I was wondering how to make my program use the built in notifications of Ubuntu, notify-OSD, like other programs such as rhythmbox. If someone could post a link to a description of how to do this, or the syntax of the command that would be great. 

Even better, if you have example code in C++ or similar language, I would *really* appreciate it.

Thanks.

---

### Post by j7%&lt;RmUg on 2009-09-22
Check this out:

[http://pkpatel88.wordpress.com/2009/03/25/using-bashpodder-with-notify-osd/](http://pkpatel88.wordpress.com/2009/03/25/using-bashpodder-with-notify-osd/)

Basically you write a bash script to make a call to notify-osd and ask it to display a message specified by you.

Also, thanks for bringing this up, i might use this in some of my projects.

---

### Post by fct on 2009-09-22
> **nisshh said:**
> Check this out:

[http://pkpatel88.wordpress.com/2009/03/25/using-bashpodder-with-notify-osd/](http://pkpatel88.wordpress.com/2009/03/25/using-bashpodder-with-notify-osd/)

Basically you write a bash script to make a call to notify-osd and ask it to display a message specified by you.

Also, thanks for bringing this up, i might use this in some of my projects.


You write a bash script if you want to use it from scripts.

For C/C++ it should work using libnotify:

[http://manishtech.wordpress.com/2009/03/29/working-with-libnotify/](http://manishtech.wordpress.com/2009/03/29/working-with-libnotify/)

---

### Post by SigmaSanti on 2009-09-22
Nice!, thanks a lot this is exactly what I was looking for.

---

