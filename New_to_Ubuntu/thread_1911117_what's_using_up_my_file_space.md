---
title: "what's using up my file space?"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by coalhole on 2012-01-18
I'm using Ubuntu 10.4 on my N130 netbook... My system monitor tells me that I've used 52% of my available file space... I actually store  nearly all of my documents on an external memory stick and cannot see where this growing file volume is coming from... The only new items I'm aware of going onto the hard drive are Ubuntu updates.... 

I'm an absolute beginner with ubuntu especially with command line operations....

Any suggestions welcomed....

---

### Post by lykwydchykyn on 2012-01-18
The updater caches downloaded packages indefinitely, in case you want to reinstall them.  The command to clear this cache is:

```

sudo apt-get clean

```

That should clear the entire package cache.  It can easily free up a Gigabyte or more, if you've been updating or installing a lot.

---

### Post by Elfy on 2012-01-18
I'd have a look at the Disk Usage analyzer - sytem admin menu I think. You can see what is where in there.

You can run 

```
df -h
```

and post that so people could see if it is more or less normal.  > tells me that I've used 52% of my available file space...could be perfectly normal - no idea for anyone else to tell without some more information :)

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[https://help.ubuntu.com/community/Baobab](https://help.ubuntu.com/community/Baobab)

---

### Post by mastablasta on 2012-01-18
what is the total disk size you dedicated to Ubuntu?
 
Updates can take space, as they include whole kernels (system core). Old Kernels can be removed, if new ones don't present any issues to you.

---

### Post by coalhole on 2012-01-18
lykwydchykyn.. when I follow your suggestion the response is a demand for a password for "robert"... and I don't know of one....


forestpiskie...

here's what I get with df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   72G   66G  52% /
none                  493M  264K  492M   1% /dev
none                  497M  420K  496M   1% /dev/shm
none                  497M   88K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw 

Thanks....

---

### Post by Elfy on 2012-01-18
The password will be the admin password, which assuming you are the first user created is yours.

Ok - now we can all see there is a lot of data there - did you look at any of the links I left ?

---

### Post by drs305 on 2012-01-18
coalhole,

If you look at one of the links *forsestpiskie* posted it can walk you through commands that will help you determine the problem. There are commands for searching for large files which normally aren't found in the system folder. It also discusses the possibility of mistakenly made a backup on the / partition instead of a backup partition, which is often the cause of large amounts of disk space being 'lost'.

Here is the link again:
[HOWTO: Recover Lost Disk Space ]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by coalhole on 2012-01-18
lykwydchykyn... I've used "sudo apt-get clean" and its given me back 1%... It's good to know that procedure.... 

Everyone...... I'm going to work through the suggestions and links you've given... slowly.... to avoid the stress I know I experience with new systems and because the problem isn't yet urgent... But I'll let you know how I get on... in the fullness of time...

Thanks for all your suggestions.:)

---

### Post by sudodus on 2012-01-18
> **forestpiskie said:**
> I'd have a look at the Disk Usage analyzer ...
I also suggest that you use the Disk Usage analyzer. If you can't find it in the menu system its name is ***baobab*** and you can install it with the terminal command
```
sudo apt-get install baobab
``` or with the gnome environment ```
sudo apt-get install gnome-utils
```

---

### Post by mikechant on 2012-01-18
I would expect a Ubuntu install to use less than 10GB even if you've installed loads of packages and never done any 'housekeeping' at all. 
So you've got massive amounts (60GB+) of other data. 

One explanation is that you've somehow ended up with a copy of all the data you keep on your USB stick duplicated on your hard drive. 

How big is your USB stick and how much data do you have on it?
Also, with your USB stick and any other external drives disconnected, do you see any files in the /media directory?

And, as per a previous post, have you been doing any backups?

---

### Post by coalhole on 2012-01-18
Thanks Mikechant... I have done backups... a couple I think after fixing a major password problem... Where do I find the /media directory?

---

### Post by coalhole on 2012-01-18
Thanks Sudodus... I'll try that and let you know the result... But not until tomorrow...

---

### Post by coalhole on 2012-01-20
Well... I'm now back down to 27% file space usage but I'm not at all sure of how I did it!

I used "sudo apt-get clean" to clear my updater cache which restored 1%...

I used "sudo find / -name "*" -size +1G" to find files over 1 gig.... thus...

find: ‘/proc/1842/task/1842/fd/5’: No such file or directory
find: ‘/proc/1842/task/1842/fdinfo/5’: No such file or directory
find: ‘/proc/1842/fd/5’: No such file or directory
find: ‘/proc/1842/fdinfo/5’: No such file or directory
/var/backup/2011-11-04_08.43.54.972438.robert-laptop.ful/files.tgz
/var/backup/2011-11-11_08.14.44.737873.robert-laptop.ful/files.tgz
/var/backup/2012-01-13_08.04.08.220318.robert-laptop.ful/files.tgz
/var/backup/2011-11-18_08.20.22.475711.robert-laptop.ful/files.tgz
/var/backup/2011-12-23_08.24.49.563864.robert-laptop.ful/files.tgz
/var/backup/2012-01-06_09.14.18.019212.robert-laptop.ful/files.tgz
/var/backup/2011-12-09_08.08.07.755369.robert-laptop.ful/files.tgz
/var/backup/2011-12-30_08.23.03.690643.robert-laptop.ful/files.tgz
/var/backup/2011-11-25_07.52.15.606099.robert-laptop.ful/files.tgz
/var/backup/2011-12-02_08.40.25.479813.robert-laptop.ful/files.tgz
/var/backup/2011-12-16_07.49.44.349792.robert-laptop.ful/files.tgz
find: ‘/home/robert/.gvfs’: Permission denied
/root/.local/share/Trash/files/2011-10-24_12.47.00.381486.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-10-14_10.39.41.751755.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-10-28_08.02.06.398063.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-09-30_08.51.08.689699.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-08-10_09.52.23.669183.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-09-16_08.33.01.099117.robert-laptop.ful/files.tgz

