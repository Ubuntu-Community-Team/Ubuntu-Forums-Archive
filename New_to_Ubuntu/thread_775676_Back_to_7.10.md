---
title: "Back to 7.10?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by commondork on 2008-04-30
How would I be able to downgrade from 8.04 back to 7.10?  8.04 brought a lot of problems for me whereas 7.10 worked flawlessly.  

A small list of my issues: when I boot the machine, I receive many errors referencing certain memory locations, when I double-click the Home icon on my desktop, I'm given an error there is no application to handle this, and my sound has completely stopped working.

Thanks!

---

### Post by tamoneya on 2008-04-30
there is no downgrade path from 8.04 to 7.10.  This means that you will have to install from scratch using the liveCD.  I know it isnt the most enjoyable thing to do but canonical would rather make 8.04 better than work to make the downgrade path bug free.

---

### Post by mivo on 2008-04-30
You'll have to reinstall 7.10, unless the issues can be fixed (this sounds more like a botched install from perhaps a faulty install disk rather than 8.04 troubles).

If you haven't done this yet, you may consider re-partitioning your system so that you have a separate partition for /home. For example, on my computer I have a 10 GB partition for "/" (the operating system and the applications live here), 237 GB for "/home", and 3 GB for "swap". All personal files like movies, audio files, etc, application settings, and so on are saved in /home, so when I reinstall Ubuntu or upgrade/downgrade, only / is wiped, and my files and application settings remain untouched. That makes upgrading (or downgrading) a matter of an hour (plus what it takes to re-download applications that don't come with the base-install).

During installation, you'd need to choose "manual" partitioning and then only let the system format the / partition (file systems and mount points need to be selected, those being ext3, and / and /home). It's very painless with a set-up like this. (10 GB for / ie even then sufficient if you install a large number of programs -- this isn't Windows. ;))

---

### Post by omns on 2008-04-30
If you have to do a clean install I'd try 8.04 as a fresh install first. It mmight clear up many of your problems :)

---

### Post by commondork on 2008-05-03
I didn't use a CD for the upgrade, I used the Update Manager.

Sound works with Rhythmbox but not with any websites (Flash, etc.).  All of my other problems remain and I'm unable to start MySQL as well.  Ubuntu 8.04 appears twice in the bootloader but booting either option makes no difference as far as my issues are concerned.  Any ideas?  

I would like to avoid an install since reconfiguring and setting everything up again would be a large hassle and a large waste of my time.

---

