---
title: "Deja dup trouble"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Applesauce on 2011-11-16
I just switched to 11.10 from 11.04. After the switch I started using Deja dup to back up my Ubuntu on an external hard drive.
Just in the past few weeks, it started giving trouble. It goes to start a scheduled backup and asks for the password and then it refuses to recognize it. I have not changed passwords so I don't know what ails it.
Any ideas on what I should try?

---

### Post by Applesauce on 2011-11-17
Hello? Is there anyone that would have some advice for this problem? I tried uninstall/re-install but that didn't do any good.

I hope I can get this thing working again, I would like to have a backup because I am thinking of making some major changes to the computer.

---

### Post by Jacobonbuntu on 2011-11-18
Hi Applesauce, I did have kind of the same problem; I tried them all, sbackup, deja dup and whatever you can think of, but all turned out to be rather unreliable and very (Ubuntu-) version "connected".

What I use is Grsync. very easy to set up and if you copy the output when you run the backup once, you can make a quicklist in the Unity launcher with your backup commands, or make them run automatically with cron. If you keep your directories as it is on the next upgrade, you can be sure the scripts will keep on working. (G)rsync is basic system stuff and not likely to "catch a cold" in the next Ubuntu version. :)

note*
if you copy the output of Grsync, be sure to put directory-names with spaces in it between "", or else the script will "end" at the space.....

---