I used "sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort" to find trash files thus....

/root/.local/share/Trash/files/2011-08-10_09.52.23.669183.robert-laptop.ful 
120K	/root/.local/share/Trash/files/2011-10-21_17.41.57.213175.robert-laptop.inc 
12G	/root/.local/share/Trash 
12G	/root/.local/share/Trash/files 
1.3G	/root/.local/share/Trash/files/2011-09-16_08.33.01.099117.robert-laptop.ful 
1.3G	/root/.local/share/Trash/files/2011-10-14_10.39.41.751755.robert-laptop.ful 
1.4G	/root/.local/share/Trash/files/2011-10-28_08.02.06.398063.robert

I don't really know how to interpret the data but is seems I had large amounts of backup and trash... I've had very confusing reactions to my attempts to delete these files... I followed the instructions on forestpiskies links but was sometimes refused access as the terminal asked for my password and sometimes wouldn't accept it... I never seemed to get anywhere near deleting the stuff but when I booted up this morning my file space usage was down to 27%.... I guess that using the terminal doesn't give the same confirmations of success that you tend to get with a graphic interface....

The reading for "sudo find / -name "*" -size +1G" is now...

find: ‘/proc/1756/task/1756/fd/5’: No such file or directory
find: ‘/proc/1756/task/1756/fdinfo/5’: No such file or directory
find: ‘/proc/1756/fd/5’: No such file or directory
find: ‘/proc/1756/fdinfo/5’: No such file or directory
/var/backup/2012-01-13_08.04.08.220318.robert-laptop.ful/files.tgz
/var/backup/2012-01-06_09.14.18.019212.robert-laptop.ful/files.tgz
/var/backup/2012-01-20_08.45.22.309462.robert-laptop.ful/files.tgz
find: ‘/home/robert/.gvfs’: Permission denied
/root/.local/share/Trash/files/2011-10-24_12.47.00.381486.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-10-14_10.39.41.751755.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-10-28_08.02.06.398063.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-09-30_08.51.08.689699.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-08-10_09.52.23.669183.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-09-16_08.33.01.099117.robert-laptop.ful/files.tgz
robert@robert-laptop:~$ 

So I've clearly got rid of some backup files but when i use gksudo nautilus to open root (to delete trash) there is an empty desktop icon inside and nothing else....

Still confused but moving in the right direction!... any more suggestions / understandings gratefully received...

---

### Post by sudodus on 2012-01-20
I think you have some backup utility running, that trashes old backup versions but does not delete them. Keep an eye on that for a while, and I think you will fix the problem!

---

### Post by Sigma1 on 2012-01-20
Try gksudo nautilus /root/.local/share/Trash/
This will open a nautilus file window, in a root session, right where you want to be: in the root trash folder. There, you should be able to delete things permanently and free up disk space.
You can probably configure your backup utility to make the backup somewhere other than in /var, too, to make things easier in the future.

---

### Post by drs305 on 2012-01-20
> **coalhole said:**
> .... I guess that using the terminal doesn't give the same confirmations of success that you tend to get with a graphic interface....

That is correct. It's a bit counterintuitive. In Linux, if a terminal command of this nature works it often provides no feedback. If an error occurs, a message is generated. Sort of "I've done what you asked, I'll let you know if I can't" philosophy...

> 
The reading for "sudo find / -name "*" -size +1G" is now...

/var/backup/2012-01-13_08.04.08.220318.robert-laptop.ful/files.tgz
/var/backup/2012-01-06_09.14.18.019212.robert-laptop.ful/files.tgz
/var/backup/2012-01-20_08.45.22.309462.robert-laptop.ful/files.tgz
find: &#8216;/home/robert/.gvfs&#8217;: Permission denied
/root/.local/share/Trash/files/2011-10-24_12.47.00.381486.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-10-14_10.39.41.751755.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-10-28_08.02.06.398063.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-09-30_08.51.08.689699.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-08-10_09.52.23.669183.robert-laptop.ful/files.tgz
/root/.local/share/Trash/files/2011-09-16_08.33.01.099117.robert-laptop.ful/files.tgz
robert@robert-laptop:~$ 

So I've clearly got rid of some backup files but when i use gksudo nautilus to open root (to delete trash) there is an empty desktop icon inside and nothing else....


As *sudodus* states, you are still getting large backups placed in your /var/backup folder. Since the command you used only will identify files that are larger than 1GB, it indicates an abnormal situation. Linux normally will not generate files that large. 

If you aren't aware of setting up a backup program, it might be 'deja-dup', a backup app now a default in Ubuntu. Since it is storing files as root, open the package as root and see if it is active and storing backups in /var/backup (click the 'Storage' option):
```
gksu deja-dup-preferences
```

To delete root's trash, you can open nautilus as root. Use SHIFT-DEL to remove the files in the Trash bin (using DEL only will not remove the files):
```
gksu nautilus /root/.local/share/Trash/files
```
Note: *Sigma1* said the same thing as I was composing this response.

---

### Post by coalhole on 2012-01-20
My used file space is now down to 18%... I've set up manual backups and I'm becoming more familiar with some of Ubuntu's behaviour... "gksudo deja-dup-preferences" doesn't appear to do anything.... But.... Enough to be going on with... Thanks to all... coalhole:)

---

