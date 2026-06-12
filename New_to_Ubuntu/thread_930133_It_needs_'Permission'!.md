---
title: "It needs 'Permission'?!"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by ChaosMuffins on 2008-09-25
I can't change certain things about files, like system sounds, and I cannot access certain folders in the system, because I need 'Permission'. The problem with this is that I happen to be the only user, so I'd *assumed* I was the admin. 

Is there something special I have to do to get 'Permission'...? Or is it better left alone? :confused:

Thanks in advance, this is my very, very first Non-Windows OS, and most of the Tech Support I've been getting is from my older sibling...but he's not on Ubuntu. He's on slackware...#-o So he's not the most help.

---

### Post by nkri on 2008-09-25
To change system files (which you should only do if you know exactly what you're doing), you must be the superuser, or root.  To gain full access to these files, you must open Nautilus as root.  Go to Applications>Accessories>Terminal.

In the window that pops up, type
```
sudo nautilus
```

It will ask for your password.  Type it in and hit enter, even though it won't show anything.

You can now do anything you want, but be very careful.  This is like taking a stroll in no-man's-land, so don't delete or change anything you're unsure about!

Good luck!
-nkri

---

### Post by Sinkingships7 on 2008-09-25
When you try to perform an administrative task, you'll most likely be asked for the administrative password. If you're the only user on the computer, then the password is the same as your login password. 

If you are trying to perform root (admin) actions on files or folders, and you don't want to do it through the terminal, you can open a terminal and type ```
gksudo nautilus
``` to get a root-level 'explorer' (nautilus) window. This is not a high recommendation, and you ought to be careful when messing with that stuff. Unless you know 110% what you're doing, try to limit yourself to ONLY your home folder. Do not touch system folders unless you have a purpose.

If you have more questions, ask away.

---

### Post by Tatty on 2008-09-25
Have a read of this - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

:)

---

### Post by halitech on 2008-09-25
typically if the system won't let you make a change, there is a good reason for it. The root user is disabled in Ubuntu but you are part of the SUDO group which gives you admin rights *when you need them* by prefixing the command with sudo.

if you need to edit a text file, you would open the terminal and type in```
gksu gedit /path/to/file
```
I normally stay away from using Nautilus as root because you can make mistakes which are not easily recoverable from.

---

### Post by halitech on 2008-09-25
> **nkri said:**
> To change system files (which you should only do if you know exactly what you're doing), you must be the superuser, or root.  To gain full access to these files, you must open Nautilus as root.  Go to Applications>Accessories>Terminal.

In the window that pops up, type
```
sudo nautilus
```

It will ask for your password.  Type it in and hit enter, even though it won't show anything.

You can now do anything you want, but be very careful.  This is like taking a stroll in no-man's-land, so don't delete or change anything you're unsure about!

Good luck!
-nkri

its generally a better idea to use gksu (or gksudo) then sudo when launching a graphical app. sudo is fine for terminal commands

---

### Post by ChaosMuffins on 2008-09-25
Thanks a lot, everyone! I was getting a tad worried that I'd done something wrong. Don't worry; I never mess around in system files without consulting my brother over the phone and getting a lengthy, simplified explanation. He's the programmer, not me. :oops:

---

### Post by billgoldberg on 2008-09-25
> **ChaosMuffins said:**
> Thanks a lot, everyone! I was getting a tad worried that I'd done something wrong. Don't worry; I never mess around in system files without consulting my brother over the phone and getting a lengthy, simplified explanation. He's the programmer, not me. :oops:

When you do launch nautilus as root, be sure to use

gksudo nautilus, not sudo nautilus like on user adviced.

---

### Post by nkri on 2008-09-25
> **halitech said:**
> its generally a better idea to use gksu (or gksudo) then sudo when launching a graphical app. sudo is fine for terminal commands

Ah, sorry, I meant gksudo:)

---

### Post by ChaosMuffins on 2008-09-25
:3 Everyone here is so helpful; this is *already* so much better than Whinedows. I get free help from people that actually care about helping me, and not getting paid 10 bucks an hour to run me in circles. 

...and here I was afraid that I'd get a slow response...

---

### Post by billgoldberg on 2008-09-25
> **ChaosMuffins said:**
> :3 Everyone here is so helpful; this is *already* so much better than Whinedows. I get free help from people that actually care about helping me, and not getting paid 10 bucks an hour to run me in circles. 

...and here I was afraid that I'd get a slow response...

These forums have a pretty big userbase and most questions get answered pretty fast.

If things are going to slow for you, you could also use IRC to get your answers. 

If you don't know on how to use it,:

[http://linuxowns.wordpress.com/2008/04/23/ubuntu-irc-channel/](http://linuxowns.wordpress.com/2008/04/23/ubuntu-irc-channel/)

--

Because you are new to linux/ubuntu I think your will find some of my guides pretty useful.

My codecs guide (dvd playback, avi/divx/xvid, mp3, wma, wmv, ...) and the customization guide are the ones you'll need.

They are in my signature.

---

