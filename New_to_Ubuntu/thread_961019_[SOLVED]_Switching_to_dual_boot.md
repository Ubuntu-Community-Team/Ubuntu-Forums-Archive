---
title: "[SOLVED] Switching to dual boot"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by supwest on 2008-10-27
Hey everyone,

I'm trying out ubuntu, and I really like it so far, everything seems to work, so I wanted to try a real dual boot and try a bit more stuff (read World of Warcraft) and see if that works. I installed ubuntu inside Windows (since I couldn't get it to boot from either of my CD-drives). It seems to work a little like a dual boot, I get to choose which OS to use when I start the computer, but it doesn't have a lot of space, which is why I want to try the dual boot option. My question is how do I go about setting up the dual boot, or do I even need to? 

Keep in mind I'm a total noob at this, so keep your responses at the appropriate level :) .

Thanks

---

### Post by ratmandall on 2008-10-27
From the info you have given me it sounds like you are alreading dual booting windows and ubuntu because the grub menu appears at startup which allows you to choose which OS to boot into...

So with that aside are you just asking how to make your ubuntu partition bigger in size so you have more space?

---

### Post by antmenj on 2008-10-27
Do you see something like this with more options ie windows?

[IMG]http://upload.wikimedia.org/wikipedia/commons/1/12/GRUB_screenshot.png[/IMG]

If so you are already dual booting.

---

### Post by supwest on 2008-10-27
@ratmandall

Yeah, I'm looking to increase the amount of space available. I didn't explicitly set up a partition, and it looks like I've got 10GB available.

@antmenj

I don't see that when I start up the computer. When I start up the computer, the screen where I can choose ubuntu is the same as it was before I installed ubuntu (so I'm assuming that's the Windows boot manager). I can choose Windows XP, Windows recovery mode, or ubuntu. 

However, after I choose to boot up ubuntu I can get to the screen you posted, with just those options.

---

### Post by ratmandall on 2008-10-28
> **supwest said:**
> @ratmandall

Yeah, I'm looking to increase the amount of space available. I didn't explicitly set up a partition, and it looks like I've got 10GB available.

@antmenj

I don't see that when I start up the computer. When I start up the computer, the screen where I can choose ubuntu is the same as it was before I installed ubuntu (so I'm assuming that's the Windows boot manager). I can choose Windows XP, Windows recovery mode, or ubuntu. 

However, after I choose to boot up ubuntu I can get to the screen you posted, with just those options.

Well I don't know how to resize a partition from windowsXP, But you can resize it with gparted live cd ```
[http://gparted.sourceforge.net](http://gparted.sourceforge.net)
``` have a go at running that liveCD see if it works, And if it does work it's pretty simple just make sure you resize the 'ext3' might be 'ext2' filesystem that has the amount of Gigabytes that you alocated for ubuntu when installing it.

---

### Post by kansasnoob on 2008-10-28
> How do I migrate to a real partition, and/or get rid of Windows entirely?

Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).

As an alternative, the following script can be used with Wubi 8.04.

Download wubi-move-to-partition

Open a terminal and run: 

```
sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10
```

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

It's not problem free!

---

### Post by bumanie on 2008-10-28
If you like the wubi installation, you can move it to its own partition and then delete the wubi install via add/remove in windows, once you are sure the move has occurred properly. [Look at this]("http://lubi.sourceforge.net/lvpm.html")

---

### Post by ashmew2 on 2008-10-28
If you are thinking of installing Ubuntu from scratch on a newly partitioned disk or something and you cannot boot from CD/DVD.. I'd say you MUST try  out booting from USB.Post back if you're interested! :)

---

### Post by Paqman on 2008-10-28
[LVPM](http://lubi.sourceforge.net/lvpm.html) can either migrate your Wubi install to a fresh partition, or it can actually resize your existing Wubi virtual partition files, giving you more space.

---

### Post by ITT1 on 2008-10-28
I am trying Ubuntu 8.10 RC on an ACER Aspire M1510. it seems to boot OK, except it says:

Ubuntu is running in low graphics mode. The following error has occurred you may need to update your configuration to solve this
(EE) no device detected. Ubuntu offers to fix this. Can I wait till after installation? :???: 

I want to end up with a dual boot machine.

Drive c has Vista home premium installed, and I want to keep this and install Ubuntu to Drive d which is a Data drive.

Will opting to allow Ubuntu to install itself from the CD enable me to direct Ubuntu onto Drive d and end up with a dual boot machine?  :???: What else would I need to do? Simple instructions would be terrific! :)

I'm nervous of corrupting the Vista by unintentionally overwriting files or whatever on Drive c.

Thanks!

---

### Post by supwest on 2008-10-28
LVPM did the trick.

Thanks, everyone, for the help!

---

