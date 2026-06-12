---
title: "Ubuntu and Mac HD file permissions, HELP :("
date: 2014-07-07
forum: New to Ubuntu
---

### Post by tonie3 on 2014-07-07
I bought my first Macbook Pro in 2010 and I've never had a problem with it until now. The OS won't boot and is stuck on the gray screen (I've tried a few things, but it just won't work). When I had a PC, if it ever got a virus or wouldn't boot, I would just throw in my old Ubuntu CD that I got from my step-dad and had no problems transering all my files over to my external hard drive so I could wipe my computer. I got Ubuntu 14.04 to run on my Macbook (yay!) but now I'm totally stuck because I can't see any of my files. Something about permissions? I've searched online for a solution but they're all VERY confusing, and I don't want to fiddle with the Terminal unless I know exactly what I'm doing lol (I'm actually not even very familiar with using the Terminal). Now uh, I'd take a screenshot of exactly what I'm looking at to help everyone see my problem, but I don't know how to do that on Ubuntu at all lol. If any of you have some very easy beginner's information on how to help me out it'd be greatly appreciated!! Thank you :)

---

### Post by grahammechanical on 2014-07-07
Can you clarify a few things? So, you have installed Ubuntu 14.04 in its own partition and you now want to access the Mac partition to gain access to files so that you can transfer them off the hard disk onto an external hard disk. Is this correct?

When you open file manager does it see the Mac partition? Does it open the Mac partition so you can view the folders and files on it? If you open the Disks utility does it see the Mac partition?

Regards.

---

### Post by coffeecat on 2014-07-08
> **tonie3 said:**
> I got Ubuntu 14.04 to run on my Macbook (yay!) but now I'm totally stuck because I can't see any of my files. Something about permissions?

Definitely about permissions. 

Assuming you've set up a dual-boot with MacOS and Ubuntu on your Macbook and that you are browsing the MacOS partition from Ubuntu, this following is the problem you are experiencing. Both MacOS and Ubuntu use the same set of Unix permissions and ownership. Ownership of files is defined by the UID (User ID) and GID (Group ID). In Ubuntu, the first created user has a UID of 1000 with the default group GID of 1000 also. In MacOS the first created user has a UID of either 500 or 501 (can't remember which). So when you browse your files on the Mac partition, Ubuntu sees them as having a different owner and hence the permission denied error, or whatever, that you see. 

A further complication. The Mac partition will be formatted with the journalled version of the HFS+ filesystem. Ubuntu can mount this read-only, which means that you can't change ownership of files or folders on it. Not that you would want to do that on your Mac partition anyway - that would give you problems when running MacOS, assuming you could repair whatever is preventing it from booting. 

If I've misunderstood you, and you are running Ubuntu from the live CD/USB, the principle is the same but the "ubuntu" user account in the live session has a UID/GID of 999/999, so you get the same permission problem.  

The solution? You need to open a root-owned file browser window and use that to copy files. In Ubuntu, from a terminal:

```
gksu nautilus
```

You may need to install the gksu package before that will work. If you do have to install the gksu package, run this first:

```
gksu-properties
```

And check that authentication mode is set to sudo. Change if necessary.

When your root-owned nautilus window opens, it will do so in the root home folder. Browse up a level to get to the root of the Ubuntu filesystem before navigating to the mounted Mac filesystem. If you've mounted the Mac partition from the file browser, it will be mounted in /media/yourusername/something, so if you get lost with where you are with the root file browser window, try this instead:

```
gksu nautilus /media
```

You'll see a folder with your username and the Mac mountpoint will be a folder inside that.

Last tip: you say you are going to copy your rescued files to an external HD. It is easier if it is formatted with a Microsoft filesystem such as NTFS or FAT32. Microsoft filesystems don't support Unix permissions and ownership, and whatever ownership or permission issue is causing you trouble at the moment will be conveniently lost on the way. If you copy from the MacOS partition to a HD formatted with a Linux filesystem using a root-owned file browser, I'm not sure what ownership the files will end up with, but it will probably be inconvenient and the MS filesystem sidesteps this neatly.

---

