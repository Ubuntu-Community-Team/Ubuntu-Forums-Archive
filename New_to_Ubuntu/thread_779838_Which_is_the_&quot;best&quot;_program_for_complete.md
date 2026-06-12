---
title: "Which is the &quot;best&quot; program for complete backup?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by yc2 on 2008-05-03
Hello

I just installed Hardy as dual boot with Vista on my HP laptop. I am very happy with Hardy and at least for the computers I have used, my first impression is that it seems to have even better hardware compatibility than Feisty, Gutsy.

Please tell me, how do I make a **complete** backup. Which is the best **complete** backup program, easy to use GUI, reliable ... I like to make frequent backups of my systems on external (USB-connected) disks.

I only have two partitions (root and swap) and I would like to be adviced about a quick and simple way to make a FULL copy of these two (maybe swap is not needed?) partitions on an external disk.

Thank you

---

### Post by tamoneya on 2008-05-03
i personally use sbackup.  It has a nice gui plus it easily allows you to save your backups over ssh which is idea incase you get a corrupted filesystem or a harddrive failure.  
As for backing up you swap partition that is totally unnecessary.

---

### Post by yc2 on 2008-05-03
Thanks for the advice.

sbackup installed without complaints through synaptic, but I couldn't find the program. not in usr/bin, not under the applications menu. So I don't know how to start it!

I found "keep" under applications, but it did not work well, the panel blanked out after the scrensaver had been on, there was no information on how long time the process was about to take. My feeling was that the program was finished but not responding, it had worked for quite a while.

I have also heard about flyback but I cant find it in synaptic.

So please give me further advice:

How do I start sbackup, I cant find it.
Should I also try something else, like f.ex. flyback?

Thanks

**EDIT**
I found the sbackup program folder in usr/share/
in the folder I found the following script (named sbackup), which however, hangs on startup.
```
#!/bin/bash
#
# Sbackup Service file used by anacron

if [ -x /usr/sbin/sbackupd ]
then /usr/sbin/sbackupd
fi
```

---

### Post by louieb on 2008-05-03
**partimage**
**pros:**  fast, reliable, full partition backup and restore. Can be run from command line or nursors interface. option  to compress image.

**cons:** must be run from a live CD, ancient ncursors interface. Full -  all or nothing  backup and restore (cannot  selectively restore individual files).

What can I say? partimage is what I use before making major changes to my system such as  the every 6 month distribution upgrade.

---

### Post by yc2 on 2008-05-03
Thanks, I found the partimage webpage. The ncursor interface wakes up old memories. Looks like a very useful program. Individual files that may have to be restored I usually back up separately.

Fast, reliable - important qualities.

Run from Live CD is also an advantage I think. (No temptation to fiddle around when backup is running.) I have had 99% of very good experiences with Norton Ghost. However, once I was only editing one single manuscript lying on the desktop while the backup was running. Result: Not one single file or folder from the Desktop was included in the backup!! (XP/Norton Ghost ver. 8 )

---

### Post by cpbl on 2010-05-11
Yikes, this thread is ancient, but sad it never got replied to.
After installing sbackup, lookin the System->administration->Simple bckup config.

---

### Post by derande on 2010-05-11
Clonezilla has saved my life before.

---

### Post by Kellemora on 2010-05-12
I don't trust ANY backup program!  I've had too many of them fail on me!!!!!

I MIRROR my working drive to an external drive, then mirror the external to an off-site location.

Since a corrupt file will be mirrored destroying your external mirror, I keep a small external and just copy DATA under the date the copy was made of the data file.  Eg copy /home to the MayTwelveTen folder.  Tomorrow, copy /home to the MayThirteenTen folder, and as the drive gets full, delete remove AugustEightSeven folder.  You'll be surprised how many copies of /home you can keep on an old 120 to 250 gig external drive!

TTUL
Gary

---

### Post by yc2 on 2010-06-10
Well, we keep this thread alive. (And the mods will kill us ;) )

Installing Lucid I realized that partimage that I have trusted for a long time didn't work with ext4.

I have now started using clonezilla Live CD. It always does the job, but sometimes dies from exhaustion afterwards. (Last printout: PCI ... followed by black dead screen)

---

