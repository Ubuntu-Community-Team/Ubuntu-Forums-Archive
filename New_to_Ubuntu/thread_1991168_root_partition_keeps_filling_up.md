---
title: "root partition keeps filling up?"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by Jmob on 2012-05-30
Since migrating to 12.04 (though I'm not sure this was the cause), I've been having repeated instances of my computer reporting that my root partition is full.  (20 GB, separate from /home and /boot)  Reports first when under a gigabyte, then if left will eventually completely fill.  

I can't find any specific set of actions that would cause this--it often seems to happen first thing in the morning, after the computer has sat for a while, though not exclusively so.  When full, functionality is reduced (some things won't load), though stability remains.

Rebooting the computer seems to clear out whatever it is, and resets to normal, where / isn't even close to full.

I've dug around with an elevated nautilus window and the disk analyzer, thinking this might be some error logging problem, but I can't find anything, despite several searches.  Can someone give me some direction on this?  I'm at a loss.

---

### Post by 2F4U on 2012-05-30
If the situation gets back to normal after a reboot, I would suspect that there is stuff stored in either /tmp or /var. Both folders are for temporary files and should be emptied on a reboot.

---

### Post by Jmob on 2012-05-30
That's what I figured, though I couldn't find anything there.  It's possible I just missed it, but if there were 20 GB of stuff there, why wouldn't a size search find it?

Maybe I'll try something--is there any way to save a record of the contents of a drive at a particular moment (i.e., now, not long after a reboot), and compare it against a later point in time?  That would give me some way to compare and maybe locate this thing.

Thanks.

---

