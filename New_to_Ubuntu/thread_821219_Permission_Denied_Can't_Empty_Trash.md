---
title: "Permission Denied Can't Empty Trash"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by caitistrophic on 2008-06-07
I've already gone through a bunch of the archives and can't find an exact answer to my problem.  I have a second hard drive on my pc, I just went through a deleted a bunch of stuff from it to make room so that I could move some of my movie back-ups onto it.  When I went to unmount the drive it asked if I wanted to empty the trash first and I said sure of course because I couldn't get the movies onto it without making the room.  But now those files are sitting in my regular trash bin (some of them) and they wont go away.  They say I don't have permission and that I can't change the permissions from the trash bin. I tried moving them back but I don't have the permission.  How do I get rid of them and why the hell was I allowed to move them in first place if I don't have permission? 

Please forgive me if this is a repeated question, I really did try to find the answer on my own. I am as noob as noob can get. :?

Can I delete this entry at all? I feel really stupid but once I logged back out after the third time and unmounted the other hard drive again it emptied itself - I don't know why so maybe if someone doesn't mind explaining it to me anyways that would be cool, but otherwise forget I wrote this. Sorry for any inconvienace.

---

### Post by Bodsda on 2008-06-07
Graphical way


```
gksudo nautilus ~/.local/share/Trash
```

cli way

```
sudo rm -rf ~/.local/share/Trash/*
```

WARNING: THE COMMAND USED IN THE SECOND EXAMPLE IS EXTREMELY DANGEROUS IF USED INCORRECTLY!!

hope this helps

---

### Post by alienexplorers on 2008-06-07
Check that /.local/share/Trash is listed in the permissions under your name and not under root.

---

### Post by allenk on 2008-06-22
Thanks, I was looking for this answer as well.

Some of the threads say the trash is in ~/.Trash (which doesn't exist) instead of .local/share/

---

### Post by square_monkey on 2008-06-27
Thanks very much - big help!

---

### Post by Cotopaxi on 2008-07-01
> **alienexplorers said:**
> Check that /.local/share/Trash is listed in the permissions under your name and not under root.

Sorry for my very stupid question: how do I check that? Or, better said, how do I check permissions in general'

I have Permission problems with my USB Printer.

Operative System: Kubuntu Hardy Heron,

Printer Brother-MFC 5440CN

Thanks.

---

### Post by Ryadt on 2008-07-01
Right-click on the folder you want to check. Select permission.:)

---

### Post by Ryadt on 2008-07-01
Sorry you need to go on properties after right-clicking on the folder...

---

### Post by soxs on 2008-07-01
> **Bodsda said:**
> Graphical way


```
gksudo nautilus ~/.local/share/Trash
```

cli way

```
sudo rm -rf ~/.local/share/Trash/*
```

WARNING: THE COMMAND USED IN THE SECOND EXAMPLE IS EXTREMELY DANGEROUS IF USED INCORRECTLY!!

hope this helps

```
sudo rm -Rrf ~/.local/share/Trash/*
```
you lacked the R, for recursiveness, in case he deleted folders..

---

### Post by Cotopaxi on 2008-07-01
Ryadt,

Thanks, so I know this trick. Still my dammed printer only produces the reply under cups:

"Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4f9_16d_BROM5F423564_if0_printer_noserial": Permission denied"

Thanks again!

---

### Post by ChameleonDave on 2008-07-01
> **Cotopaxi said:**
> Sorry for my very stupid question: how do I check that? Or, better said, how do I check permissions in general'

This command will make sure that everything in your home directory belongs to you.  

```

sudo  chown -R cotopaxi:cotopaxi  /home/cotopaxi

```

Put your actual username in, obviously.

*Edit:  Just put "cotopaxi" after the "-R".  The bit after the colon is the group name, which is unnecessary.*

---

### Post by Mornedhel on 2008-07-01
> **soxs said:**
> ```
sudo rm -Rrf ~/.local/share/Trash/*
```you lacked the R, for recursiveness, in case he deleted folders..

