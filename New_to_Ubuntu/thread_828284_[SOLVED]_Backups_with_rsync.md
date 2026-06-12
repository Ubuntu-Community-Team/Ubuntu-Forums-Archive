---
title: "[SOLVED] Backups with rsync"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Nxion on 2008-06-13
Hi all,

I am a noob when it comes to rsync, so be gentle :)

OK I think I have settled on rsync for backups. I have never used it before so I did some digging and hound this [http://ubuntuforums.org/showthread.php?t=776585&highlight=Backups+rsync](http://ubuntuforums.org/showthread.php?t=776585&highlight=Backups+rsync). That is pretty much what I want to do. I have a few questions thought.

1. Lets say my machine dies tomorrow. And I want to set it up almost exactly how I had it before (ie bar serttings, GUI settings, wireless networks, etc.). WHat directories do I have to add to my rsync script so if my machine dies I can just bring them back with rsync and then my machine wont know the differance?

2. How would I write the command out (ie rsync -au --delete ????????).

Thanks in advance.

---

### Post by neurostu on 2008-06-13
You should definately backup your your /home directory most of your prefs are stored there

---

### Post by ukripper on 2008-06-13
> **Nxion said:**
> Hi all,

I am a noob when it comes to rsync, so be gentle :)

OK I think I have settled on rsync for backups. I have never used it before so I did some digging and hound this [http://ubuntuforums.org/showthread.php?t=776585&highlight=Backups+rsync](http://ubuntuforums.org/showthread.php?t=776585&highlight=Backups+rsync). That is pretty much what I want to do. I have a few questions thought.

1. Lets say my machine dies tomorrow. And I want to set it up almost exactly how I had it before (ie bar serttings, GUI settings, wireless networks, etc.). WHat directories do I have to add to my rsync script so if my machine dies I can just bring them back with rsync and then my machine wont know the differance?

2. How would I write the command out (ie rsync -au --delete ????????).

Thanks in advance.

In your case I would suggest you use full backup first using tar backup  and then only rsync the files which changes on regular basis.

To follow the tar backup tutorial here is the link - [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Nxion on 2008-06-13
> **ukripper said:**
> In your case I would suggest you use full backup first using tar backup  and then only rsync the files which changes on regular basis.

To follow the tar backup tutorial here is the link - [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

How would I write that in the script?

---

### Post by ukripper on 2008-06-13
> **Nxion said:**
> How would I write that in the script?

you will need two different scripts one for tar backup which you will run only once to backup full system and 

then 

you can create script which will sync your regularly changin files such as /home directory.

check this link for rsync - [http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

---

### Post by Nxion on 2008-06-13
> **ukripper said:**
> you will need two different scripts one for tar backup which you will run only once to backup full system and 

then 

you can create script which will sync your regularly changin files such as /home directory.

check this link for rsync - [http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

Thanks for the link. So am I correct that rsync will up date the tar file that is created when I do a full backup?

---

### Post by ukripper on 2008-06-14
> **Nxion said:**
> Thanks for the link. So am I correct that rsync will up date the tar file that is created when I do a full backup?

No tar backup is different to rsync.

This solution only works if you want full backup once using tar and then rsync separately.

But if you just want backup then you can just use tar only which can be croned (using crontab) for automatic backups on regularly  but won't work for incremental backups with tar.

Only use rsync if you want to have only one backup which will keep updating the destination file with the source file. and you can also use grsync gui version of rsync and it is in repos.
```
sudo apt-get install grsync
```

If you looking for easiest GUI way to backup I would suggest you use quickstart which is python app created by one of our member of ubuntu community.
[http://ubuntuforums.org/showthread.php?p=4184952](http://ubuntuforums.org/showthread.php?p=4184952)

---

### Post by silkstone on 2008-06-14
I use the 'tar' method mentioned earlier to backup system files once a week or so. Before doing so, it's a good idea to clear out the Thumbnails folder (.thumbnails/normal/), clear private data and unwanted cookies from Firefox, and also clear the cache of programs such as Bibble.

There should be --exclude=/xxx entries for /media, data folders (documents etc) and also perhaps for the Thunderbird mail folders if these are large.

That takes care of system and program files, and I then use grsync (GUI version) every day for data files including mail folders, documents, photos, etc.

I've found that grsync wants to copy absolutely everything again if the target is a FAT32 drive or partition. If the target is formatted ext3, it copies only the files that have changed, which of course is much better. Perhaps I've been doing something wrong here, but anyway I now have an external USB drive formatted ext3 which I use for backups, and it all seems to work very well.

---

### Post by ukripper on 2008-06-14
> **silkstone said:**
> 
I've found that grsync wants to copy absolutely everything again if the target is a FAT32 drive or partition. If the target is formatted ext3, it copies only the files that have changed, which of course is much better. Perhaps I've been doing something wrong here, but anyway I now have an external USB drive formatted ext3 which I use for backups, and it all seems to work very well.

You can also use --exclude=directory/ in rsync to exclude and if you want --include=directory/ can be used to only include directories you want.

If you are using ssh to backup on another machine this what i use -
```
rsync -e "ssh" -avz --progress --delete --exclude=directory/ <Source directory> <username@remote-machine:Destination directory>
```

---

### Post by mdpalow on 2008-06-14
You could probably save yourself a lot of time and just use QuickStart (see my signature below) to make your TAR back-up and even setup a 'sync' plan.

Good luck

---

### Post by Nxion on 2008-06-17
Thanks you everyone for your suggestions. I will give them all a try and let you know how it works :)

---

### Post by Nxion on 2008-06-17
> **mdpalow said:**
> You could probably save yourself a lot of time and just use QuickStart (see my signature below) to make your TAR back-up and even setup a 'sync' plan.

Good luck

Ill give that one a try too. I looked at it and it looks promising. Thanks.

---

### Post by dje on 2008-06-17
you could take a look at linbaku in my sig

hope that helps,
dje

---

### Post by Nxion on 2008-06-23
> **dje said:**
> you could take a look at linbaku in my sig

hope that helps,
dje


I like yous as well. It worked without any issues.

---

### Post by Nxion on 2008-06-23
> **mdpalow said:**
> You could probably save yourself a lot of time and just use QuickStart (see my signature below) to make your TAR back-up and even setup a 'sync' plan.

Good luck


Yours is very detailed and is amazing. Im going to use this one as well.

---

### Post by Nxion on 2008-06-23
Thanks to everyone who gave suggestions and help me on this!!!

---

### Post by ukripper on 2008-06-23
> **Nxion said:**
> Thanks to everyone who gave suggestions and help me on this!!!

you are always welcome mate!:)enjoy backing up to your likes

---

### Post by Nxion on 2008-09-30
Thanks to everyone on this, I have settled on Quickstart, this seems like the easiest way to do it. But thanks to everyone and there suggestions.

---

### Post by mdpalow on 2008-10-04
> **Nxion said:**
> Thanks to everyone on this, I have settled on Quickstart, this seems like the easiest way to do it. But thanks to everyone and there suggestions.

Yea... I win.  LOL :guitar:

---

