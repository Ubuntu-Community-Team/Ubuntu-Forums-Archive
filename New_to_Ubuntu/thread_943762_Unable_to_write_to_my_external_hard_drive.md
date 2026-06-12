---
title: "Unable to write to my external hard drive"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by nicholas mccarthy on 2008-10-10
Hello,

I'm trying to put files on my external hard drive, but whenever I try, this comes up:

Error while moving to "external hard drive"
You do not have permissions to write to this folder.

Any help here?

---

### Post by MusicMastaMike on 2008-10-10
I'm guessing that the external drive is currently owned by root.  You need to do a ```
sudo chown user:group /path/to/external/drive
```.  Replace user with your username and group with your username as well.  The path will probably be something like /media/disk or wherever it's mounted at.

---

### Post by nicholas mccarthy on 2008-10-10
ok, i need help with this. my user name is stephen, and the name of my external hard drive is called SimpleDrivePS. is that enough info for you to put in those slots in the code you gave me, cos i dont know how to do it

---

### Post by MusicMastaMike on 2008-10-10
Sure, I need you to do one thing for me first.  Open up a terminal (Applications>Accessories>Terminal) and type ```
ls -l /media/
```
Please post the output here and I'll give you the code you need.

---

### Post by nicholas mccarthy on 2008-10-10
total 44
lrwxrwxrwx 1 root    root        6 2008-10-08 12:17 cdrom -> cdrom0
drwxr-xr-x 2 root    root     4096 2008-10-08 12:17 cdrom0
lrwxrwxrwx 1 root    root        7 2008-10-08 12:17 floppy -> floppy0
drwxr-xr-x 2 root    root     4096 2008-10-08 12:17 floppy0
dr-x------ 1 stephen stephen 36864 2008-10-10 15:49 SimpleDrivePS

---

### Post by snova on 2008-10-10
The problem here is pretty simple. Try this:

```
chmod 700 /media/SimpleDrivePS
```

You simply don't have write permissions on this drive.

---

### Post by MusicMastaMike on 2008-10-10
What he said! :-)

---

### Post by nicholas mccarthy on 2008-10-10
I did that, and it said "chmod: changing permissions of `/media/SimpleDrivePS': Read-only file system"
Will it take awhile, or should it have immediate effects, cos I still can't put stuff on the drive.

---

### Post by MusicMastaMike on 2008-10-10
Try ```
sudo chmod 755 /media/SimpleDrivePS
```

And it will take effect immediately if the command executes properly.

---

### Post by nicholas mccarthy on 2008-10-10
Hmm, it may just be something wrong with the drive, cos I did that, it said the same thing in the Terminal, but isn't working still.

---

### Post by lisati on 2008-10-10
Keep up the good work with the troubleshooting!

A couple more possibilities to contemplate:
How is the external drive formatted? If it's NTFS, you might need to install the NTFS-3G driver and/or set it to allow you to write to the external drive. And non-admin user accounts can also be set so they can't write to some devices.

Feel free to ask questions.

---

### Post by nicholas mccarthy on 2008-10-10
I think it's NTFS, but I'm not sure, how do you figure it out?

---

### Post by MusicMastaMike on 2008-10-10
Run this: ```
sudo fdisk -l
``` and post the output.

---

### Post by nicholas mccarthy on 2008-10-10
Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1162     9333733+  83  Linux
/dev/hda2            1163        1216      433755    5  Extended
/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7301    58645251    7  HPFS/NTFS

Disk /dev/sda: 62 MB, 62189568 bytes
16 heads, 32 sectors/track, 237 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         237       60655+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(235, 15, 32) logical=(236, 15, 31)

---

