---
title: "Partition &amp; Resizing... Help? Please!"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by clearviewsavings on 2013-06-17
HI,
  I am fairly new to the UBUNTU community. I installed UBUNTU a while back and only reserved about 25GB? of my 250GB hard drive and the rest for Windows Vista (I believe WINDOWS is using the rest, but I am not positive...). I am now running out of memory - It took me a while to use up all the memory but I Have to keep deleting files because the OUT OF MEMORY icon keeps popping up ... I don't know if it's possible to Resize my PARTITION and add memory to the UBUNTU partition.... I have many files that I don't want to lose and would like to add to my partition.. I don't even know where to start with this...  ( I ALSO noticed I have multiple versions of UBUNTU installed on my PC, It looks like I Have 8 different partitions)... 
 I am hoping someone can please help me!! 
I recently upgraded to Ubuntu 12.10 and I have 4GB memory.  

I typed in this command: [COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l[/FONT][/COLOR]
----------------
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbfbf78e5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   259219571   128072762    7  HPFS/NTFS/exFAT
/dev/sda3       476026880   488396799     6184960   17  Hidden HPFS/NTFS
/dev/sda4       259224840   476022014   108398587+   5  Extended
/dev/sda5       307002213   469049804    81023796   83  Linux
/dev/sda6       469049868   476022014     3486073+  82  Linux swap / Solaris
/dev/sda7       259224966   304929764    22852399+  83  Linux
/dev/sda8       304929828   307002149     1036161   82  Linux swap / Solaris

-----------------
Partition table entries are not in disk order
jill@jill-laptop:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda7       22493164 18329016   3021532  86% /
udev             1797196        4   1797192   1% /dev
tmpfs             722864     1032    721832   1% /run
none                5120        0      5120   0% /run/lock
none             1807160      668   1806492   1% /run/shm

---

### Post by carl4926 on 2013-06-17
Memory? You mean disk space...?

Post a screen of your partitions as seen in Gparted. It's easier for us to make recommendations from that

---

### Post by MidnightGrey on 2013-06-17
It looks like you have two installs of Linux, sda5 and **sda7**, sda7 being the linux you are currently running.
Can you mount sda5 by any chance? Is there anything in there other than a default linux install in there. If not you can go ahead and reformat it and free up some space.

How are you using your partitions may I ask? Are you aware that Linux can access the <larger> windows partition and place files in these partitions? Only system-essential programs are required to be in the root partition such as libraries and drivers. Nearly everything else can be placed in seperate partitions.

---

### Post by clearviewsavings on 2013-06-17
I believe I do have access to the other Linux version that I am not using - when my system boots it will show both linux (ubuntu) versions and my windows vista... I must have installed it by accident and I don't need it OR the files in it.. I would like to remove this partition, but I am afraid I am going to screw something up, as I don't want to lose this linux version or my copy of windows. 


Please see the gparted shot below, I hope this helps..

---

### Post by clearviewsavings on 2013-06-17
should I just go ahead and DELETED sda5? It states I only have 21GB in sda7 (the linux verison I am currently using and need more HD space in)

I actually just download GPARTED (after a screen shot was requested)- I have never used this program, but it does look easy enouph to use....

---

### Post by MidnightGrey on 2013-06-17
If you are absolutely sure you do not need anything in the *other* linux partition, you can format it and the swap parititon, this will give you an extra 80 Gb of free space. 
However you should probably look up instructions on formatting via gparted, or wait for further input from someone in the forums if you are concerned about losing your WinOS/Linx partitions =)

---

### Post by clearviewsavings on 2013-06-17
I replied to your post, but it's below the others... I also incuded a screenshot of GPARTED so you can get a better idea of what I am using.. 

I didn't answer your question about how I am using my partitions... What do you mean by that?.. I am using a copy of windows vista and ubuntu 12.10 on seperate partitions and that's all.. Id like to keep the 2.... I hope this answers your questions, if it doesn't then im lost..lol ..

---

### Post by MidnightGrey on 2013-06-17
First thing first, type **swapon -s** to figure out which of the two swap partitions you are using (i suspect it is sda8 but lets confirm it)

edit: also gparted should have come pre-installed with ubuntu.?

---

### Post by clearviewsavings on 2013-06-17
OK. Thank you for help.. It also looks like I have 2 unallocated spots that are about 2.5gb a piece.. Can I delete these, or does my HD need these for drivers or..etc.. ? I will have to do some further research (or my luck - I will end up losing everything...)! Thanx again

