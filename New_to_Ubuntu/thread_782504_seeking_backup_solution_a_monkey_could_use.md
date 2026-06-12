---
title: "seeking backup solution a monkey could use"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by srossnz on 2008-05-05
I am looking for a very simple backup utility that runs in a gui and is EASY to configure and use.  I would like to with 1-click dump my entire system to an external disk.  In the event of a failure there should be an easy way for me to restore and be back up and running.  Thanks for any advice!

---

### Post by sdennie on 2008-05-05
You could try Simple Backup.  To install it, type the following in a terminal:

```

sudo apt-get install sbackup

```

After that you can start if from System->Administration->Simple Backup Config

---

### Post by agim on 2008-05-05
I hear pybackpack is good too, thought I haven't had a chance to try it.

Edit: upon trying out sbackup just now, it is amazing. It might become my backup system of choice. A lot of fine-grained control.

---

### Post by srossnz on 2008-05-05
> **vor said:**
> You could try Simple Backup.  To install it, type the following in a terminal:

```

sudo apt-get install sbackup

```

After that you can start if from System->Administration->Simple Backup Config

OMG that is beyond awesome and exactly what I needed, thanks!!

---

### Post by eivind on 2008-05-13
It has a very useful GUI and options, but unfortunately, it can ruin your backups without telling you:

[https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719](https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719)

That happened to me when I backed up to an external, VFAT-formatted disk. It may of course not happen to you, but be aware of the risk. I personally would encourage people to use other backup solutions.

---

### Post by srossnz on 2008-05-13
> **eivind said:**
> It has a very useful GUI and options, but unfortunately, it can ruin your backups without telling you:

[https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719](https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719)

That happened to me when I backed up to an external, VFAT-formatted disk. It may of course not happen to you, but be aware of the risk. I personally would encourage people to use other backup solutions.

What do you use now?

---

### Post by srossnz on 2008-05-13
I have been running the sbackups to a secondary disk on my system.  The partition taht it copies to is ntfs so not sure if that is an issue.  I may fireup vmware, install ubuntu and see if it restores ok..

---

### Post by mapes12 on 2008-05-13
There's some good advice about backups here:

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by brettg on 2008-05-13
Hmmmmmmm . . . .

I just made a script;

    #!/bin/bash
    rsync -a sourceDir --delete destinationDir

then linked to it in /etc/rc0.d and it runs every time I shut down.

Result: my files drive (200Gb) automatically backs up to another drive every night but only changed files are written.

Takes about 10 minutes on average

---

### Post by srossnz on 2008-05-13
this is starting to get into the 'over my head' realm.. anything with a gui?

---

### Post by philinux on 2008-05-13
This seems the best to me.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by brettg on 2008-05-13
Well, the thing is, once you've got put in the effort and got the script working then it is quite literally set and forget. GUI solutions tend to lend themselves to human error. ie I was too busy last week, I clicked the wrong thing and didn't realise etc etc.

With a script, once it is working then the human error factor is almost irrelevant

---

### Post by srossnz on 2008-05-13
> **philinux said:**
> This seems the best to me.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

seems pretty cool.  I insttalled it, it then said it made an iso, checked the directory it mentioned but i see no iso file, bunch of folder and files, hmm..

---

### Post by srossnz on 2008-05-13
ah i see, i ran out of diskspace.  I have eve online installed so my livecd build iso would have been 6.1gb any idea what i need to do to exclude files?  in the gui i got to an exclude files dialog, i guess i just put in the path to my eve folder?

---

### Post by eivind on 2008-05-19
> **srossnz said:**
> What do you use now?

Nothing at the moment ;) I just hope my computer lasts until I find the ultimate backup tool [-o< 

That was partly a joke. I haven't had anything to backup since slbackup messed up my last backup, but I think I'd use rsync if I wanted to back up now. The downside to that is that you have to use the exact right command, or it will include all your .cache and other useless data, and I haven't quite found out what the correct incantation is yet :-)

So I'm still searching for a good backup tool to use once I have anything which needs backing up.

---

