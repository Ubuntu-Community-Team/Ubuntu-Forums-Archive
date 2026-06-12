---
title: "Preferred Apps"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Gonz_91 on 2008-09-01
Hi, everyone!
Sometime ago, I read an article stating a few advantages KDE has over GNOME. One of them is the capability of choosing which software handles which files and services in a more advanced way than GNOME. I've seen this is actually true, in an out-of-the-box OS.


My question is: is there any application in GNOME that allows me (us) to enable this functionality?

---

### Post by Nepherte on 2008-09-01
I just right click on a file (with the file type I want to assign a program to) > choose properties > choose 'open with' tab > pick the program you want. Afterwards every file with that file type will be opened with the selected program.

---

### Post by Gonz_91 on 2008-09-01
I know that, but what I was looking for is an app that allows me to choose in a more... open way. Something like "Video:VLC", "Music:Amarok".

Maybe with the possibility to chose by filetypes.
I'm not so sure such a thing exists, anyway...

---

### Post by soloman498 on 2008-09-01
try these sites

[http://ubuntuforums.org/showthread.php?t=905155&highlight=kde+desktop](http://ubuntuforums.org/showthread.php?t=905155&highlight=kde+desktop)               

[http://ubuntuforums.org/showthread.php?t=906375&highlight=kde+desktop](http://ubuntuforums.org/showthread.php?t=906375&highlight=kde+desktop)

---

### Post by billgoldberg on 2008-09-01
> **Gonz_91 said:**
> Hi, everyone!
Sometime ago, I read an article stating a few advantages KDE has over GNOME. One of them is the capability of choosing which software handles which files and services in a more advanced way than GNOME. I've seen this is actually true, in an out-of-the-box OS.


My question is: is there any application in GNOME that allows me (us) to enable this functionality?


Yes.

You can set a proffered App for everything in Ubuntu.

You will going to have to get into some text files.

I've written a blog post about it here:

[http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/](http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/)

---

### Post by forger on 2008-09-01
It's better if you alter desktop-file-utils
```
cat /usr/share/applications/defaults.list
ls /usr/share/applications/
```

You have to create a yourfilename.desktop and customize it the way you like!
Once you're done you update the database:
```
sudo update-desktop-database
```
(a log off / log in would be even better)

Also, make sure you didn't use "open with" for a user, otherwise it will override the default application.

---

### Post by Gonz_91 on 2008-09-01
Thank you all for your responses!:)


> **billgoldberg said:**
> Yes.

You can set a proffered App for everything in Ubuntu.

You will going to have to get into some text files.

I've written a blog post about it here:

[http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/](http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/)

I've bookmarked your post for future reference.

*thiks to himself:*something with a gui would be nice...*:)*

---

