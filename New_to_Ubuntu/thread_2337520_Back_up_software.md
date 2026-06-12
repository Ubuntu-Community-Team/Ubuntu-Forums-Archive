---
title: "Back up software"
date: 2016-09-19
forum: New to Ubuntu
---

### Post by ray42 on 2016-09-19
I'm new to Gnome. Generally I'm an Intermediate user, have used Mint, longtime Windows user

What is the best app to backup all software, including users personal files?

---

### Post by ajgreeny on 2016-09-19
Hello ray42 and welcome to the forum.

That is a very difficult question to give an simple answer to as you will get almost as many different answers as the number of people who reply; everyone seems to have their favourite way of backing up, and as long as you have what you really need backed up somewhere safe, that will be the right answer for you.

To start the ball rolling, personally I use rsync, in fact generally grsync, a GUI front-end to the command-line rsync and backup to an external hard disk.
I back up only my /home and don't worry about the OS itself or any software, as it is a matter of about 45 minutes only to reinstall my whole system as I use a separate /home partition.  As far as I'm concerned it is my personal files and folders that are important to me and can not be replaced; the OS can be quickly and easily.

Look in gnome-software or ubuntu-software, whatever it is called and search for backup packages and you will probably find lots of possible options.

---

### Post by cmcanulty on 2016-09-19
Yes I agree the most important thing is to have your /Home on a separate partition. Also grsync has a simulate option so you can run it to see what it does once without risking anything-hit the light-bulb icon in top right. The only thing with grsync if you have delete on destination option checked, be absolutely sure you have the destination as the backup place not the source or you delete your source.

---

### Post by ray42 on 2016-09-19
> **cmcanulty said:**
> Yes I agree the most important thing is to have your /Home on a separate partition.

Aha! OK I don't have /Home on a separate partition. How do I move it?

---

### Post by ian-weisser on 2016-09-19
ajreeney is totally right...about everyone having a different opinion.

I *don't* use a separate /home partition, and life rolls along just fine. I simply don't reinstall often enough to bother. Ubuntu is solid.
I *do* backup my /home folder regularly. And every few years test restoring data from the backup. A backup is worthless if you cannot restore from it.

The base system is very easy to reinstall from your original install media, so there is no gain backing that up. Simply retain (and occasionally update) your USB installer.
The applications are (nearly) all freely available from the Ubuntu Repositories, so there is no gain backing those up. A few jotted notes is usually all you need.
The simplest way to backup all your email and documents and other data in /home is 1) Plug in external device, 2) Copy /home to external device using the normal File Manager, 3) Unplug external device, 4) mark calendar for next backup.

Easier ways are available, once you get comfortable with the command line.

If you really want a separate /home partition, then you must use a LiveUSB to repartition your hard drive. Not something I recommend to a new, unskilled-at-linux user.

---

### Post by PartisanEntity on 2016-09-19
It all depends on your needs/requirements.

Generally I have had mixed results with Ubuntu's built in back-up tool (found under Settings). It has been hit and miss so far, with certain backups becoming corrupted for no apparent reason. 

I have also opted to use rsync to copy documents and incremental updates to a small home server.

---

### Post by ray42 on 2016-09-20
OK thanks all

---

### Post by ajgreeny on 2016-09-20
Great! If everything is now solved for you please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by izznogooood on 2016-09-20
> **PartisanEntity said:**
> It all depends on your needs/requirements.

Generally I have had mixed results with Ubuntu's built in back-up tool (found under Settings). It has been hit and miss so far, with certain backups becoming corrupted for no apparent reason. 

It also has bugs, entering dirs it should not.

---

### Post by deadflowr on 2016-09-21
> **izznogooood said:**
> It also has bugs, entering dirs it should not.

What would those be?

---

### Post by izznogooood on 2016-09-21
[COLOR=#000000]~/.dbus and ~/.cache

[/COLOR]These should be ignored.

[https://ubuntuforums.org/showthread.php?t=2319715&highlight=deja+dup+izznogooood](https://ubuntuforums.org/showthread.php?t=2319715&highlight=deja+dup+izznogooood)

---

### Post by leunam12 on 2016-09-21
I use clonezilla to backup my system partition and rsync to backup my /Home partition. The reason I backup my system partition is because sometimes things go wrong and the system breaks and it takes 5 minutes or less to restore the partition.

---

