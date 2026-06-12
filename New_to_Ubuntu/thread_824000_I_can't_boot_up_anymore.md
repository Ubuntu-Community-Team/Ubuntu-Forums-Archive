---
title: "I can't boot up anymore"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by schmidtbag on 2008-06-09
I hontestly have no idea what I did, but when I boot up the computer I get this error:
> Trying to resume from /dev/disk/by-uuid/{random letters and numbers}
kinit: No resume image, doing normal boot...
Ubuntu 8.04 Tornado-II tty1
Tornado-II login:

I did try updating in the recovery boot, which it did do, but nothing happened.
I tried "sudo apt-get install ubuntu-desktop", but it didn't do anything.
When I tried "sudo update-grub", I got the message:
"Your /usr is broken, please fix it before call this wrapper!" in those exact words.

I really don't feel like reinstalling, and my wireless does appear to be working.  What do I do?

EDIT:
If I type in "startx", it does start normally but it gives an error message saying
> Internal error
failed to start HAL!
And not only that but I can't continue to update, I can click "install updates" and nothing happens.
AND after later realization, it won't let me shut down, so I check for the login settings in Preferences, only to find it missing.

I'm sure some of these were due to some codes other people said to do in other posts, but I sure have a lot of repairing to do.

---

### Post by cprofitt on 2008-06-09
I am not sure how to fix your problem... but based on the description it sounds as though your computer hibernated (saved session to disk) and is trying to resume. I will flag this for the unanswered posts team.

---

### Post by schmidtbag on 2008-06-09
i haven't hibernated on this computer yet and when i typed in startx to get back into gui mode, i turned off save session and that didn't help.  i wouldn't think that'd be the issue cause i always have that on

---

### Post by cariboo on 2008-06-09
From the message you are getting something is not right in your /usr directory. This is where most of your executables and program information is, if you removed any of the directories in this directory that is where your problem lies.

Jim

---

### Post by atoponce on 2008-06-09
Can you post your partition layout as reported by:

```
cat /proc/partitions
```

Further, I'm interested in the contents of your /etc/fstab file.

---

### Post by MattP220 on 2008-06-09
Interesting, I'm having a similar problem in Gutsy/7.10, only this happened after some issues w/ my ATI video driver (tried to install the manufacturer driver, didn't work properly, then reinstalled the repository driver). 

I get to the same point you do, but I have to call a command line with ctrl+alt+F1, and "startx" just takes me to a black screen with no functionality.

---

### Post by Unix_Slayer on 2008-06-09
Anyone running any disc arrays? It could be a problem with the way the drive was formatted. Your usr folder is using one drive, or partition other than the main program drive.

---

### Post by MattP220 on 2008-06-10
Mine is an older install that's been working fine for months; it's a dual-boot setup with XP on one partition and 7.10 on another. 

I didn't have any problems until the debacle w/ the ATI driver.

---

### Post by Unix_Slayer on 2008-06-10
> **MattP220 said:**
> Mine is an older install that's been working fine for months; it's a dual-boot setup with XP on one partition and 7.10 on another. 

I didn't have any problems until the debacle w/ the ATI driver.


Ah.... This driver issue never goes away. Be it NVidia, or ATI.

---

### Post by MattP220 on 2008-06-10
> **Unix_Slayer said:**
> Ah.... This driver issue never goes away. Be it NVidia, or ATI.

Yeah, it's been a pain. Update didn't go smoothly, the xorg-driver-fglrx didn't want to uninstall (via terminal or synaptic).

Finally hacked the .postrm file and got that out, then reinstalled the restricted driver from the repositories. That corrected the display issues.

Then I rebooted to finalize, and it's been in this state ever since. I get a terminal prompt, but anything that involves X/GTK/Gnome is a no go. I get a "cannot display" error from any gksudo command, and "startx" just blacks the screen.

Otherwise I'm getting the kinit error above, along with the usual kernel mapping up to 10000 8000-d000 blah blah

No idea where to go from here.

---

### Post by schmidtbag on 2008-06-10
@cariboo:
I do know there is a problem with my /usr directory as well as my /var.  I also know that I didn't manually change anything in those myself, or at least not deliberately.  I deleted absolutly nothing.  The programs in these do work, but only under sudo and even then, some are not fully functional.

@atoponce:
/proc/partitions results:
> 
major minor  #blocks  name
   8   16    39082680 sdb
   8   17    38572033 sdb1
   8   18      506047 sdb2
/etc/fstab:
command not found

@Unix_Slayer:
I'm only using 2 partitions, 1 is the swap.


Thanks for the replies, I really hope you can find a solution.

---

### Post by atoponce on 2008-06-10
> **schmidtbag said:**
> /etc/fstab:
command not found

That is a file, not a command.  So, you need to supply me with it's contents.  Probably via the 'cat' command.

---

### Post by schmidtbag on 2008-06-10
cat /etc/fstab results:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=39d52005-6b37-47e1-9f32-a9ec53ae486c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=fb268714-cc3c-49e7-a453-fe362494d955 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


---

