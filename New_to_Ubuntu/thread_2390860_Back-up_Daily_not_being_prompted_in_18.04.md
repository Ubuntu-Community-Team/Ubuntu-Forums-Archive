---
title: "Back-up Daily not being prompted in 18.04"
date: 2018-05-03
forum: New to Ubuntu
---

### Post by scottm75 on 2018-05-03
This involves the backup program that comes with Ubuntu - Deja-dup.

I was getting notifications in the days leading up to my upgrade from 16.04 to 18.04, to connect my backup device.  And the backup would run seamlessly.  Now with 18.04 Bionic Beaver, automatic prompting is not happening.


My WD Passport external hard-drive shows up on my new Bionic Beaver desktop.  It mounts so I can access files.
I've been running my laptop at all hours, with backup device connected.  Backups is turned on, in both notifications and automatic start-up applications.
Deja Dup has no buttons greyed out.  Schedule is for daily backups.  Backup locations is My Passport (external hard drive).

The other day Deja Dup said I had not back-up for three days.  I was able to run a manual backup.  Today it says again the last one was done three days ago.
I've done some web searching on this and can't find an answer.  

Thanks in Advance.

---

### Post by scottm75 on 2018-05-04
I may have found a solution.  Through some further research I became aware of the deja-dup-monitor file.  I looked in my list of startup-applications.  I found where Ubuntu is looking for this file, it was not located.  It is not located in /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor.

To be safe.  I decided to add a new startup and call it Deja-Dup-Montitor.  To help remind me that it's an item I added.  I put a comment that it was  a manually added backup monitor.
File location:  /usr/lib/deja-dup/deja-dup-monitor   which is where I actually located the file.

I did a reboot.  Waited for a few minutes for the computer to settle or prompt a backup.  I ended up opening Deja-Dup.  Buttons were greyed out and there was a bunch of hard-drive activity for a few minutes.  Program says backup is done and next one is tomorrow.

I will keep an eye on this to see if it continues to work properly.

---

