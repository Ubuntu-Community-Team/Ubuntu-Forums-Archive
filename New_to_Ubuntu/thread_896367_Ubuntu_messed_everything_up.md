---
title: "Ubuntu messed everything up?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by pankirk on 2008-08-21
I have a hard drive seperate for linux and another one for windows. From the windows harddrive I tried to use Wubi to install linux (bad idea) and now when ever i try to boot into the windows hard drive it says "grub loading error 17" or something along the lines of that. How can I fix this error? I know that windows isnt messed up because when i access the drive from linux i can see all of my windows files and everything else. so how can i be able to boot from it again? Thanks!

---

### Post by Loaded.len on 2008-08-21
XP or Vista?

If it's XP, then you could boot the windows recovery console and run fixmbr (as in Fix Master Boot Record)


[LIST=1]
[*]Set your computer to boot to CDROM before HDD (or use a one time boot menu that many newer computers have)
[*]Boot from your XP setup disc and do NOT press enter to setup...press R for recovery console instead
[*]select the installation to repair (you probably only have one, type the number corresponding to the installation)
[*]enter your administrator password
[*]at the recovery console type ```
fixmbr
```
[/LIST]

---

### Post by pankirk on 2008-08-21
It's actually vista =/

---

### Post by Elfy on 2008-08-21
Grub error 17 generally refers to a missing partition. I would do as loaded len suggests and try to install it again, you might find more information on the wubi forum - [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

This is the wiki which might also help [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Loaded.len on 2008-08-21
In Vista, I believe the command is bootsect... but I can't give you exact instructions on it.

---

### Post by pankirk on 2008-08-21
Yes, but sometimes it says "grub error 21" and others. it might be my motherbard?

---

### Post by sandysandy on 2008-08-21
> **pankirk said:**
> Yes, but sometimes it says "grub error 21" and others. it might be my motherbard?

see this

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

[http://ubuntuforums.org/archive/index.php/t-630550.html](http://ubuntuforums.org/archive/index.php/t-630550.html)

regards

---

### Post by forger on 2008-08-21
I'd go with the reinstallation..
Have you tried to install it again without wubi? Put in the CD and boot from the Ubuntu live CD?

---

### Post by philinux on 2008-08-21
One easy way to fix this is with the supergrub disc.

It can restore the boot for vista xp and linux.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

On the right you'll see the download options.

---

### Post by pankirk on 2008-08-21
ok but the thing is i can't reinstall vista because it has important files on it (MySql databases, program sources, ect...) that I cant really backup because of other files they are linked too, making it impossible to back up all of those files.

---

### Post by WastePotato on 2008-08-21
Use a LiveCD, force it to mount the drive and backup for data from there?

I dunno. I'm actually clueless on Linux. =\

---

### Post by pankirk on 2008-08-21
I get what your saying but my computer doesnt play well with live CD's. I have tried gOS, ubuntu, kubuntu, edubuntu, and gOS space. Not one of them would boot from the live CD. I had to just do the text based installer.

---

### Post by cariboo on 2008-08-21
If I were you I would use philinux's solution, that way you wouldn't have to re-install anything.

Vist:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Jim

---

### Post by sandysandy on 2008-08-21
> **pankirk said:**
> I get what your saying but my computer doesnt play well with live CD's. I have tried gOS, ubuntu, kubuntu, edubuntu, and gOS space. Not one of them would boot from the live CD. I had to just do the text based installer.

have u gone thru the links at post # 7 above.

regards

---

### Post by jerzydirtracer on 2008-08-21
It might be the hard drive make, it took me a couple of hard drives to work with Ubuntu. I am using a Toshiba for laptop and wd for garage. I tried maxtor and segate and got a bunch of grub errors, I loaded with what i am using now, and both hdrives work.

---

### Post by k3lt01 on 2008-08-22
If ever a thread was given the wrong title this one is it. Ubuntu hasn't messed everything up at all, instead what has probably occurred is two things and you have already basically admitted to one and it seems as though you may be about to do another.

1st. Never play around with your PC without having a good backup plan (i.e. having a way to back up VITAL information).
2nd. did you do any preparation to Windows before you started playing around? You know things like defrag etc. I know its Wubi but you have installed an entire OS within your main OS so you really need to make sure your primary OS is clean and in good working order.
3rd. Take the advice given in previous posts and let us know how you go. Check out the Grub disk already mentioned.

---

### Post by forger on 2008-08-22
> **pankirk said:**
> ok but the thing is i can't reinstall vista because it has important files on it (MySql databases, program sources, ect...) that I cant really backup because of other files they are linked too, making it impossible to back up all of those files.

Who said about reinstalling vista?! I suggested formatting the **linux** partition(s) and reinstalling **ubuntu**

Although supergrubdisk might be a better idea to try first :)

---

### Post by Elfy on 2008-08-22
Just a question here as I don't know the answer :) - does supergrub work for a linux installed in windows with wubi

---

