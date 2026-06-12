---
title: "partitions"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by fcf on 2008-11-08
As an absolute beginner to linux, I'm trying to install Ubuntu EEE from a usb key into an EEE 901 Linux 20 GB. I'm stuck with the "Prepare partitions" screen. I don't know what I'm supposed to do. Please help me.

Thanks

---

### Post by ggaaron on 2008-11-08
Can't you do the recommended option - use the whole disc and partition it automatically? If you want something more advanced or specific then don't be afraid to ask, but you must give us more information so we can help you.

---

### Post by mapes12 on 2008-11-09
> - use the whole disc and partition it automatically?

and once you have everything installed then move /home to a separate partition to keep everything safe in the future: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by ggaaron on 2008-11-09
Err, if you want a separate home partition you can do this with a few clicks when installing (isn't it default behaviour anyway?), doing this later is stupid as it involves unneeded complexity.

---

### Post by mapes12 on 2008-11-09
> (isn't it default behaviour anyway?)

No it isn't. The installation defaults to the "Guided - use entire disk" option. For someone new to Ubuntu they would naturally go with the default. As I did when I first started with Ubuntu. Therefore, if the system has install with /(root) and /home on the same partition it is good practice to move it. Hence my previous post pointing to the HowTo.

---

### Post by ggaaron on 2008-11-09
Ok, haven't seen Ubuntu installer for a while;) Still if someone is new to this it's a lot easier to do a home partition in GUI by dragging some handles instead of using cryptic commands in the console, if it wasn't no one would have written this GUI and if Ubuntu team does a good job so you don't have to know the console then why not use stuff they come up with?

---

### Post by mapes12 on 2008-11-09
> Still if someone is new to this it's a lot easier to do a home partition in GUI by dragging some handles instead of using cryptic commands in the console,

I agree. But even the GUI installer can be confusing to a noob. And some boxes (like one of mine) will not load the Live CD which means that a text based installation needs to be performed off an Alternate CD. From the perspective of someone new to Ubuntu the "Manual" configuration required in a text based installation is big ask :roll:

---

### Post by betes on 2008-11-09
> **fcf said:**
> As an absolute beginner to linux, I'm trying to install Ubuntu EEE from a usb key into an EEE 901 Linux 20 GB. I'm stuck with the "Prepare partitions" screen. I don't know what I'm supposed to do. Please help me.

Thanks

Installing the same OS on the same laptop, I did manual partition.  I created one mount point called / on the 4g drive, then another partition with another mount point called /home on the 16g drive.  I also created another partition on the 4g drive to be a very small swap partition (like 400mb).  I chose this setup because I think the guided partition wanted to install the whole thing on the 16g drive leaving the 4g drive empty (if I remember correctly).  But if you did the "guided" option its nothing to worry about.

I hope that info helps. I know its vague and might not be useful if your a complete beginner, but I don't know how detailed an explaination I can give since I'm relatively new myself.  Feel free to ask questions if you don't understand something.

---

### Post by fcf on 2008-12-09
Thanks all. It's done.

---

### Post by sandeep108 on 2008-12-10
> **betes said:**
> Installing the same OS on the same laptop, I did manual partition.  I created one mount point called / on the 4g drive, then another partition with another mount point called /home on the 16g drive.  I also created another partition on the 4g drive to be a very small swap partition (like 400mb).  I chose this setup because I think the guided partition wanted to install the whole thing on the 16g drive leaving the 4g drive empty (if I remember correctly).  But if you did the "guided" option its nothing to worry about.

I hope that info helps. I know its vague and might not be useful if your a complete beginner, but I don't know how detailed an explaination I can give since I'm relatively new myself.  Feel free to ask questions if you don't understand something.

I actually have done the same thing - manually did the partitions, with one as / and the other as /home. My problem is that the home directory is still in the main root partition '/' and I cannot access the /home partition. Do I need to mount it? if so where and how do I get the OS to use the new /home partition. The guide in this post seems rather old.

---

