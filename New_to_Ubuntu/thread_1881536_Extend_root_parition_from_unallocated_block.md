---
title: "Extend root parition from unallocated block"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by greendragons on 2011-11-15
I shrunk one of my ntfs partition in windows... and it is now 10gb unallocated... 
i want to add this to my root partition.... 
How to find where is that unallocated partition is in /dev and also how to add tht unallocated space to root partition,,,
Thxn!!

---

### Post by drs305 on 2011-11-15
An easy way would be to boot the Ubuntu LiveCD you used to originally install Ubuntu. Then open Gparted to see a graphic depiction of your drive(s).

The advantage is that you can then perform partition operations on your Ubuntu partition from Gparted. Since the Ubuntu partition must be unmounted, using the LiveCD or a 'rescue' type CD is normally required. 

Here is a link on changing the size of /. Make sure you backup important data before accomplishing any partitioning operations.

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by greendragons on 2011-11-15
Yes ur right it should be unmounted first... 
lemme try that... if i try 2 extend root..won't it affect my documents stored in there..?

---

### Post by drs305 on 2011-11-15
> **greendragons said:**
> Yes ur right it should be unmounted first... 
lemme try that... if i try 2 extend root..won't it affect my documents stored in there..?

Expanding a partition generally does not corrupt files, as the files aren't normally moved. 

The problem usually occurs when a partition is made smaller, since files may have to be relocated on the disk. The time during which the files are in transit from one part of the disk to another is when they are vulnerable. And of course the copying itself could go wrong or the resulting partition table could also have errors which could, at least temporarily, prevent reading the files.

---

### Post by greendragons on 2011-11-15
thnx!!
can u give me link on creating back up properly... as i know that it is done using tar...
also i want to create back up of my home dir and want list of installed packages to be stored as txt file..
so in case something goes wrong then i can recover my home dir and can installed perviously installed packages from that txt file... so how to get list of installed packages using command....?

---

### Post by drs305 on 2011-11-15
Synaptic has a nice feature for creating a list of installed packages. Open Synaptic then File > Save Markings As > and then designate a location and name. Make sure to 'tick' the "Save full state" option in the lower left panel. You would use "File > Read Markings" on the new system.

Obviously you want to save the file on a partition which won't be involved in your resizing operations. I'd put it on a thumb or external drive (or even upload it) if possible.

If you don't store data files in your /home folder, you could easily just copy the entire /home/yoursuername folder elsewhere to use in case there are problems.

As far as full backups, there are a lot of apps out there: rsync is one of the popular ones. I use a simple terminal app called fsarchiver but there are probably much better solutions for most users. The newer versions of Ubuntu also have 'deja-dup' as a default backup application but I haven't used it much. You'll probably have to do a search or wait for others to help you out on selecting a backup method.

---

### Post by greendragons on 2011-11-15
> **drs305 said:**
> 

As far as full backups, there are a lot of apps out there: rsync is one of the popular ones. I use a simple terminal app called fsarchiver but there are probably much better solutions for most users. The newer versions of Ubuntu also have 'deja-dup' as a default backup application but I haven't used it much. You'll probably have to do a search or wait for others to help you out on selecting a backup method.

I'll search more on back up and then i'll resize the / parition....
Thnx!!! :) :)

---