### Post by MusicMastaMike on 2008-10-10
Ok, so it is NTFS.  You can tell under the entry for /dev/sdb1.  Try this: ```
sudo apt-get install ntfs-3g
```.  You will have to restart your computer after (unless it says it's already installed).  If it installs it and you do restart, try running ```
sudo chmod 755 /media/SimpleDrivePS
``` again.

---

### Post by nicholas mccarthy on 2008-10-10
I got this when I put in the first code:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-3g

---

### Post by snova on 2008-10-10
I don't think this is an NTFS problem, although it may become one shortly.

I'm fairly certain that you've somehow mounted the drive as read-only. It's not a permission thing (unless it's both).

If you mounted the disk from a GUI, check the mount settings and make sure "Read Only" isn't checked. If you did it from a terminal... that's odd, since mount doesn't make it read-only by default. Check fstab.

Now, regarding the "Couldn't find package ntfs-3g" error, that's a package manager thing. For whatever reason, apt can't locate where it's supposed to fetch this package from.

Perhaps you need to enable additional repositories. Show us the contents of /etc/apt/sources.list, which contains a list of valid repositories. It may need another entry. That seems strange though, since my machine tells me that ntfs-3g is in Main.

---

### Post by nicholas mccarthy on 2008-10-10
All I did was plug it in and it mounted by itself. Should I unmount it, but leave it plugged in and try to mount it again?

Also, there is nothing in the sourses.list folder, although the folder is named "sources.list.d" for me, is that a problem?

---

### Post by MusicMastaMike on 2008-10-10
```
cat /etc/apt/sources.list
```
sources.list is a file, that will show you what's in it.

---

### Post by Dre8927354 on 2008-10-10
What happens if you type "gksu nautilus" and do it with the gui?

---

### Post by nicholas mccarthy on 2008-10-10
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


(I'm only on version 6.10, I had questions about upgrading in another thread of mine, so if you also want to help with that, go for it.)

---

### Post by newlinux on 2008-10-10
edgy isn'tofficially supported anymore, so I don't think those repos are working and you won't be able to install from the repos - plus ntfs support has come a ways since edgy...

---

### Post by nicholas mccarthy on 2008-10-10
> **newlinux said:**
> edgy isn'tofficially supported anymore, so I don't think those repos are working and you won't be able to install from the repos - plus ntfs support has come a ways since edgy...

Yeah, I figured. I used to have 8.04, then my computer crashed, and I had to use my disk that had 6.10 on it, that's the only disk I got (my friend gave it to me, I'd make a disk with 8.04 on it if I knew how to). So I installed 6.10 on my computer. I did it a few months ago and I was still able to upgrade all the way to 8.04 again, so did it just start happening recently that I can't upgrade anymore?

---

### Post by MusicMastaMike on 2008-10-10
Sounds like we've found the problem... All I can say is that I'd recommend doing a clean install of 8.04 or wait a few weeks for 8.10 to come out.

---

### Post by nicholas mccarthy on 2008-10-10
> **MusicMastaMike said:**
> Sounds like we've found the problem... All I can say is that I'd recommend doing a clean install of 8.04 or wait a few weeks for 8.10 to come out.

Yeah, I've tried to install 8.04 a few days ago, but I didn't know what I was doing.
When 8.10 comes out, will I be able to upgrade or install it even if I am still on 6.10?

---

### Post by MusicMastaMike on 2008-10-10
If the edgy repos aren't working, you'll have to do a fresh install, I believe.

---

### Post by nicholas mccarthy on 2008-10-10
> **MusicMastaMike said:**
> If the edgy repos aren't working, you'll have to do a fresh install, I believe.

Ok, well thanks for your time and help. I installed an .iso of 8.04 last night, I'm gonna try burnning it to a cd then install it from that. The problem is, I don't know what I'm doing. I just hope I'm doing it right, cos I also can't download stuff off of Add/Remove Applications cos of all of this, so I can't listen to music, watch videos, ect., and this is my only computer.

---

### Post by snova on 2008-10-10
If you have a fast internet connection (you said you just downloaded an .iso, so it can't be to bad) you can upgrade your way to 8.04 off the internet.

Here are the contents of my sources.list file. If you replace yours (make a backup first) with this and run the commands I give you, you should be able to upgrade just fine. Be warned that it will take a long time, depending on the speed of your connection and the number of packages you have installed.

Anyway, my sources.list file:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Then run this:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

And wait *very* patiently.

When 8.10 comes out, you'll have to make a few modifications to the file, but they shouldn't be major. In theory you can just replace "hardy" with "intrepid" (unless it's "ibex", not sure) and run those commands again.

Best of luck with updating.

---

### Post by newlinux on 2008-10-10
Don't go straight from 6.10 to 8.04. It won't be pretty. The proper upgrade path from 6.10 is 6.10->7.04->7.10->8.04 (in other words it would be easier to just install the latest release from CD). You can go from LTS to LTS release (6.06->8.04 for instance) but you can't skip releases otherwise.

Edgy expired around June I think. Regular desktop releases are supported for 18 months.

---

### Post by nicholas mccarthy on 2008-10-10
So I don't want to do what the guy above you said to do?

---

### Post by newlinux on 2008-10-10
No you don't.

Also, it is best to upgrade releases of ubuntu desktop  using the update manager if you are not reinstalling.

---

### Post by nicholas mccarthy on 2008-10-10
That's the problem, I can't. 

[http://ubuntuforums.org/showthread.php?t=942147](http://ubuntuforums.org/showthread.php?t=942147)

Apparently something is wrong with my connection, but I don't know what. I would have upgraded in order if it would let me.

---

### Post by newlinux on 2008-10-10
see my post on your other thread.

---

### Post by snova on 2008-10-10
Sorry, I didn't know that.

In theory, you can just use that snippet anyway by replacing "hardy" with different code names and performing the same operation several times. It'll just take longer.

But if your internet connection doesn't work, that changes things...

If downloading CD's isn't an option, disks are cheap off the internet. You can buy the entire repositories on DVD and reinstall from the first one. That's how I did it initially. Package installation is then dependent on the speed of your DVD drive and how quickly you can swap disks in and out.

---

### Post by nicholas mccarthy on 2008-10-10
> **snova said:**
> Sorry, I didn't know that.

In theory, you can just use that snippet anyway by replacing "hardy" with different code names and performing the same operation several times. It'll just take longer.

But if your internet connection doesn't work, that changes things...

If downloading CD's isn't an option, disks are cheap off the internet. You can buy the entire repositories on DVD and reinstall from the first one. That's how I did it initially. Package installation is then dependent on the speed of your DVD drive and how quickly you can swap disks in and out.

I don't know why it's saying my internet connection isn't working, clearly it is. Before my comupter crashed and I was still on 8.04, I could download updates, ect. on it, I don't know why it's not working now.

---

### Post by snova on 2008-10-10
Oh! That *is* strange. If you're online *now* to browse these forums from Ubuntu, I have no idea why APT isn't working.

---

### Post by newlinux on 2008-10-10
It is telling you your network connection *may* be broken because it can't connect to the repos. In fact the repos aren't there to connect to - there is probably nothing wrong with your connection, but when that happens and you are trying to connect to repos that actually are alive network connection is usually the problem.

---

### Post by nicholas mccarthy on 2008-10-10
> **newlinux said:**
> It is telling you your network connection *may* be broken because it can't connect to the repos. In fact the repos aren't there to connect to - there is probably nothing wrong with your connection, but when that happens and you are trying to connect to repos that actually are alive network connection is usually the problem.

Yeah, I just hope that I can get a blank cd soon, burn my 8.04 iso to it, and hopefully get it installed properly.

---

