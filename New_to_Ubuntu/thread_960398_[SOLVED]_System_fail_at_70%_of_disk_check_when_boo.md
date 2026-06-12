---
title: "[SOLVED] System fail at 70% of disk check when booting up"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by unknown user on 2008-10-27
Last night I booted my system up and it run the file check when it was at 70% complete it seemed to freeze for a minute then changed screens and all the writing said [FAIL].
I could write the whole of the error down if it will help, but I was wondering if anyone know any areas I could look at to help resolve this?

---

### Post by philinux on 2008-10-27
Try rebooting again. Hopefully it's not hard disk failure. And yes the error messages are vital to understand whats going on.

---

### Post by teaker1s on 2008-10-27
also worth at grub(may need to hit esc) try booting recovery kernel-I have experienced similar and allowing it to fsck in recovery mode and rebooting has worked for me.

---

### Post by unknown user on 2008-10-29
teaker1s - sounds like the same as my issue as the fsck is in my error message below, how do I go about doing what you mentioned?

Now as soon as it hits 70% the Escape option is on the screen for a few seconds and then the error message below shows:
[COLOR="Red"]
Checking drive /dev/sda1: 0% (Stage 1/5, 0/436)

/dev/sda1:Inodes that were part of a corrupted orpahan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (i.e., without -a or -p options)

Checking drive /dev/sda1: 0% (Stage 1/5, 2436)

*An automatic file system check (fsck) of the root file system failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the foot file system mounted in read only mode.
A maintence shell will now be started.
After performing system maintenance, press control D to terminate the maintenace shell & restart the system.
bash: no job control in this shell
bash: groups command not found
bash: lesspipe:command not found
bash: command: command not found
bash: the: command not found
bash: dircolors: command not found
bash: command: command not found
bash: the: command not foind
root@unknown - laptop ~#[/COLOR]

---

### Post by Elfy on 2008-10-29
Boot into recovery mode - from recovery menu - root prompt and run fsck 

```
fsck /dev/sda1
```

then exit and reume start from the menu alternatively - if you're still where your post shows

```
fsck /dev/sda1
``` and then Ctrl+D

---

### Post by teaker1s on 2008-10-29
either you will get a boot option screen(grub) with various kernels or you will need to hit esc and select recovery kernel option

---

### Post by unknown user on 2008-10-30
Today whilst the laptop was booting I hit the esc button which took me into the recovery mode screen (I think it was).
I selected both Ubuntu 8.04, kernel 2.6.24-16-generic (Recovery Mode) and Ubuntu 8.04, kernel 2.6.24-14-generic (Recovery Mode) and when they have both run I get the same error as put before.

I also hit the C button for the command line and typed fsck /dev/sda1 after grud> and I get the following error:

Error 27:Unrecognized Command

Any ideas?

---

### Post by mc4100 on 2008-10-30
> **unknown user said:**
> Today whilst the laptop was booting I hit the esc button which took me into the recovery mode screen (I think it was).
I selected both Ubuntu 8.04, kernel 2.6.24-16-generic (Recovery Mode) and Ubuntu 8.04, kernel 2.6.24-14-generic (Recovery Mode) and when they have both run I get the same error as put before.
Per "unknown user"'s  post, it seems like the error drops you to a root prompt:

> **unknown user said:**
> <snip>
[COLOR="Red"]
Checking drive /dev/sda1: 0% (Stage 1/5, 0/436)

/dev/sda1:Inodes that were part of a corrupted orpahan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (i.e., without -a or -p options)

Checking drive /dev/sda1: 0% (Stage 1/5, 2436)

*An automatic file system check (fsck) of the root file system failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the foot file system mounted in read only mode.
A maintence shell will now be started.
After performing system maintenance, press control D to terminate the maintenace shell & restart the system.
bash: no job control in this shell
bash: groups command not found
bash: lesspipe:command not found
bash: command: command not found
bash: the: command not found
bash: dircolors: command not found
bash: command: command not found
bash: the: command not foind
***root@unknown - laptop ~#***[/COLOR]

Have you tried forestpixies commands at that point, just after seeing the fsck fail error?

---

### Post by Elfy on 2008-10-30
but have you run the command manually once it's finished trying to boot and you get to the root@unknown - laptop ~# prompt

> A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the foot file system mounted in read only mode.
A maintence shell will now be started.then run the command manually

---

### Post by unknown user on 2008-10-30
How do I run it manually?

---

### Post by Elfy on 2008-10-31
let it get to the root maintenance shell and run

```
fsck /dev/sda1
```

---

### Post by unknown user on 2008-11-01
On the boot screen I clicked Esc and then pressed C for the command line and then typed fsck /dev/sda1, this did nothing.
I am really having problems with this, any ideas?

---

### Post by Elfy on 2008-11-01
let it boot normally, when it's finished trying to boot an dumps you at the prompt you posted - don't escape

once it has tried to do it's check then run the command

---

### Post by unknown user on 2008-11-01
forestpixie - thanks for that, was just how I can understand it. I run the command and it asked me to fix a number of files and after this it rebooted and seemed to go through all OK. I think it has worked now, thanks.

If I get this problem again do I run fsck (then the file name in question) to fix it?

---

### Post by Elfy on 2008-11-01
If you need to do it again then you run it on a partition - dev/sda1 - d/dev/sda1 is the first partition of the first drive.

fsck /dev/partition

If you do get problems it is very important to read the error you are given - in this case it did tell you what to do and where to do it - then it left you in a suitable place to do so :)

---

