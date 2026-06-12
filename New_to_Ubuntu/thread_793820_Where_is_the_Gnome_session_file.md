---
title: "Where is the Gnome session file?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by shewenhao on 2008-05-14
I had some problem like I should rename the session file in the ~/.gnome or ~/.gnome2. But I do not understand what does the ~/.gnome means....I should find a sessioin file in this folder. Who can tell me the complete path to find this /.gnome folder?

Thank you very much!!

---

### Post by KingWilliam on 2008-05-14
The "~" sign means your home folder. So this is probably /home/*yourname*/.gnome

---

### Post by alienexplorers on 2008-05-14
IT should be in your home folder.

---

### Post by Nepherte on 2008-05-14
Btw, every map or file with a "." in front of the name is hidden. To see them in nautilus press ctrl+h

---

### Post by sunstriker on 2008-05-14
It's in your home folder i think. But there's a '.' before the filename, which means it hidden. To view it, type in the terminal:

```
cd /home/yourusername/ 
ls -a (now you see ALL the files, including hidden ones)
gedit .gnome
```

Now you can edit the file
~ stands for your home folder..

---

### Post by shewenhao on 2008-05-14
thank you very much, you guys. There quick replies give me passion for the Ubuntu!!!

---

### Post by shewenhao on 2008-05-14
Hey, guys. I successively found the .gnome folder but there is nothing about session file. Actually I met some problem described in this thread. And on the second page ([http://ubuntuforums.org/showthread.php?t=406225&page=2](http://ubuntuforums.org/showthread.php?t=406225&page=2)) of this thread one guy recommended to rename the session file  under ~/.gnome or /. But I found nothing about session file. How do you guys think about this?

Thanks again!

---

### Post by itsjustarumour on 2008-05-14
> **shewenhao said:**
> Hey, guys. I successively found the .gnome folder but there is nothing about session file. Actually I met some problem described in this thread. And on the second page ([http://ubuntuforums.org/showthread.php?t=406225&page=2](http://ubuntuforums.org/showthread.php?t=406225&page=2)) of this thread one guy recommended to rename the session file  under ~/.gnome or /. But I found nothing about session file. How do you guys think about this?

Thanks again!

Try looking in /home/(your username)/gnome2/   

File is just called "Session" I think.

---

### Post by shewenhao on 2008-05-15
Hi, every body here, i found the way to solve this problem. I delete all gnome gnome2 conf confb and metacity file before log in by clicking ctrl+shift+f1. Then I log in. Every thing fine now. Thnaks!!!!

---

### Post by shewenhao on 2008-05-15
How I thank this thread?? I can not find the thank button...

---

### Post by itsjustarumour on 2008-05-15
> **shewenhao said:**
> How I thank this thread?? I can not find the thank button...

Its that little star/medal icon over on the right (you have to go into the post you want to "thank" first)

 :-)

---

### Post by rustamb on 2008-08-20
In Intrepid Ibex it's not more in ~/.gnome2. Does anybody know where 'session' file is in Intrepid?

---

### Post by zir0n on 2008-12-26
> **rustamb said:**
> In Intrepid Ibex it's not more in ~/.gnome2. Does anybody know where 'session' file is in Intrepid?

Every additional entry you make to the session startup gui a new file is created in this directory:

~/.config/autostart

---

### Post by hovzio on 2008-12-26
> **zir0n said:**
> Every additional entry you make to the session startup gui a new file is created in this directory:

~/.config/autostart

Thank you, I have been looking for this for a while. The whole time I was starting things from: /etc/X11/Xsession.d/script. (Like starting syndaemon and setting synclient settings.) The prob. is these settings are system wide. 

 One question, I looked at a file I setup with gnome in .config/autostart,

[Desktop Entry]
Type=Application
Name=performance
Exec=cpufreq-selector -g performance
Icon=system-run
Comment=Performance

So to the questions.. For "TYPE", is it safe to assume that this will always be an application, what if you start a daemon? 

What does "ICON" mean, is this like a desktop configuration file that may point to an icon? 

If I want to start up a script, do I just put in the path to file?

Thanks for the help, a happy holiday to all!

---

### Post by buzzbo on 2009-12-31
> **hovzio said:**
> Thank you, I have been looking for this for a while. The whole time I was starting things from: /etc/X11/Xsession.d/script. (Like starting syndaemon and setting synclient settings.) The prob. is these settings are system wide. 

 One question, I looked at a file I setup with gnome in .config/autostart,

[Desktop Entry]
Type=Application
Name=performance
Exec=cpufreq-selector -g performance
Icon=system-run
Comment=Performance

So to the questions.. 
I'm sure you've figured this out already (or perhaps forgotten about it lol!), but I thought I'd fill in a hanging question.  I found [this info here (freedesktop.org)]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html").

> **hovzio said:**
> For "TYPE", is it safe to assume that this will always be an application, what if you start a daemon? 
valid TYPES are Application, Link, or Directory.  daemon sounds like an application to me. :)

> **hovzio said:**
> What does "ICON" mean, is this like a desktop configuration file that may point to an icon?
Yes the icon to show on the desktop.  Since no path is given, it looks like the icon is pulled from the theme, otherwise you specify the entire path for the picture.

> **hovzio said:**
>  If I want to start up a script, do I just put in the path to file? That is what I would do under, i.e. Exec=/path/to/script

> Thanks for the help, a happy holiday to all! Happy Holidays! (one year late ;) )

Buzz

---

