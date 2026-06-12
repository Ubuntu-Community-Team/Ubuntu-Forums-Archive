---
title: "Cannnot mount hard drive"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by omi291 on 2008-10-19
Well, my friend cannot use windows becuase a vital file(C:\windows\system32\config\system)is corrupt or missing. So we decided to use the ubuntu live cd to get whatever files he needed from his hard drive, but we get an error saying "Cannot mount volume" and we are given two options:

1) Start up windows and shut down properly (which we cannot do)

2) Or type this command into the terminal:

```

mount -t ntfs-3g /dev/sda2/media/disk -o force

```

or add the option to the /etc/stab file: /dev/sda2/media/disk ntfs-3g force.

What would be the consequences of running this command? And would it be solved if we just did an install of ubuntu instead?

Thanks for the help :)

---

### Post by omi291 on 2008-10-19
Anybody willing to help? Please? It would be much appreciated.

---

### Post by ajgreeny on 2008-10-19
I would not normally recommend running that command but rather booting into windows and shutting down properly as the message says, but you seem to have no other option.  When windows is shutdown wrongly by power-outage or something similar there is a "lock" put on the ntfs file system which will not allow linux to mount the drive/partition.  You have no real option other than using this force command to get the partition mounted and then backup the files you want to.

Installing ubuntu will make absolutely no difference to you, it will still only mount the partition if forced using that command.  You may need to add sudo to the front of the command, but I'm not sure.  It shouldn't cause any problem to your windows partition, so go ahead and give it a try.

---

### Post by anystupidname on 2008-10-19
The consequences of mounting with the force parameter are that the dirty bit will get ignored/reset which essentially just says "assume the file system doesn't have any inconsistencies".

Installing Ubuntu vs. running it from the liveCD would not change anything. You have to make the decision for yourself, but I've forced an NTFS volume mount countless times without problems.

For another option if you're curious/worried see:
```

sudo aptitude install ntfsprogs
man ntfsfix
```

---

### Post by Shazaam on 2008-10-19
Download and burn a Knoppix livecd. ntfsprogs/ntfsfix is included on the cd.

---

### Post by omi291 on 2008-10-19
Well, I tried force mounting...but i have a syntax error because the terminal keeps on giving me a page about the entire structure of the mount command. I'm assuming i'm typing in the wrong directory name since there is no such volume as "disk" on /media. The volume's name is "495.1 GB Media" and even after exchanging names, i still got a syntax error. o.O

EDIT: I also tried ntfsfix after installing ntfsprogs, and this is what i got:

```

Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk

```

and the hard drive diagnostics passed.

---

### Post by captclearleft on 2008-10-20
Hey bub,

just to let you know, Im a total noob with the linux.  However...

I have had a similar situation with one of my raid arrays on an xp machine.  

The array would not boot do to a corrupted boot file.  I too tried creating a linux system on a seperate drive to try and get the info off the corrupted one.  It never worked.  I hit my head against the wall several times.

But I did find a fix.  Not sure if this will help.

I created a new xp install on a seperate drive, installed corrupted drive into machine as slave, and recovered what i needed.  

I then used the recovery consule on the xp disk to repair the corrupted file.  Help for this can be found on their website (MS).  Good Luck, Im learning...

---

