---
title: "theme is screwing up apt-get"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by kl2bmark on 2008-08-24
Trying to get a few apps and I get the following error:

> mark@ubuntu:~$ gksudo app-get avant
/home/mark/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:48: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/mark/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:49: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/mark/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:50: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

From what I see its an issue with the theme I've got, but is there any way around it or to fix it? :confused:

 Thanks

---

### Post by txcrackers on 2008-08-24
Since you're on the command-line, try
```
sudo apt-get avant
```

---

### Post by kl2bmark on 2008-08-24
Tried that, but this is the result:

> mark@ubuntu:~$ sudo apt-get avant
E: Invalid operation avant


---

### Post by Tsurugi13 on 2008-08-24
You're installing right?

> sudo apt-get install avant

I think you left out install.

---

### Post by maddy4u on 2009-08-28
Try the following link it gives a good information about app-get and the options

[http://www.cyberciti.biz/howto/question/linux/apt-get-cheat-sheet.php](http://www.cyberciti.biz/howto/question/linux/apt-get-cheat-sheet.php)

cheers
~Maddy

---