### Post by traditionalist on 2012-05-30
> **Jmob said:**
> Since migrating to 12.04 (though I'm not sure this was the cause), I've been having repeated instances of my computer reporting that my root partition is full.  (20 GB, separate from /home and /boot)  Reports first when under a gigabyte, then if left will eventually completely fill.  

.

I had this, it was caused by tracker indexing files when the machine was not being used. It was a hidden file in root.

---

### Post by Jmob on 2012-05-30
Thanks, trad, I'll look for that too.  Were the hidden files stored in the root folder proper, or somewhere else on the root partition?  

What is tracker, though (or "tracker indexing", not sure which)?

---

### Post by traditionalist on 2012-05-30
> **Jmob said:**
> Thanks, trad, I'll look for that too.  Were the hidden files stored in the root folder proper, or somewhere else on the root partition?  

What is tracker, though (or "tracker indexing", not sure which)?

I had to go looking for it, it was quite well hidden, Found it by using the disk usage analyser as root.

This is "tracker";

[[IMG]http://img41.imageshack.us/img41/1299/selection001i.th.png[/IMG]](http://img41.imageshack.us/i/selection001i.png/)

but there are a couple of other things which are similar. The major problem with it is that there is apparently no way to specify where it places the index. It goes to root by default and I found no way to change it.

---

### Post by drs305 on 2012-05-30
It could be duplicity/deja-dup trying to make backups of your system. You can look for large files with this command:
```
sudo find / -name '*' -size +500M
```

---

### Post by Jmob on 2012-05-30
Trad, I don't have tracker installed, but I wondered if it might be Deja/Duplicity instead, and was writing something up to that effect when drs305 posted.  

I'll definitely use that command come next time (and learn more of its use for the future).  This is how I become competent (well, in a few decades, anyway, at this rate).

Thanks to you both.


Just covering the bases: how likely is it that this is something generating tons of small files instead of a large one, say in a single folder somewhere on / ?  If that is a possibility, can I use a similar strategy to search for a folder of size, as opposed to individual contents?

---

### Post by drs305 on 2012-05-30
> **Jmob said:**
> Trad, I don't have tracker installed, but I wondered if it might be Deja/Duplicity instead, and was writing something up to that effect when drs305 posted.  

I'll definitely use that command come next time (and learn more of its use for the future).  This is how I become competent (well, in a few decades, anyway, at this rate).

Thanks to you both.


Just covering the bases: how likely is it that this is something generating tons of small files instead of a large one, say in a single folder somewhere on / ?  If that is a possibility, can I use a similar strategy to search for a folder of size, as opposed to individual contents?

Your log files could take up a large amount of space if there are enough of them.

For troubleshooting the issue, this thread I created long ago may help:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Jmob on 2012-05-30
Thanks a lot.

---

### Post by Paqman on 2012-05-30
Next time it gets full launch Disk Usage Analyser as root and have a look at where all the space is being eaten up. Hit Alt-F2 and:
```
gksudo baobab
```

That will tell you what's at fault.

---

### Post by traditionalist on 2012-05-30
> **Jmob said:**
> Trad, I don't have tracker installed, but I wondered if it might be Deja/Duplicity instead, and was writing something up to that effect when drs305 posted.  

I'll definitely use that command come next time (and learn more of its use for the future).  This is how I become competent (well, in a few decades, anyway, at this rate).

Thanks to you both.


Just covering the bases: how likely is it that this is something generating tons of small files instead of a large one, say in a single folder somewhere on / ?  If that is a possibility, can I use a similar strategy to search for a folder of size, as opposed to individual contents?


Could be more or less anything really. You have to find it in order to know what is causing it. In my case it was a huge index, but it could be load of small files or a few larger temporary files.

---

### Post by Jmob on 2012-05-30
Thanks, Paqman.   I've used DUA, but didn't have any luck finding it.  It's still in my toolkit, though; previous failure was probably PEBKAC on that one, me just being unfamiliar with the program somehow.  I'll keep it at the ready.

Thanks, Trad.  The linked HOWTO had some info about folder searches that should work for that.  I'll have to internalize all of it, really--I loved linux pretty much from my first moment of trying it, but I've gone too long without getting my file and filesystem management abilities up to a sensible level.  Kudos to Ubuntu and others for getting us to the point where I can be this slack with linux and still have a positive experience, but I'm old enough to know the virtues of having a more robust skillset

---

### Post by jerome1232 on 2012-05-30
When it fills up run this command and post back the results. It will simply list all your top level folders and how much space is being eaten under each.

```
sudo du -hx --max-depth=1 / 2> /dev/null
```

---

### Post by Jmob on 2012-05-30
Jerome, I'll do that.  

I'll keep you all posted of the outcome of these searches and eventual solution (or at least problem identification; shouldn't get ahead of myself just yet).  Thanks everyone.

---

### Post by Paqman on 2012-05-30
> **Jmob said:**
> Thanks, Paqman.   I've used DUA, but didn't have any luck finding it.  It's still in my toolkit, though; previous failure was probably PEBKAC on that one, me just being unfamiliar with the program somehow.  I'll keep it at the ready.


You might have more luck running it as root. I've had trouble in the past with root backup tasks pointing at large network drives that turned out not to be mounted. It would fill the mount point with gigs of data owned by root that couldn't be seen by DUA unless it was run as root.

---

### Post by Jmob on 2012-05-30
I did run DUA as root at least once I recall, but I was probably just unfocused or in the middle of something, because I didn't figure out the problem from it.  Who knows.

[http://ars.userfriendly.org/cartoons/?id=19980506](http://ars.userfriendly.org/cartoons/?id=19980506)

---

### Post by Jmob on 2012-05-31
No luck with find or baobab.  Gparted indicates that the partition is full, as does the warning.  Partition size is 20GB.  

output of sudo du:

```

16K    /lost+found
2.3M    /tmp
4.0K    /home
4.9G    /usr
0    /sys
0    /run
1020M    /var
8.9M    /bin
17M    /etc
131M    /opt
0    /proc
3.0K    /boot
4.0K    /lib64
4.0K    /cdrom
5.1M    /.rpmdb
0    /dev
939M    /lib
4.0K    /srv
4.0K    /selinux
3.4M    /lib32
5.6M    /root
36K    /media
4.0K    /mnt
8.8M    /sbin
7.0G /
```

Still not making sense.  Am I missing something obvious?

---

### Post by steeldriver on 2012-05-31
yes it's odd - I'm really just throwing these out here (don't have experience of either one)

1) you have an unusual reserved block count on that fs (supposedly can be checked / changed via tunefs)

[http://ubuntuforums.org/showthread.php?t=1372331](http://ubuntuforums.org/showthread.php?t=1372331)

2) there are orphaned inodes (basically files that are taking up blocks  but that don't appear to 'belong' anywhere in the filesystem so don't get picked up by 'du')

[http://askubuntu.com/questions/32197/no-space-left-on-device](http://askubuntu.com/questions/32197/no-space-left-on-device)

---

### Post by traditionalist on 2012-05-31
Try bleachbit, it removes a lot of rubbish and also gives indications of blocked files etc;

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

[http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux)

( I got it from the Ubuntu Software Centre originally, but that seems to be offline or not working right now).

You need to run it once as root, and then normally. I have been using it for a while now without any problems at all. Keeps the machine nice and clean.

Some more info on that  [http://www.makeuseof.com/tag/bleachbit-utility-clean-linux-system/](http://www.makeuseof.com/tag/bleachbit-utility-clean-linux-system/)

---

### Post by traditionalist on 2012-05-31
PS:  Precise is not listed specifically  I just used the version for 10.04. Works fine on 12.04. get the bonus pack as well;

[http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux)

I installed these using the  Gdebi Package installer;

[http://appnr.com/package/gdebi](http://appnr.com/package/gdebi)

---

### Post by drs305 on 2012-05-31
Have you checked root's Trash bin to see if there are a lot of files there:```

gksu nautilus /root/.local/share/Trash/files &
```
If you find files there, use SHIFT-DEL to delete the "Trash" folder.

---

### Post by mikechant on 2012-05-31
The fact that 'du' reports only a total of 7Gb out of 20Gb when the partition is full indicates to me that there's something badly wrong with the partition, that it may be corrupt in some way.
Your best bet may be to firstly try a file system check (if you haven't already done this e.g. using gparted from a Live CD), and if this doesn't work backup, reformat and restore this partition using a Live CD/USB.


The backup/restore needs to be done at a file level rather than a partition image obviously otherwise you would probably just restore the corruption.

Possible outline:
Boot from live CD/USB

Use 'sudo rsync -av --progress [source] [dest]'
to back up (-av preserves file timestamps and permissions etc. which is essential).

Confirm that the backup is only using 7Gb approx, not 20Gb.

Use gparted to reformat the partition, confirming that it now shows as 20Gb approx free (a bit less probably due to overheads, maybe 18/19Gb).

Use rsync as above to restore the files.

Confirm space usage is now 7Gb approx.

Anyone see any problems with this method?

---

### Post by choppyfireballs on 2012-05-31
> **Jmob said:**
> Since migrating to 12.04 (though I'm not sure this was the cause), I've been having repeated instances of my computer reporting that my root partition is full.  (20 GB, separate from /home and /boot)  Reports first when under a gigabyte, then if left will eventually completely fill.  

I can't find any specific set of actions that would cause this--it often seems to happen first thing in the morning, after the computer has sat for a while, though not exclusively so.  When full, functionality is reduced (some things won't load), though stability remains.

Rebooting the computer seems to clear out whatever it is, and resets to normal, where / isn't even close to full.

I've dug around with an elevated nautilus window and the disk analyzer, thinking this might be some error logging problem, but I can't find anything, despite several searches.  Can someone give me some direction on this?  I'm at a loss.

we had a similar issue except in fedora then when we transferred the server it stopped in ubuntu, the fix is the same, open up your app browser, and type in disk usage analyzer, run a check on your partition that is filling up and it will sort it by what is using the most storage this will point you towards where your hdd is filling up. Post back when you have run it/know more about where the files are if you are still having issues.

---

### Post by Jmob on 2012-06-01
Thanks, I'll look into this.  Notably, ubuntu just did its own filesystem integrity check at boot, after a reboot this morning, when it had gone down to 0 bytes.  I usually restart it before then, but I've restarted it after and I don't recall it triggering the FS check.  

I'm pretty sure I'm just going to repartition, reinstall and restore from backups, but I'd like to get some info first.  Anyone know where the logs are stored for the check, and what I should do with them?  

as far as rsync backups.  I have a duplicity schedule running already through deja, and my /home partition seems fine.  I'm gathering, though, that you're using rsync as an OS backup/restore, not for my data?  Is this preferable to a reinstall for any particular reason?

Thanks for the help.

---

