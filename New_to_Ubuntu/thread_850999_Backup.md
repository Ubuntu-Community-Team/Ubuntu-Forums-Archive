---
title: "Backup"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by johnbradbury on 2008-07-06
Hi Guys,
I want to backup my laptop (Ubuntu 8.04) onto my home server. I have a cloned image of the base installation (using acronis 10) but how do I backup everything else for easy restore?

I know I can backup the /home directory which will save all my data and config settings. However I'm not sure if this will restore other settings such as installed packages, cron jobs etc?

I've setup my home server so I can ssh over the backup, I'll also be looking at setting up a cron job to do this for me at some point.

So the theory is, I restore the base build from cloned image then copy back the saved /home directory from my server. Is this enough?

---

### Post by rraj.be on 2008-07-06
you can try partimage.

It will clone only used space of the partition.

you can restore installtion using partimage  with all setings as same as you had during cloning.

to install partimage type this in terminal
```

sudo apt-get install partimage

```
see here for more info

```
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")
```

---

### Post by johnbradbury on 2008-07-06
Thanks. In future I can use Partimage...

However I don't want to use this as my primary backup method. I want to be able to restore a base image from acronis or partimage and then restore my personal files and configs.

If I setup a backup using rsync what folders will I need to backup to restore my user accounts and profiles, the installed packages etc...?

Thanks

---

### Post by silkstone on 2008-07-06
I'm not sure if this will suit you, but it's the way I do it.

I use Grsync to backup data files to an external hard drive. I use this for folders such as ~/Documents, ~/Photos, my mail folders, etc. Note that the external drive needs to be formatted ext2 or ext3 for Grsync to work efficiently - if it's anything else, Grsync will want to copy everything again whether it has changed or not.

That deals with the data files. For everything else, I use a terminal command to create a tar file...

```
sudo su

cd /

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/home/silkstone/Photos --exclude=/home/silkstone/Music --exclude=/home/silkstone/Downloads --exclude=/home/silkstone/Videos --exclude=/home/silkstone/Documents --exclude=/home/silkstone/.bibble/cache --exclude=/home/silkstone/.mozilla-thunderbird/hlhwudic.default/Mail --exclude=/home/silkstone/.thumbnails/large --exclude=/home/silkstone/.thumbnails/normal /
```

That looks a bit heavy, but all I'm doing is telling it to exclude the data files I've backup up with Grsync, and also the system folders that don't need backing up because they are generated on boot-up.

(Note: You need to exclude /media if another drive or partition is mounted there.)

----------------------

To restore Ubuntu, ensure that the file backup.tgz is in the root directory, then....

```
tar xvpfz backup.tgz -C /
```

This will overwrite everything! After that, and before doing anything else, recreate the excluded directories....

```
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
mkdir media
mkdir /home/silkstone/Photos
mkdir /home/silkstone/Music
mkdir /home/silkstone/Downloads
mkdir /home/silkstone/Documents
mkdir /home/silkstone/Videos
mkdir /home/silkstone/.bibble/cache
mkdir /home/silkstone/.thumbnails/large
mkdir /home/silkstone/.thumbnails/normal
mkdir /home/silkstone/.mozilla-thunderbird/hlhwudic.default/Mail
```

---

### Post by rraj.be on 2008-07-06
> **johnbradbury said:**
>  I want to be able to restore a base image from acronis or partimage and then restore my personal files and configs.

Ok.But restoring a clone will automatically restore all your personal settings too.I am not getting what you are expecting.

>  If I setup a backup using rsync what folders will I need to backup to restore my user accounts and profiles, the installed packages etc...?


I am not much known to rsync because i have never used it.

But if you want to make a backup of all your installed pacakages you could create a local repository on a disk.

this could be done using aptoncd.

to install aptoncd type this in terminal

sudo apt-get install aptoncd

this will install aptoncd and you can use that for creating local repo of your system along with all installed pacakages and even with packages in a directory.

You dont need to install packages separately or copy them to any other directories.
you can use synaptic  to install packages from aptoncd.

Really its a handy tool to backup all your packages.

See more tutorials here.

---

