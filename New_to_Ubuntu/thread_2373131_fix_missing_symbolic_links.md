---
title: "fix missing symbolic links"
date: 2017-10-03
forum: New to Ubuntu
---

### Post by firesdhgsht on 2017-10-03
After I did 

```
find -type l -delete
```
in the root as admin I cant mount my hard drive, not even from a live linux stick. How do I repair the missing symbolic links? Thanks.

---

### Post by Impavidus on 2017-10-03
You ran that command in the root directory as the root user? Why? On my system that would have deleted 74824 symbolic links, surely breaking the entire system. The only realistic way to fix it is a fresh install.

However, you should be able to access the file system from a live usb to backup any files you need. What error messages do you get when you try to mount the partition? Is it encypted?

---

### Post by firesdhgsht on 2017-10-03
... because someone on stackoverflow said it would get rid of symlinks. And I thought I set one earlier that was now causing problems so I was glad I found that helping hint. Obviously Linux does not ...[deleted because of rock throwing tendency].

This is what I see trying to mount:
> udevil: /dev/sda4 is known to mount - running mount as current user
udevil: warning 45: options ignored for device in fstab (or specify mount point)
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

... meaning, it does not mount, hence no access.

---

### Post by ian-weisser on 2017-10-03
> **firesdhgsht said:**
> Obviously Linux does not warn the user when it is about to destroy the entire notebook.

This sentence is rock-throwing, and will turn off many potential helpers. Consider an edit to soften it.
Linux does have a great many safeguards included...but human folly sometimes will not be stopped.
The power to build your system your way is also the power the cause great damage.

Impavidus is right - you seem to have destroyed your system beyond convenient repair.
If you lack backups, then use a LiveUSB to preserve your data to a different media.
Then reinstall.

---

### Post by DuckHook on 2017-10-03
> **firesdhgsht said:**
> This is what I see trying to mount:
…

Also, please don't duplicate post. It confuses those trying to help and dilutes community effort. I have moved your other duplicate posting out of public view.

---

### Post by QIII on 2017-10-03
> **firesdhgsht said:**
> Obviously Linux does not warn the user when it is about to destroy the entire notebook.

Not when you are in / as root, it doesn't.  It allows you to choose to destroy your entire installation if you tell it to.  You are the boss, not the OS.  This should be no "surprise".  A Windows user can do the same thing from the command line while operating with admin privileges.

Where exactly did you find these instructions?

---

### Post by SeijiSensei on 2017-10-03
Before proceeding, back up the contents of /home onto another device, then reinstall from scratch.  Afterwards, copy back the contents of /home.

---

### Post by Impavidus on 2017-10-04
> **firesdhgsht said:**
> ... because someone on stackoverflow said it would get rid of symlinks. And I thought I set one earlier that was now causing problems so I was glad I found that helping hint. Obviously Linux does not warn the user when it is about to destroy the entire notebook.

This is what I see trying to mount:


... meaning, it does not mount, hence no access.

I see. People shouldn't give such dangerous advice. Instead of removing the offending symlink (which can simply be done with **rm**), this removes all symlinks.

Boot a live usb. Have a look at the partitions present on the hard drive:```
sudo parted -l
```
Is the one you want to mount /dev/sda4? Try```
sudo mount -o ro /dev/sda4 /mnt
```
It should mount at /mnt. I added the read-only option, which is more likely to succeed if something is wrong with the file system. You won't be able to write to the partition, but should be able to copy files to your backup drive.

If it doesn't mount, maybe it needs a file system check. It may not have unmounted cleanly when you shut down your damaged system.```
sudo fsck /dev/sda4
```

---

### Post by firesdhgsht on 2017-10-04
Thank you all. I was able to save some data with a rescue disk and with  some trail and error manually mounting attempts via Testdrive but e.g.  the Thunderbird profile was destroyed, it could not be copied. fcsk said  sda4 would be in use so it could not continue. Now I just reinstall and  redo my work in Thunderbird and what else got destroyed and hope to  never ever have to use the terminal again.

---

