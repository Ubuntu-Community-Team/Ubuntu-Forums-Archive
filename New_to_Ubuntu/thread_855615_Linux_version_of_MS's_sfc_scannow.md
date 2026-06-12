---
title: "Linux version of MS's sfc /scannow?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by csu1 on 2008-07-10
Being new to Linux is exciting but I am currently finding it difficult to assure myself that my OS installation files are all intact and in good working order. When using a microsft OS I could type the command sfc /scannow, what is the Linux equivalent to this command may I ask?

Thank you.

---

### Post by phidia on 2008-07-10
I'm not sure exactly because I'm not familar with the program you referred to but take a look at fsck or e2fsck. Open a terminal and type or copy paste > man fsck and read all about it.

---

### Post by dracayr on 2008-07-10
What do you mean by "installation files"? the files on the liveCD/WUBI or the System Files after a fresh install?

the LiveCD can check it's contents. If some of the System Files were broken, you would notice without checking. If not, then you shouldn't care (never touch a running system).

fsck is a filesystem check, not a system file check^^

dracayr

---

### Post by tech9 on 2008-07-10
> **csu1 said:**
> Being new to Linux is exciting but I am currently finding it difficult to assure myself that my OS installation files are all intact and in good working order. When using a microsft OS I could type the command sfc /scannow, what is the Linux equivalent to this command may I ask?

Thank you.

there is no such command - Linux doesn't need to repair itself like Windows

---

### Post by f37u5g0d on 2008-07-10
I once had corrupted files on my harddrive.  Windows happily booted as if nothing was wrong at all.  When I started ubuntu that day during the boot it stopped and told me I had corrupted files on both of my partitions.  I wasn't there (in the shower) when it happened so linux automatically repaired them for me.  Windows continued to bumble around oblivious to the problem.

---

### Post by skymera on 2008-07-10
Amen to above.

If something was wrong, It would detect.

Don't fret.

---

### Post by csu1 on 2008-07-10
> **tech9 said:**
> there is no such command - Linux doesn't need to repair itself like Windows

So I never need to worry about it? The virus immunity got me hooked, now you're telling me Ubuntu doesn't break or need maintaining!

Happy days! 

Thanks

ps. on the other hand it would nice to be assured everything is 100%, so there's no command to ask if everything is in place and in tip-top shape?

Sorry, for some reason I just feel like I need confirmation, even two letters like 'OK' LOL, sorry:popcorn:

---

### Post by dracayr on 2008-07-10
your System is working, that's confirmation enough, so:

OK

dracayr

---

### Post by chili555 on 2008-07-10
By default, *fsck* is run every 30th time the file system is mounted, generally, every 30th time you boot. You can check the report of the last check with:```
cat /var/log/fsck/checkfs
cat /var/log/fsck/checkroot
```Your indication that all is nice and tidy will look something like:> /dev/sda1: clean, 273363/1987136 files, 1643010/3968047 blocksIf, during boot, things are *not* tidy, your file system will be mounted read only, you will be dropped to a root prompt and asked to run fsck manually. You will then be asked if you want the system to attempt to repair any errors. (Well, certainly!) After the process finishes, you will reboot and carefully consider the age of your harddrive, purchasing a UPS and the frequency of your backup process.

---

### Post by ajgreeny on 2008-07-10
The MS sfc (system file checker) is needed by windows as it is very good at messing up its own system files, it seems to me.  Linux and ubuntu doesn't do that, or not nearly so much nor so easily, anyway.  Just make sure you keep your system updated with the security and recommended updates, and all should be well, and comfort yourself that if the system should go totally bonkers, it is only about 30 minutes to reinstall, and so much easier than reinstalling windows.

---

### Post by csu1 on 2008-07-10
> **dracayr said:**
> What do you mean by "installation files"? the files on the liveCD/WUBI or the System Files after a fresh install?

the LiveCD can check it's contents. If some of the System Files were broken, you would notice without checking. If not, then you shouldn't care (never touch a running system).

fsck is a filesystem check, not a system file check^^

dracayr

Not system files after a fresh install, a check to see if any sys files have been overwritten only by me. btw tbh im scared shitless as my *[microsoft management console]("http://technet.microsoft.com/en-us/library/bb742442.aspx")* is gone. GUI's FTW! *[scf /scannow]("http://support.microsoft.com/kb/310747")* 

what GUI's do I need to comfortably administrate Ubuntu? my command line effort is weak at best:)

---

### Post by bludgard on 2011-01-01
Deleted.
Didn't look at the date.

One

[]("http://ubuntuforums.org/showpost.php?p=5359977&postcount=9")

---

