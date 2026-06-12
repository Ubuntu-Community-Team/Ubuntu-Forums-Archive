---
title: "Need Emergency disk checker help!"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by skymera on 2008-06-28
Hi!

Ermm well my XP has eaten itself and black ooze is spilling out my PC and XP won't start.

I'll start from the beginning, i was hoping to resize my XP in order to install a test Debian Etch for me to try.

All went well it seemed to resize with Parititon Magic (restarted first) then it errored.

Turns out the error was a chkdsk was scheduled, so i restarted after setting the /f and /r options and it started normally checking, then something weird happened.
I remember as good as i can "Deleting an index entry of index $0 of file 25"
That sometimes happens but this time it kept sayint that for TWO HOURS!

So eventually i had to use my PC and pulled the plug.. (No HDD light active) XP worked fine.
Anyway tried again today and the same thing, so i popped in the XP disk and done a chkdsk in recovery mode, no luck it locked at 25%.
I restarted and went to check XP now, i got a BSOD and failed to boot.
I can't get it to boot at all!
bsod, bsod, bsod.

Ive tried safe mode, ive tried best config.

Is there a Ubuntu program that can check NTFS partitions??
I feel a reinstall is closing in.

Sorry if wrong section, i feel this is where most people look.

---

### Post by Elfy on 2008-06-28
I found a post by herman which might be of some help, using ntfsprogs from linux

[http://ubuntuforums.org/showpost.php?p=4556510&postcount=2](http://ubuntuforums.org/showpost.php?p=4556510&postcount=2)

I knwo you can do from linux, but I never needed to try and last ntfs I had was last year now.

I'd certainly trust herman though I think  :) hope it can help

Edit there is a bit of a list at the package page with the things it can do


[http://packages.ubuntu.com/hardy/ntfsprogs](http://packages.ubuntu.com/hardy/ntfsprogs)

---

### Post by moore.bryan on 2008-06-28
you could also try badblocks from the cli... takes a while to run and i'm not sure it goes with ntfs.

---

