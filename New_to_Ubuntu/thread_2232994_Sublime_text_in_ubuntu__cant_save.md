---
title: "Sublime text in ubuntu / cant save"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by sheez on 2014-07-05
So, I really like using sublime text, but I cannot save html files in the server directory (permission errors). When I use sudo gedit index.html for example it works perfectly (I can edit and save without any problems).
Is there a way to use sublime text in ubuntu like gedit?

---

### Post by capscrew on 2014-07-06
> **sheez said:**
> So, I really like using sublime text, but I cannot save html files in the server directory (permission errors). When I use sudo gedit index.html for example it works perfectly (I can edit and save without any problems).
Is there a way to use sublime text in ubuntu like gedit?

The short answer is yes there is no reason why you can't use a form of sudo with sublime.  You should not use sudo with either gedet or sublime however.  You should use gksu or gksudo with either editer.  Both editors or GUI based text editors.  You run the risk of loosing the file or other environment problems using sudo in this manner.  depending upon which version of Ubuntu you have installed you may need to install gksudo before using it.

The proper command for sublime text is ```
gksudo subl
``` 

A more long term answer for you is to set up the permissions correctly so you can place files in the folder without having to use root user permissions.

---

### Post by sheez on 2014-07-06
thanks, that worked!

---

