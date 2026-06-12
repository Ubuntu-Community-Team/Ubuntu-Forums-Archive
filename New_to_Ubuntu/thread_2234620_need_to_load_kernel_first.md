---
title: "need to load kernel first"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by izirider on 2014-07-15
hey everyone,

yesterday installed updates after 6 months of off-line, there were one comment of 1 important package... don't ask me name, cannot remember. when tried to start my computer today surprise!. cannot find way to make it work. no doubt, cannot be too complicated. even if google doesn't know...:confused: only ubuntu isntalled in a system.

thanks in advance. 

tired to have a PC as a brick :mad:

P.S.: sorry for poor quality of pictures. hopefully can be seen...

[ATTACH=CONFIG]254746[/ATTACH][ATTACH=CONFIG]254747[/ATTACH]

---

### Post by mooreted on 2014-07-15
Sounds like the Grub boot loader is messed up. You might try the Boot Repair CD:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2014-07-15
> there were one comment of 1 important package... don't ask me name, cannot remember

OK, I won't ask but suggest that you keep a pen and paper handy in the future as it could simplify these problems.

One guess is a kernel update and grub wasn't updated to reflect this.  The Boot Repair CD might fix this for you.

---

### Post by izirider on 2014-07-16
thanks everyone for such a quick response. today i've taken some *screenshots* more, , command line doesn't take me anywhere. have tried to start system with bootrepair from flashdrive with ISO image on it still nothing. sorry, my knowledge of Linux is not too advanced. it just... works, and normally doesn't require advanced skills... 

[ATTACH=CONFIG]254777[/ATTACH][ATTACH=CONFIG]254778[/ATTACH][ATTACH=CONFIG]254779[/ATTACH][ATTACH=CONFIG]254780[/ATTACH]

---

### Post by NM5TF on 2014-07-16
> **izirider said:**
> thanks everyone for such a quick response. today i've taken some *screenshots* more, , command line doesn't take me anywhere. have tried to start system with bootrepair from flashdrive with ISO image on it still nothing. sorry, my knowledge of Linux is not too advanced. it just... works, and normally doesn't require advanced skills... 

[ATTACH=CONFIG]254777[/ATTACH][ATTACH=CONFIG]254778[/ATTACH][ATTACH=CONFIG]254779[/ATTACH][ATTACH=CONFIG]254780[/ATTACH]

do you mean that you actually tried using the boot repair app from here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

or did you use the "recovery" option from the USB iso image ???

tommy

---

### Post by izirider on 2014-07-16
recovery mode doesn't work, starting from USB cannot help. comands for terminal neither (pc doesn't even know what *sudo* means - guess, it's something with GRUB was deleted as an disconitinued library. system doesn't even start from CD in mode "try ubuntu". personally known, linux-experts out of reach... don't have an idea were from to start... perfect circle, in short words! :confused: for boot-repair must be at least loged in? don't have this option...

---

### Post by grahammechanical on 2014-07-16
First, Grub does not use terminal commands. Grub has its own set of commands. But the simple and easy way to solve this is to use a live session to back up your data and then re-install. I have done this in the past. I keep all my documents on a separate partition so that re-installing is almost painless.

Regards.

---

### Post by NM5TF on 2014-07-17
@izirider...

go to the link I mentioned earlier & download Boot Repair to a CD or USB....

boot repair will run from a CD or USB...go to the BIOS to set it to boot from either
CD or USB....follow the instructions & select "recommended repair" button...let it
work & then reboot...

or do as Grahmmechanical suggested & reinstall....

tommy

---

### Post by izirider on 2014-07-17
i've tried... i'm not keeping secret that it's quiet diffcult for me to solve this problems, unless step-by-step detailed sequence is described. no possibility to start ubuntu, when choosing by F8 "start from USB" on the next screen appears "GNU GRUB version 1.99-21ubuntu3", when choose "Ubuntu, with Linux 3.2.0-58-generic pae (recovery mode)" next message as follows

[ATTACH=CONFIG]254802[/ATTACH]

---

### Post by coffeecat on 2014-07-17
Third on the list in the grub menu is "previous Linux versions". Have you tried selecting that? If you do, it will take you to a secondary menu where you can choose a previous kernel. See if you can boot with one of the older kernels.

---

### Post by izirider on 2014-07-17
yes, i did, even the very first in a list, not succeeded:mad:

anyhow, appreciate attention of all who tries to assist me;)

---

### Post by izirider on 2014-07-20
> **grahammechanical said:**
> First, Grub does not use terminal commands. Grub has its own set of commands. But the simple and easy way to solve this is to use a live session to back up your data and then re-install. I have done this in the past. I keep all my documents on a separate partition so that re-installing is almost painless.

Regards.



hello,

can you tell me, step-by-step, how to proceed?

thanks in advance

---

### Post by Rob Sayer on 2014-07-20
What you want to have a according to what you quoted is a separate data partition.  What you want there is to reinstall and when the formatting section comes up set it up with a separate partition for /home.

Google is your friend ... though I rarely use it, usually startpage or duckduckgo.  Search for "ubuntu install separate /home partition" or something like that.

When doing that kind of thing remember that sources actually from ubuntu sites are usually preferable to others.  There are some very good ones of the latter but the thing is, just because someone writes a linux blog does NOT mean they know what they're talking about.  I've seen pretty bad advice out there.

My netbook has had some hardware support issues previous to 14.04 so I've desktop/distro hopped a bit before settling on xubuntu 14.04.  In the process I've lost whatever fear I had of installing ... at least with ubuntu, not something like Gentoo.

Sometimes it really *is* faster and easier to reinstall rather than try to find out what the problem is.  And if you install with a separate /home partition all your user data and program settings are still there the next time you reinstall ... unless you forget to not tick the box to format /home.

Nevertheless, even though your data would still be there you still want it backed up.

---

