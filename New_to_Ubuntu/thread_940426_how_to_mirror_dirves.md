---
title: "how to mirror dirves"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by fr.theo on 2008-10-07
i was wondering if it were possible to mirror my root drive which contains my Ubuntu installation onto another drive.

---

### Post by Gazneth on 2008-10-07
rsync is a command line tool to synchronize files across drives or even across a network. I use grsync which is a graphical program to make it simple to do what you need. The grsync package is in the ubuntu repository. Always double check your source and destination when using this program.

---

### Post by Dark_Stang on 2008-10-07
gparted may be able to do it. I'm pretty sure Acronis True Image can if gparted can't... as long as they didn't drop their linux filesystems support...

---

### Post by kansasnoob on 2008-10-07
partimage

It's in the repos.

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by wizard10000 on 2008-10-07
Do you need to mirror just the files or the entire partition?

If you're just making a backup I'll echo Gazneth's suggestion that you use rsync - I use it to back up home directories on one Hardy machine and one XP machine plus all the audio and video on my media server and my desktop workstation's /etc directory.  I haven't used grsync and command-line rsync's commands can be a little intimidating but not that hard once you play with it a little.

Good luck -

---

### Post by Paqman on 2008-10-07
> **wizard10000 said:**
> I haven't used grsync

I have, it's excellent. Highly recommended.

---

### Post by Liviu-Theodor on 2008-10-07
You can not mirror the drive on which resides the OS. So probably you will have to use a live CD and from it to run what the others suggested. But I know that is possible to do. You can install programs even when you start ubuntu from the live CD, but these are of course lost when you restart/shutdown the computer.

---

### Post by wizard10000 on 2008-10-08
> **Paqman said:**
> I have, it's excellent. Highly recommended.

I checked it out.  Interesting frontend for quick and dirty copying and it might be pretty neat run as a cron job for scheduled backups - it's certainly easier than remembering rsync command line options.

thanks -

---

