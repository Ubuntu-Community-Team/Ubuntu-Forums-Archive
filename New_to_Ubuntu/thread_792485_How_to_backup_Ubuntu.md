---
title: "How to backup Ubuntu?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by drbk563 on 2008-05-13
What can I use to backup Ubuntu? I want to backup my entire OS incase something goes wrong.

---

### Post by tamoneya on 2008-05-13
you should use partimage```
sudo apt-get install partimage
```

---

### Post by thedevnull on 2008-05-13
Hey,

You can also check out G4L or Clonezilla.  

[http://www.clonezilla.org/]("http://www.clonezilla.org/")

[http://sourceforge.net/projects/g4l]("http://sourceforge.net/projects/g4l")

Personally I find it just as easy to rebuild from scratch.  Your personal data is much more important so make sure you are backing that up on a scheduled basis.  =)  Check out the program Keep. 

:rolleyes:

---

### Post by ironwolfe on 2008-05-13
In linux you can just copy all the files in your / directory to another drive.  Coming from Windows, I could hardly believe this... but it's true ;)

I use the following command to backup nearly my entire filesystem

```
sudo rsync -avzr --delete --progress --stats --exclude "/sys" --exclude "/media" --exclude "/proc" / /media/Backup500/gutsybackup
```

It looks scary but here is the explanation:

rsync is the copy/sync program run from the terminal command line

-avzr are the flags that tell rsync what to do - a = archive (which keeps all the permissions and important geeky stuff intact) v= verbose (tells you what the program is doing), z = zip (compresses the files where it can), r=recursive (backs up all the nested folders).

--delete = deletes files in the backup that were also deleted in the "source".  Careful with this one - if you are not sure don't do it, you will just have more outdated files.

--progress = tells me more what it is doing - I like to see stuff happening.

--stats = tells me after it is done how it went - time, bytes, etc..

--exclude = excludes some directories I don't want to backup

/ tells it to start at the root directory (i.e. the entire filesystem).

/media/Backup500/gutsybackup is the directory I want to save the backup.

The nice thing about doing it this way is that you can see the files, and ensure they are all there.  Most other programs just put everything into a big blob...

An even easier way is just to copy all the files using the cp command:

```
sudo cp -dpRxv / /media/backupdrivename/files
```

I have restored from this so I know it works... enjoy.
good luck

---

### Post by drbk563 on 2008-05-13
Thank all for your help.

---

### Post by philinux on 2008-05-13
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

is very good

---

### Post by SlappyPappy on 2008-05-13
I've been cloning my hard drive to larger drives but in the process creating awesome backups. I just have to pop in the drive and away I go.

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

Great thread with a lot of good info.  :)

---

