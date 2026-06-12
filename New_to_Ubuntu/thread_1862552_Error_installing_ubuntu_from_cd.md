---
title: "Error installing ubuntu from cd"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by bellial on 2011-10-16
I have this western digital 1 Tb that used to hold my lucid lynx distro, worked great and then I had to format it (for stupidity issues), and now I'm trying to install it again from the cd (I have one from shipit, both 10.04 and 10.10), and they both produce the same 'can't install, check hd or the quality of the recording' error. I burned it again and tried it, tried on another dvd drive, and nothing! The hd was working fine, I can mount it and use it from a live session with no problems. I'm running the badblocks on it since yesterday, but it didn't give me any feedback yet, is this normal? I can't live without my ubuntu, please help me install it! :cry:

---

### Post by Lisiano on 2011-10-16
This is a interesting error. Could you try using "Try Ubuntu", launching the installer and use "Manual partitioning"/"Something Else" then partition the disk as you wish.

EDIT: If the error persists, please post a screenshot of Disk Utility in System -> Administration -> Disk Utility showing the WDC.

(Note to others: I don't remember how to see if it's MBR, Apple or no partition scheme from fdisk or the likes)

---

### Post by bellial on 2011-10-16
I'll try that now, back in a bit :)

Now that I think about it, I don't know why it never crossed my mind to try by the live session installer! Any regards about ext4?

---

### Post by dFlyer on 2011-10-16
You might want to also boot into a live cd and use disk utility to check your bad sectors. I had something like this 2 years ago and it was a failing hd and disk utility picked it up.

---

### Post by bellial on 2011-10-16
yeah, installing from a live session is a no go. :/
it hangs on 'creating user', and it advises me to report the problem to launchpad and add the contents of /var/log/syslog and /var/log/partman. On to run disk utilities for bad sectors. :(

EDIT: Disk utilities already tells me that there are bad sectors on my hd. I'm running some self-tests.

---

### Post by bodhi.zazen on 2011-10-16
Check the integrity of your iso and CD.

This like describes how to verify both the iso and cd

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by bellial on 2011-10-17
Disk utilities self-test showed 1 bad sector. Can I fix it?

---

### Post by techvish81 on 2011-10-17
if the bad sector is in the boot. area or sector , u will have to change your hdd,  if it is anywhere else,  may be u can use it.

---

### Post by bellial on 2011-10-17
How do I find out where the bad sector is located?

---

### Post by techvish81 on 2011-10-17
I can't tell you 100%. but I think it is in the boot sector, that is why you can't install even after trying many times.  otherwise you would have succeeded atleast once, after trying many times.

---

### Post by bellial on 2011-10-17
Yeah, I guess you're right, but aren't there tools to try and fix bad sectors?

---

### Post by Lisiano on 2011-10-17
There is no need for tools, all those tools do is try to read the block. The disk itself does the fixing, once you Disk Utility notices the bad block it will try to read it a lot, the HDD will notice there is a bad block and remap it. Please note that any amount of bad blocks is a sign of imminent failure, except if you recently dropped the HDD or otherwise caused physical damage to the disk. To see if the bad block is remaped, check that in the "SMART Data" ID 197 has a 0, this means that all blocks are remaped.

Please try to remember if you caused any damage to the HDD. If you did then there is a high chance that the bad blocks won't spread, but if you didn't cause any damage, it's time to start looking for a new HDD.

---

### Post by bodhi.zazen on 2011-10-17
> **bellial said:**
> Disk utilities self-test showed 1 bad sector. Can I fix it?

That is a red herring, more to do with your hard drive, not a reason Ubuntu could not install.

---

### Post by bellial on 2011-10-17
This stinks, I didn't cause any damage to the hard drive, nor can I install ubuntu. What else can I do?

---

### Post by ahmed.cnbd on 2011-10-17
I think you should check your iso file by md5 check

---

### Post by bellial on 2011-10-18
I already tried different iso's, even plugged my hd on a different computer, and no go. :(

---

### Post by Harry.k on 2011-10-18
try installing somethin small like puppy linux to see if it works. If it does, you know nothing is wrong with your computer.

---

### Post by Harry.k on 2011-10-18
> **bellial said:**
> I already tried different iso's, even plugged my hd on a different computer, and no go. :(

Too bad. Looks like your hdd's a gonner

---

### Post by bellial on 2011-10-18
:D it works!!!!
I installed it from a flash drive and it miraculously worked!!! Guess it didn't like cd's after all. Oh the sun is shining again!!! *happy dance*
Thank you guys for sending me good vibes. :)

---

