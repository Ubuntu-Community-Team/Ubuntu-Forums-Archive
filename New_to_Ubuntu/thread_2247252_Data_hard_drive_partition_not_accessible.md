---
title: "Data hard drive partition not accessible"
date: 2014-10-06
forum: New to Ubuntu
---

### Post by Enigma12 on 2014-10-06
Obviously, a little knowledge can be a dangerous thing. I added a second SATA hard drive to my Lubuntu 14.04 computer. The first one, a 40G, contains the operating system and all added programs -- nothing else. The second, an 80G, is for all data (photos, videos, music, documents, etc.). This computer has Lubuntu as its only OS, FWIW. 

When I did the installation of Lubuntu, I decided to partition the 80G drive into two partitions: a 45G for the majority of data files, and the remainder for whatever I chose to do with it. Creating the 45G partition went smoothly, but I have 33G in a partition that I cannot access or format or name. See photo. [ATTACH=CONFIG]256998[/ATTACH]

I must have missed that opportunity when I installed Lubuntu. So, how can I now make this 33G partition accessible, format it as Ext4, and give it a name like "Other stuff"? 

If this requires using Terminal, please be specific with instructions. I am not yet all that comfortble or knowledgeable in Terminal usage. If another process is possible, please explain that as well. 

Thanks in advance for any help in this matter.

---

### Post by Dennis N on 2014-10-06
The 33 gB is not in a partition, but is unallocated space (free space). You can make a new partition in this space with a partition editor such as gparted.

---

### Post by Mike_Walsh on 2014-10-06
Agreed. 

You need to use 'GParted', as Dennis says; 'Disks' allows you to re-format, and/or completely wipe a disk or external drive clean. But to create a new partition in that unallocated space, you need to use GParted.....that's exactly the kind of thing it's intended for.

Both apps will format and/or erase partitions, but in MY (admittedly limited) experience, only GParted can create new ones. I think there's others out there, but GParted is so universally recommended, and so very efficient at what it does, that there's no real need to search others out. ;)

Regards,

Mike.

---

### Post by oldfred on 2014-10-07
Some info on how to use gparted. 
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

To use Linux partitions you have to create a mount point (which may or may not be same as label), give yourself ownership & permissions. If an internal drive much better to also permanently mount using fstab.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
Another example 
[http://ubuntuforums.org/showthread.php?t=2227574](http://ubuntuforums.org/showthread.php?t=2227574)

      Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

   [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Also best with Linux not to use spaces in labels or mount points. You have to escape space or add quotes around every use. Easier to use CamelCase, under_score, or justonename.

---

### Post by Enigma12 on 2014-10-09
I downloaded and burned a CD of Gparted, printed bunches of web info on using it, and watched 5 YouTube videos demonstrating how to use it before I actually booted up with the Gparted CD. First and second time, the mouse wouldn't do anything. Had to manually shut down the computer. On the third try, the mouse worked. Don't know why or care. 

Decided to eliminate that unallocated space and add it to the sdb. KISS. That worked, so, other than the swap partition, I have all that drive for data. 

Oldfred, when I get more cozy with Linux, I may also prefer to go the route you suggested, but I'm not yet there today. I'm still in Linux diapers right now. 

Mike and Dennis, thanks for your good advice. I'll mark this thread solved.

---

### Post by Mike_Walsh on 2014-10-10
> **Wayne_Terrebonne said:**
> I downloaded and burned a CD of Gparted, printed bunches of web info on using it, and watched 5 YouTube videos demonstrating how to use it before I actually booted up with the Gparted CD. First and second time, the mouse wouldn't do anything. Had to manually shut down the computer. On the third try, the mouse worked. Don't know why or care. 

Decided to eliminate that unallocated space and add it to the sdb. KISS. That worked, so, other than the swap partition, I have all that drive for data. 

Oldfred, when I get more cozy with Linux, I may also prefer to go the route you suggested, but I'm not yet there today. I'm still in Linux diapers right now. 

Mike and Dennis, thanks for your good advice. I'll mark this thread solved.

Morning.

I WAS wondering why you were running GParted from a Live-CD; and of course, it then hit me... :-k

With a single OS, and with having to unmount partitions to work on them, you would NEED to do it that way. I have 3 or 4 OSs on the go at any one time, and if I want to make modifications to any of them, well.....I re-boot into one of the others, and make the changes from there. I have GParted installed in each OS I run; it's one of the first utilities I put in a new OS as soon as it's up & running.

I knew you could do this from a system Live-CD, but I DIDN'T know that GParted has its own Live-CD; that's something new I've learnt! ;)


Regards,

Mike.

---

