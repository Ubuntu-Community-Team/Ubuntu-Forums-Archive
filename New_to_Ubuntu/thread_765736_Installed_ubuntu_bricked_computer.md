---
title: "Installed ubuntu bricked computer?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by daviddsims on 2008-04-24
Well guys I just downloaded ubuntu and put the cd in and installed it. All went well except when I try to put my user name and password it says not correct. I know it is the correct stuff I wrote it down. Also when I reboot I dont have an option to boot back up to XP so now my computer is useless. Anyone have some advice how to get out of this mess? Thanks.

---

### Post by Bodsda on 2008-04-24
yeah, are you 'sure' you set up the passwords correctly??

did ubuntu install the GRUB onto the mbr of your windows hard drive/partitionor the ubuntu one?

download super grub disk
[http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/]("http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/")
(although this could be a problem if you have no OS) then burn to cd, whack it in to restore your windows MBR (remove ubuntu HD if possible before doing that)

you could edit the menu.list by hand to add windows to the list but you'd have to no the exact line (which i have no idea how to find out)

anyway, hope this helps

---

### Post by Chayak on 2008-04-24
The easiest thing to do is reinstall.  It is a bit odd.  There is a way to fix it but it gets a bit technical as it involves writing values into /etc/shadow when booted from the live CD

That and make sure your caps lock is off

---

### Post by daviddsims on 2008-04-24
Well I guess thats a little over my head. I really just would like to scrub this whole idea of Ubuntu since it has been a nightmare and go back to XP.

---

### Post by Bodsda on 2008-04-24
You could do that,.,. then in a years time when you still dont want vista cause everyones still sayin its rubbish youll be really annoyed when you learn you cant play the latest games becausedirect x 10 isnt being released for xp -- then youll get a virus and have to spend days fixing it,and all the time you waste sat there while its froze -- but you can be sure il be having a direct x free, virus free and freeze free lifeon my ubuntu machine

---

### Post by Calash on 2008-04-24
Definetly check cap lock if you are sure about the password.  Upper and Lower case does make a difference in the user name as well.

As to your XP partition, did you do the guided partitioning or did you tell it to use the entire disk?  As long as you did not tell it to use the whole disk you can get your XP back, worst case you should be able to boot to your Windows XP CD, go to the recovory console, and type FIXMBR c:  , this will erase GRUB and put the XP boot loader back in place.

---

### Post by daviddsims on 2008-04-24
How do I get to the recovery screen to type that in?

---

### Post by Bodsda on 2008-04-24
you insert the xp install cd that you recieved when purchasin your machine -- then set the bios to boot cd's first, then instead of sayin install say recover -- these are all options on the cd --

---

### Post by otrojake on 2008-04-24
You'll need a XP CD.  Boot off of that CD.  You'll have to either get to your boot menu from BIOS (by pressing esc, f8 or f10, or something else depending on your board) or set the boot order to make sure CD is before hard drive.

One thing you might want to do before doing the fixmbr command from the XP recover CD is booting from the LiveCD again.  When you get into the Ubuntu Live session open up a terminal and trying typing in this:

```
sudo passwd USER
``` replacing USER with your user name.  I think that should work for resetting your password.

---

### Post by bodhi.zazen on 2008-04-24
Booting to recovery mode is an option on the grub boot screen.

You will boot to a command line.

Enter this command to see your user name :

```
ls /home
```

Now re-set the password :

```
passwd user
```

where "user" = you user name.

Re-boot. At the log in screen make suer caps lock is off.

---

### Post by otrojake on 2008-04-24
bodhi.zazen's method is best.  I didn't think about the recovery option from GRUB.  Follow his directions.

---

### Post by TWO on 2008-04-24
If you're still interested in trying out Ubuntu when you manage to get XP back, you could always try Wubi as a method of using Ubuntu through Windows. It will allow you to use Ubuntu as if it was just another application in Windows. 
[http://wubi-installer.org/](http://wubi-installer.org/)

It's a shame that the installation didn't go well for you.

I assume that you made sufficient space on your disk prior to installing Ubuntu right?

Whilst you're attempting to recover XP, it might be a good idea to do a scan disk via the recovery console on the XP disc, just to make sure that there are no disc errors.

---

### Post by daviddsims on 2008-04-24
Thanks so much budhi!!!! Worked perfect where I could get back into ubuntu. Now maybe I will try to get used to this and forget about xp. Once again thanks

---

