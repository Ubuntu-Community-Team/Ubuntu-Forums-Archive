---
title: "No boot: attempt to repair or retrieve data/reformat?"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by karrank% on 2013-02-03
Dualbooting 10.04.2 and W7 on a home-built box with a WD 500GB SATA HDD. Today, no boot. Have connected the HDD to my spare box to retrieve the files, mostly some flac, mp3s, and photo files, without success. 

Firstly, how can I access those files? My spare box is also running 10.04. Seems that this would be easier, idk.

Secondly, should I attempt to repair? Or is a clean reinstall/reformat/repartition a better alternative? 

Thanks for looking.

---

### Post by audiomick on 2013-02-03
If the machine wont boot from the drive, and a second machine can't read the drive, I would be worried about the drive being broken. Can you see it at all, for instance with the disk utility on the machine it is now connected to? If you can, look at the SMART values on it. That is a button to the  right of the hard drive utility window. The SMART values are information that the drive stores about itself and the results of self-tests. If the drive has a problem, you might see an indicator of it there.

---

### Post by karrank% on 2013-02-03
Michael. thanks for your reply. What has me flummoxed is the drive utility indicates a healthy drive, I did the basic diagnostics available in that utility and nothing unusual indicated.

Just don't quite know where to start looking for a solution.

additionally, the second drive has some contents available, just not the ones I'm interested in. Weird.

---

### Post by Mark Phelps on 2013-02-03
If you're trying to retrieve files from an NTFS filesystem and that is corrupted, you won't be able to use Ubuntu because it will refuse to mount the partition -- to prevent further file corruption.

In that case, you should try running CHKDSK on that partition with the drive connected to a Windows PC.

If that doesn't work, there are Windows-based data recovery apps that might be able to retrieve the files.

---

### Post by karrank% on 2013-02-03
Thanks for the quick replies, folks. 

Mark, sorry I wasn't more specific, the files I'm trying to access are actually on the Ubuntu partition. (Only have W7 for a couple things really, Harmony remote software & such.)
Thought the gparted function on the Lucid live cd would help, but not so far.

---

### Post by karrank% on 2013-02-17
So, for an update of sorts. Ubuntu disk utilities report no problems with the HDD in question (a relatively new WD 500GB Green)  but when I run a file system check a warning dialog pops up, "file system NOT CLEAN"

I can see system files but no data files, guess my / is gone basically. 

Oh well.

Thanks for the assistance folks.

-Oh, and I tred recova (sp?) to no avail.

---

### Post by Bashing-om on 2013-02-17
karrank%; Hi !

All is not lost yet !
My memory of 10.04 is not real clear, but seemingly I recall there is an option on the live cd to "repair a broken system" (fsck).
To see these booting options:
from cold boot -cd drive set as first boot priority in bios-  at the purple splash screen (stick figure and keyboard at bottom of screen) hit any key -> language screen, escape key to accept the default -> booting options.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by karrank% on 2013-02-18
The continuing saga:

No ethernet last night. 

Switched to my backup box after breakfast and bingo, ethernet. 

So, have to assume a funky mobo (Asus M4A-785M) at this point. Which may have contributed to the originally reported problem. 

Add to this the persistent bios boot note "New CPU detected" (untrue of course) makes me one unhappy camper.

*grumble grumble*

---

### Post by Mark Phelps on 2013-02-18
From what I recall, fsck runs automatically every 30 "mounts" of a filesystem, but if you're having problems with functions suddenly not working anymore, you might want run it daily.  If it finds problems day after day, that's a good indication that your hard drive is failing.

---

### Post by karrank% on 2013-02-18
Thanks folks.

does "check disk for errors" in  the live cd menu check the HDD or just the optical disk?

...AND...now I have ethernet on the original box

Sheesh. Talk about ghost in the machine....

and, mark, I let it run the disk error check whenever it wants, never had an error message. just this... this...*expletive deleted*

---

### Post by Bashing-om on 2013-02-18
karrank%;

I was in error - I booted the 10.04 liveCD to check, that option is not available.
"check disk for errors" -> as you surmised is to check the CD.

Do this instead to run the file system check:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```#if errors: -y auto answers yes for fixes needing response see man e2fsck
```
sudo e2fsck -f -y -v /dev/sdb1
```[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by karrank% on 2013-03-07
And the saga continues. After reinstalling both OS's on the HDD still had random problems powering up/down, random reboots, hangs, &c. 

Finally stumbled across a post in an older Tom's hardware discussion relating this to an AC cord. Just replaced mine and presto, back to what passes for stability around here.

Mark as solved. 

Older, yes, but wiser?  We'll see.


Erm, how to mark as solved? Don't see it in thread tools.....

---