---

### Post by clearviewsavings on 2013-06-17
NO - I didn't have access to gparted. I had to google it and download the file...

Yes it is sda8...
Filename                Type        Size    Used    Priority
/dev/sda8                               partition    1036156    0    -1

---

### Post by MidnightGrey on 2013-06-17
Those 2 unallocated blocks are 2.5**mb** so it is very little space, as they are in-between partitions it is almost pointless to try and recover them. As they are unallocated they are basically black holes and you cannot access them.

---

### Post by clearviewsavings on 2013-06-17
okay. 

Yes it is sda8...
Filename                Type        Size    Used    Priority
/dev/sda8                               partition    1036156    0    -1

---

### Post by MidnightGrey on 2013-06-17
Okay well you can go ahead and delete the two partitions: **sda5  **and **sda6**. DO *DOUBLE CHECK* everything to make sure you are not deleting the wrong partitions!.

Once both partitions are deleted you will now see you have a very large grey block of unallocated space (about 80Gb). You can do 2 things: 
1) Create a new partition (Right click on the grey block in the graph).
2) Extend your linux partition to fill up the occupied space.

Note: The first options is much simplier than the 2nd option. Additionally if you create a new partition using the filesystem NTFS or FAT32 both your Windows system and your Linux system can see and use the partition. 
I recommend the first option.

---

### Post by clearviewsavings on 2013-06-17
DO i need to Format to , Resize/Move, or  Delete sda5? 

and if i need to  format to, where do I format it to, as it gives a list of options?

---

### Post by MidnightGrey on 2013-06-17
first Right click on sda5 and select **DELETE**. Do the same for sda6.
I havent fixed up my partititons in a while so i dont exactly remember all the context menus, and i cant exactly practise using my computer.

---

### Post by clearviewsavings on 2013-06-17
Yes the first option seems much better... I didn't know that they could both access the HD.. That makes it much easier! 

i will go ahead and re-verify everything first - This is all the help I needed.. I appreciate your help :) ... I will most likey respond if I screw it up.. which it seems easy enouph, as long as I don't delete the partions in use.. lol.. Thnx again

---

### Post by MidnightGrey on 2013-06-17
On a side note: you should familiarise yourself with Ubuntu's Software Centre, it is a much simpler and more robust way of installing common programs, all common programs are listed in one central/searchable location and any programs installed via the software centre will receive automatic updates. 
You will find gparted in there along with firefox/chrome/media players/graphics editors etc...

The Software Centre can be found in your Dash (left panel) and looks like a shopping bag (i can juuust make it out under all your icons in your screenshot).

---

### Post by monkeybrain2012 on 2013-06-17
> **MidnightGrey said:**
> On a side note: you should familiarise yourself with Ubuntu's Software Centre, it is a much simpler and more robust way of installing common programs, all common programs are listed in one central/searchable location and any programs installed via the software centre will receive automatic updates. 
You will find gparted in there along with firefox/chrome/media players/graphics editors etc...

The Software Centre can be found in your Dash (left panel) and looks like a shopping bag (i can juuust make it out under all your icons in your screenshot).

I would suggest synaptic instead. Much faster and gives a lot more information and allows finer control. You can use the USC to install synaptic and then forget about the USC or
```
sudo apt-get install synaptic
```

:)

---

### Post by MidnightGrey on 2013-06-17
i dont think someones whos just come from windows is ready to dive right in to synaptic, but shrug. (Either options is better than googling for a gparted install file from god knows where).

---

### Post by oldfred on 2013-06-17
You will not be able to use gparted from your working Ubuntu. Mounting any partition inside the extended mounts the extended partition. Then you cannot do any editing of partitions inside the extended as you cannot work on mounted partitions.

You can download a gparted liveCD or use the Ubuntu install DVD or flash drive as it has gparted. You will also have to click on swap and right click swap off as liveCD like to use swap to speed things up.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Live repairCD with gparted.

 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by wc711 on 2013-06-17
I just installed 13.04 using Penn Drive.  I'm a newbie and I didn't have my Nvidia graphics drive installed, but I was able to follow the on sreen direction as to sizing the partions and so forth.  I installed Penn Drive first then downloaded 13.04 to a DVD.  I also left the Penn Drive Web site up so i  could reference it from time to time with the Photos of the proceedure.  I was looking through various Linux sites when I came up with the Penn Drive program, so you should be able to find it.

---

