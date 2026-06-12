---
title: "Unable to access Windows 7 partition from Ubuntu"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by Myfathersheart on 2014-01-18
// This is my attempt to condense a prior thread that I began in hopes that all information regarding my problem will be easier to see
(Which is now closed and can be found by those wanting that information here [http://ubuntuforums.org/showthread.php?t=2199219](http://ubuntuforums.org/showthread.php?t=2199219))

I am running a dual boot Ubuntu 12.04/Windows 7.  I have only had Ubuntu installed for about a week now. 

I am trying to access my windows files from Ubuntu.  So far, I have tried the tutorial at [http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu) 

I believe my Windows files are at dev/sda2.  So, I want to mount that. However, at step 6 I get the error:

root@ubuntu:~# mount -t ntfs /dev/sda2 /mnt/WINDOWS -o "umask=022"
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.


From there I have tried to identify processes using fuser, but I am not sure I am using it right:

ransomed_son@ubuntu:~$ fuser -a dev/sda2
Specified filename dev/sda2 does not exist.
dev/sda2:
ransomed_son@ubuntu:~$ fuser -l dev/sda2
HUP INT QUIT ILL TRAP ABRT IOT BUS FPE KILL USR1 SEGV USR2 PIPE ALRM TERM
STKFLT CHLD CONT STOP TSTP TTIN TTOU URG XCPU XFSZ VTALRM PROF WINCH IO PWR SYS
UNUSED
ransomed_son@ubuntu:~$ fuser dev/sda2
Specified filename dev/sda2 does not exist.
ransomed_son@ubuntu:~$ 




Finally, I see a key next to dev/sda on my gparted screen.  I am assuming that is what is preventing me from successfully mounting it. 

Thanks to anyone who can help!
[ATTACH=CONFIG]249561[/ATTACH][ATTACH=CONFIG]249562[/ATTACH]

---

### Post by carl4926 on 2014-01-18
All you need to do is click on it in Nautilus and it should open

Unless Windows isn't shutdown fully? Particularly is this a problem with windows 8, as it's default power off doesn't shutdown  windows. This does prevent access.
In which case you need to change the settings in windows.

---

### Post by Myfathersheart on 2014-01-18
I haven't encountered Nautilus yet.  I will install it and see if that works.

Also, I am using Windows 7. So, the Windows 8 issue shouldn't affect me.

and thank you so much!!

---

### Post by Myfathersheart on 2014-01-18
Wait, Nautilus is the file manager... clearly I am an Ubuntu noob.

My Windows partition does *not* show up in Nautilus.

---

### Post by carl4926 on 2014-01-18
It should look like this
See my other partitions listed as XXGB HDD
[http://paste.opensuse.org/53196889](http://paste.opensuse.org/53196889)

---

### Post by Myfathersheart on 2014-01-18
Here is how mine looks.  I don't have access to my Windows partition in Nautilus. It should be a 400gb+ partition.
[ATTACH=CONFIG]249563[/ATTACH]

---

### Post by carl4926 on 2014-01-18
Umm...
I'm off out today
But can we see

```
sudo fdisk -l
```
and
```
sudo parted -l
```

---

### Post by coffeecat on 2014-01-18
Did you install Ubuntu as a wubi system? That is, when you first installed Ubuntu you would have run the wubi installer from inside a running Windows system, rather than installing Ubuntu from a live CD or USB. If yours is a wubi system, that would explain the "Mount is denied because the NTFS volume is already exclusively opened" message.

From the Nautilus file manager, click on the "File System" icon in the left pane. Is there a host folder? If so, yours is a wubi installation and you'll find the contents of your Windows partition mounted in the host folder.

**EDIT**: I've just noticed something in the images in your first post. You have a wubi system and your Windows partition is mounted to /host. See above for how to access it.

All about wubi:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Myfathersheart on 2014-01-19
Coffeecat, that sounds promising. I will check it out tomorrow. Thank you!

---

### Post by smuggly on 2014-01-19
do you have the ntfs utilities installed on buntu?

---

### Post by Mark Phelps on 2014-01-19
> **smuggly said:**
> do you have the ntfs utilities installed on buntu?
It's not a utilities-related problem.  What the OP didn't understand is that with a Wubi installation, the containing NTFS partition is already mounted -- under "/host" in the Linux filesystem.  Thus, you can't mount it a second time.

---

### Post by Myfathersheart on 2014-01-19
Cofeecat, you were right.  My Windows files were in the host folder.  Thank you all so much!

---

