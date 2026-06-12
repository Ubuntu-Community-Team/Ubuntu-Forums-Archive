---
title: "How do I change the installation folder for programs?"
date: 2015-07-31
forum: New to Ubuntu
---

### Post by Konstamokh on 2015-07-31
My problem is simple, but annoying: I have a pretty small SSD, where I installed Ubuntu (and Windows 8.1, but that's not important now) and a bigger HDD, where I got all my programs and other data (videos, music, pictures).
On Windows choosing the installation folder was easy: During the installation I would get an option to install to D:. How do I do this on Ubuntu?

---

### Post by TheFu on 2015-07-31
Nobody uses *Drive Letters* except Microsoft.

"**Choose something else**" during the disk setup part of the installation is what you need. Then you can do **anything** you want with the installation location(s), as complicated or as simple as you like.  You just need to understand partitioning and how the partition names map to the partitions you want on the different disks.  Before you start, please make a know-you-can-restore backup of everything on the drives connected to the system.  Partitioning is always a little dangerous and Windows is pretty picky about changes that happen underneath it, so be certain you have a rescue disk for Windows too.

Because of the flexibility built-into Linux, there are thousands (millions?) of different ways to setup the partitions for any system. With all that flexibility comes some added complexity.  You may want to get some partitioning advice from experts about your specific situation. Ask if you'd like that.

So - what does all this really mean?  Programs are installed under /usr most of the time, but really don't take much storage.  It is the data that eats all the storage and that will almost always go into your $HOME.  What this means is that most people will make their HOME partition have more storage than the other places to store more things.  20-30G is all 95% of users will need for /usr and that is if they go crazy and load thousands of huge, bloated, GUI programs.  I go out of my way to limit the storage used in different locations by placing media files outside any of the normal places.
For example, my traveling netbook is partitioned thusly:
```
$ df -h
Filesystem                      Size  Used Avail Use% Mounted on
/dev/mapper/c720--vg-root        51G   31G   19G  63% /
/dev/mapper/c720--vg-lv--Stuff   50G   35G   12G  75% /Stuff
/dev/sda1                       236M   77M  148M  35% /boot
istar:/D                        3.5T  3.3T   32G 100% /D
```

I'm running LVM, hence the "mapper" stuff, but it is really just a way to have virtual partitions that can be on 1 or many physical drives.
/ is using 19G and that is all programs, my documents and code.  On travel, I like to have some media to avoid hotel TV. That's what /Stuff is for.  At home, **the network IS the computer** - the last mount on /D is NFS - to another machine with a 4T disk holding lots of other media - mostly recorded TV shows from the HTPC. Accessing NFS files is just like accessing local storage. Same permissions, same performance. It is hard to explain if you've never seen it in action before.  Inside corporations, it is common to have /home on NFS and mount that storage to hundreds (or thousands) of workstations. It is sorta like "roaming profiles" under Windows AD, but without the long startup times.

Flexibility.  Suppose you didn't plan for all the storage needed under /usr during installation - are you stuck?  Heck no!   If the file(s) appears in the correct location, that is all that Unix needs. 
You can mount added storage to /usr/share and move all the files from the old storage to the new storage. 
OR if you run LVM, you can add the new storage into the VG for the old storage and increase the size of the LV used by /usr.
OR you could leave the new storage where it is and just use a symlink from the old storage to redirect the requests to new storage.  This is sorta a hack, but it does work.  It is a quick and dirty solution until you can fix the storage later. Sometimes later never happens. I've run for multiple years with added storage redirected using symlinks before.  With LVM these days, I don't do that much.

Another example - a blog server. I messed up at installation time and didn't account for all the storage needed under /var. Needed to add some more - that's what vda2 is - more storage just for /var/www.
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       7.1G  3.5G  3.3G  52% /
/dev/vda2       2.3G  814M  1.4G  38% /var/www
```
You can mount storage anywhere you need it. Hopefully this all makes sense?  I needed more storage for web stuff, not for anything else that gets stored in /var, so I only added it directly where needed, /var/www. 

Of course what Windows will do to pre-existing Linux installations is almost criminal. I've seen it wipe completely a Linux install because it didn't know what a partition was. Perhaps that has changed? I dunno.  I do know that about 2 times a year on my last dual boot system a Windows update will trash grub and prevent the system from booting. 

I find it easier to use virtualization than to dual boot these days. For my needs, Windows runs good enough inside a KVM VM.

---

### Post by Dennis N on 2015-07-31
> _How do I change the installation folder for programs_?
With .deb files, the location is controlled by information in the .deb file. There are a few standard locations that are always used. For example, the /usr/bin directory. You don't change these. With a ready-to-run binary (like some games, for example) you have some flexibility where that program files go. Could be in some subfolder of your home folder, but many people use the /opt folder for these types of installations. 

Programs from the Software Center or Ubuntu Repositories come as .deb files.

---

### Post by jason_gibson2 on 2015-07-31
It should be noted that things take up significantly less space with Linux and shared libraries than you are used to with Windows. My Kubuntu root partition is only 15 gigs, and with all of my native apps from the package manager I'm only using 7.3 gigs of my root. A similar Windows install with the equivalent apps takes up close to 40 gigs. It is much less of an issue than one would expect.

Just for reference... Samsung 840 EVO 120gb

```
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   487M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0   1.9G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0  14.3G  0 part /
&#9492;&#9472;sda4   8:4    0  95.1G  0 part /data

```

---