Actually -r and -R are the same in in rm's case.

From man rm :

-r, -R, --recursive
              remove directories and their contents recursively

Edit : Uhh, the above chown command from ChameleonDave is kinda dangerous. He might have files in there that other *groups* need to access.

---

### Post by ChameleonDave on 2008-07-01
> **allenk said:**
> Thanks, I was looking for this answer as well.

Some of the threads say the trash is in ~/.Trash (which doesn't exist) instead of .local/share/

Yes, that is where it was in earlier editions.

Note that any other partitions you have will have their own trash.  For example, I have a partition mounted at /home/david/Files, which means that there are trash cans there for me and for root.  To delete them I can enter "sudo rm -fr /home/david/Files/.Trash*".

---

### Post by ChameleonDave on 2008-07-01
> **Mornedhel said:**
> 
Edit : Uhh, the above chown command from ChameleonDave is kinda dangerous. He might have files in there that other *groups* need to access.

Yes, I suppose so.  But when would that happen?

---

### Post by Mornedhel on 2008-07-01
If he has files that need to be accessed by some other people (assuming there are multiple users on his machine).

If he has installed software directly in his home directory (which is possible if he needs something that is not available in repositories).

If some piece of (admittedly badly-written) software requires its local config file to be readable by a system user or group.

In general, chown -R is a bad idea unless he knows precisely what he's doing. This leads to the used-to-be-common "I did chown -R myusername / so I could get rid of those pesky permissions problems and now nothing works" problem.

---

### Post by kendase3 on 2008-07-23
So just in case anyone finds this thread having had a similar problem to mine, I'll briefly summarize my situation and how I solved it.  I couldn't access or empty my trash since upgrading to Hardy, and trying to follow instructions such as in this thread and similar ones didn't work.  Eventually, I navigated to the folder above trash (~/.local/share) and tried accessing Trash through both a terminal and nautilus, which both failed.  Then, I opened up nautilus as root, (sudo nautilus ./) and found that I could get in.  I right clicked on the Trash folder, went to permissions, changed the owner to me rather than root, and changed the access to read and write rather than the default which I believe was read/write with no access, though this last step may not be necessary. Anyway, I hope this helps someone, and I apologize if I hijacked the thread in any way.

---

### Post by netlaptop on 2008-08-01
> **Bodsda said:**
> Graphical way


```
gksudo nautilus ~/.local/share/Trash
```

cli way

```
sudo rm -rf ~/.local/share/Trash/*
```



Graphical way (nautilus) did not work but
```
sudo rm -rf ~/.local/share/Trash/*
```
It works for me. Thanks you very much...

---

### Post by andtsoreyu on 2008-08-31
Thanks this worked like a charm!

---

### Post by bgbg683 on 2008-09-07
> **Bodsda said:**
> Graphical way


```
gksudo nautilus ~/.local/share/Trash
```

cli way

```
sudo rm -rf ~/.local/share/Trash/*
```

WARNING: THE COMMAND USED IN THE SECOND EXAMPLE IS EXTREMELY DANGEROUS IF USED INCORRECTLY!!

hope this helps

thankyou

---

### Post by psychok9 on 2009-01-12
Same problem, after I read this topic:
1) ALT+F2 -> gksu nautilus
2) I go to ~/.local/share/
3) I've removed Trash folder.

Now the trash is empty and respawned.

---

### Post by cb34 on 2009-01-12
sudo locate -e Trash (to find some other hidden Trash bins on your system.)
(running this command without sudo you can miss some i notice if they belong to root.)

---

### Post by babygenius55 on 2010-01-26
OK, my problem is sort of different. nautilus isn't showing the files that appear when I click the trash icon in the menu bar. I have 2 files that are in the trash that are shown one way, but not another.  The line in the address bar reads "trash:///", this is where the system says the files are.

^^ Um, never mind. After some sleep, I realised that the files came from a drive that I had set to auto mount. After unmounting (with gparted), then remounting I was able to get rid of the offending files. I guess I need to set some other parameters in the auto mount function.

---

