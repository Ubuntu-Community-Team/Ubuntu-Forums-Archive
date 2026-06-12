---
title: "sony mp3 player that does not mount..."
date: 2008-08-09
forum: New to Ubuntu
---

### Post by cmaranhao on 2008-08-09
.. when i connect it to my PC. meaning that i cannot update my music list! i remember that before updating to this newer Ubuntu version, everytime i plugged my mp3 player, it showed up like a pen or a disc. i have my ubuntu system updated also.

i have gparted installed and my mp3 player shows up in there so its not a problem in the player.

can anyone help me?

---

### Post by ajgreeny on 2008-08-09
Do other USB drives (flash or hard drive) show up and mount as you expect?  What type of mp3 player is it?

---

### Post by aloshbennett on 2008-08-10
If you post the output of lsusb as well, other able members would be able to help you out :)

---

### Post by cmaranhao on 2008-08-11
> **ajgreeny said:**
> Do other USB drives (flash or hard drive) show up and mount as you expect?  What type of mp3 player is it?

yes, i have 3 different pens and all of them mount automatically.. also my psp mounts without any problem.. the only thing that is not mounting properly is my mp3 player. by the way, it is this one:

sony nwz-a818

[http://www.amazon.co.uk/Sony-NWZA818-Video-Walkman-Battery/dp/B000VD2130](http://www.amazon.co.uk/Sony-NWZA818-Video-Walkman-Battery/dp/B000VD2130)

> **aloshbennett said:**
> If you post the output of lsusb as well, other able members would be able to help you out :)

how do i do that? i don't know much about linux. in a matter of fact, i have many difficulty when things like this happen. if i have to go to terminal and search/install i really don't know how to do it.


before i forget it, with some help aof a friend of mine i modified a file inside this folder:

/etc/policykit/policykit.conf

i will wuote who that file is at the moment:

> <?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
<match action="org.freedesktop.hal.storage.mount-removable">

        <return result="yes" />

    </match>
</config>

that didn't work, my mp3 still does not mount so i will need to do an something else... remember that i don't know nothing of terminal so any instructions must be very detailed.. i am extremely appreciated to you guys, thanks for the help

regards

---

### Post by nothingspecial on 2008-08-11
> **cmaranhao said:**
> 
[http://www.amazon.co.uk/Sony-NWZA818-Video-Walkman-Battery/dp/B000VD2130](http://www.amazon.co.uk/Sony-NWZA818-Video-Walkman-Battery/dp/B000VD2130)



how do i do that? 

To post the output of lsusb, open a terminal

(click on applications, then terminal)

Then type 
```
lsusb
```and hit enter

A load of gobbldygook will appear. Copy and paste it into a new reply here.

---

### Post by cmaranhao on 2008-08-11
here it is:

> Bus 002 Device 004: ID 054c:0325 Sony Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 2525:8913  
Bus 001 Device 002: ID 03f0:b002 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000 

what should i do now?

---

### Post by cosine352 on 2008-08-11
try this
> gnome-open /media/disk/

---

### Post by cmaranhao on 2008-08-11
it didn't work

> maranhao@maranhao-desktop:~$ gnome-open /media/disk/ 
Error showing url: The location or file could not be found.
maranhao@maranhao-desktop:~$ 


---

### Post by cosine352 on 2008-08-11
change the mount point (in my example "media/disk/")
you said you can see it in Gparted. open gparted and there you can find the "mount point"

---

### Post by dacorr on 2008-08-11
in the terminal type

sudo fdisk -l

this will list the partitions that are visible

once you have the /dev/### depending which is the mp3 player try

mount /dev/###

you may need to do the following if it errors about the mountpoint

mkdir /home/username/Desktop/SonyMp3

then

mount /dev/### /home/username/Desktop/SonyMp3

Dac

---

### Post by cmaranhao on 2008-08-11
> **dacorr said:**
> in the terminal type

sudo fdisk -l

this will list the partitions that are visible

once you have the /dev/### depending which is the mp3 player try

mount /dev/###

you may need to do the following if it errors about the mountpoint

mkdir /home/username/Desktop/SonyMp3

then

mount /dev/### /home/username/Desktop/SonyMp3

Dac

that worked!! it gave an error but i created the directory and it worked fine! thanks for that tip.

i have two more questions though..

1) do i have to do that proceeding each time i want to connect the mp3 player?

2) i don't have permissions to write in the player meaning i can't copy any music over there. what should i do now?

---

### Post by cmaranhao on 2008-08-12
bump

---

### Post by cmaranhao on 2008-08-12
bump

---

### Post by cmaranhao on 2008-08-12
bump

---

### Post by cosine352 on 2008-08-13
try
> sudo mount /dev/### /home/username/Desktop/SonyMp3

---

### Post by cmaranhao on 2008-08-13
> **cosine352 said:**
> try

i already mounted the player, but now the problem is that i don't have permissions to write files into it.

---

### Post by cosine352 on 2008-08-13
did you mount it as root? (note the "sudo" in the command)

---

### Post by cmaranhao on 2008-08-14
yes, i made it using the sudo command

---

### Post by cmaranhao on 2008-08-15
bump

---

### Post by tech0007 on 2008-08-15
> **cmaranhao said:**
> that worked!! it gave an error but i created the directory and it worked fine! thanks for that tip.

i have two more questions though..

1) do i have to do that proceeding each time i want to connect the mp3 player?

2) i don't have permissions to write in the player meaning i can't copy any music over there. what should i do now?

You need to add an entry in /etc/fstab. Back it up first:

```

sudo mv /etc/fstab /etc/fstab.bak

```

Then edit the file:
```

gksu gedit /etc/fstab

```

---

### Post by cmaranhao on 2008-08-16
but when i edit the file, what do i write in it?

---

### Post by cmaranhao on 2008-08-16
bump

---

### Post by cmaranhao on 2008-08-17
still with the problem of not having permissions

please help

---

### Post by cmaranhao on 2008-08-18
bump

---

### Post by cmaranhao on 2008-08-19
bump

---

### Post by Vlad27145 on 2008-08-20
I've experienced the same problem you have and solved them as described by the other members, Mounting on the desktop folder. At that point upon not having permission to write I just accessed the folder as root (Using Kubuntu 8.04 you just need to open the folder then click on "OPEN AS ROOT" on the right side of the screen). I don't know if it works the same way under Ubuntu, since it uses GNOME, but if you manage to do it that gave me full priviliges even if it's not the perfect solution.
Anyway, worst drawback for me is that I don't get the dialog that shows me transfer status from HD to NWZ A818. I can live with that, at least I can get my music on it.
Hope this works for you too, I'm no Linux expert so this is the best I can do to help.

---

### Post by cmaranhao on 2008-08-22
it is not working.. i need more help.. i can't even mount the player, it says this:

> root@maranhao-desktop:/home/maranhao# mount /dev/sde /home/maranhao/Deskop/SonyMP3
mount: mount point /home/maranhao/Deskop/SonyMP3 does not exist
root@maranhao-desktop:/home/maranhao# 

why?

---

### Post by cmaranhao on 2008-08-23
bump

---

### Post by cmaranhao on 2008-08-24
bump

---

### Post by cmaranhao on 2008-08-24
bump

---

### Post by nothingspecial on 2008-08-24
I cannot help you anymore than anyone else has already tried so here are my sugestions -

1 Make a new post in the multimedia and video forum - the guys that help there may know more about your player and what has gone wrong.

2 Are you sure you did this command  
```
sudo mount /dev/### /home/username/Desktop/SonyMp3
```
With the sudo.

3 [SIZE="3"]**Very drastic. Only try this if you are desperate as you can really mess things up using nautilus as root** [/SIZE]

I notice you can mount your player but can not add or remove music. If you open your music player using 
```
gksudo nautilus
``` and navigating to your player - can you add music then? That is a similar solution that has been given this thread before -

> **Vlad27145 said:**
> I've experienced the same problem you have and solved them as described by the other members, Mounting on the desktop folder. At that point upon not having permission to write I just accessed the folder as root (Using Kubuntu 8.04 you just need to open the folder then click on "OPEN AS ROOT" on the right side of the screen). I don't know if it works the same way under Ubuntu, since it uses GNOME, but if you manage to do it that gave me full priviliges even if it's not the perfect solution.

4 The most drastic but safer than the last one -
I notice that this problem only occured when you upgraded Ubuntu and everything was working fine before.
> **cmaranhao said:**
> .. when i connect it to my PC. meaning that i cannot update my music list! i remember that before updating to this newer Ubuntu version, everytime i plugged my mp3 player, it showed up like a pen or a disc. i have my ubuntu system updated also.


If I were you I would back up all my important data (music, photos documents etc etc) and do a full install of the Ubuntu version I had before. Like I said drastic, but if it ain`t broke don`t fix it.

I downgraded back to Gutsy myself.

Try the multimedia forum first though.

---

### Post by cmaranhao on 2008-08-26
thanks, i will make a topic over there before i attempt anything..i don't know much of linux and don't want to mess with it on my own

thanks for your advice mate

---

### Post by cmaranhao on 2008-08-26
in the newest Ubuntu version but with gutsy it worked like a charm.

i am doing this thread following another one i made under Absolute beginner talk and was advised to ask for additional help over here..

anyway, the thread i made is here, if you take a look you might have a better view of my problem:

[http://ubuntuforums.org/showthread.php?t=884914](http://ubuntuforums.org/showthread.php?t=884914)


i made the following like dacorr explained to me:

> sudo fdisk -l

this will list the partitions that are visible

once you have the /dev/### depending which is the mp3 player try

mount /dev/###

you may need to do the following if it errors about the mountpoint

mkdir /home/username/Desktop/SonyMp3

then

mount /dev/### /home/username/Desktop/SonyMp3

this solution solved my problem momentarily.. it mounted the player but i had no writing permissions.. the second time i connected the player, it didn't mounted, even if i repeated the commands like dacorr explained to me.

i am desperate, i can't copy any tracks to the player for quite some time now..

can anyone help me over here?

the mp3 in question is this one:
sony nwz-a818

[http://www.amazon.co.uk/Sony-NWZA818.../dp/B000VD2130](http://www.amazon.co.uk/Sony-NWZA818.../dp/B000VD2130)

i don't know how to do anything under linux so be patient with me.

regards

---

### Post by cmaranhao on 2008-08-27
bump

---

### Post by cmaranhao on 2008-08-27
here is the new topic:

[http://ubuntuforums.org/showthread.php?p=5675777#post5675777](http://ubuntuforums.org/showthread.php?p=5675777#post5675777)

---

### Post by cmaranhao on 2008-08-28
bump

---

### Post by cmaranhao on 2008-08-28
bump

---

### Post by cmaranhao on 2008-08-29
can anyone help me?

---

### Post by aysiu on 2008-08-29
Please stop bumping your thread. And please do not make a new thread on the same topic. If you believe your thread is in the wrong subforum, you can click the REPORT button and report that the thread should be moved.

I've deleted your excessive bumps, and you'll get an infraction if you keep it up. Your problems are important to the Ubuntu community, but they are not any more important than other people's problems.

That said, I think people have been giving you a lot of correct instructions that are also vague.

It seems you know how to open a terminal. You can save yourself some pains by copying and pasting commands instead of retyping them.

This is what I want you to do.

**Step 1**
Make sure the only external USB device connected to your computer is your MP3 player. Disconnect any other USB external hard drives or PSPs.

**Step 2**
Reboot your computer and log in.

**Step 3**
Open a terminal and _paste_ (do not retype) these commands: ```
cat /etc/lsb-release
cat /etc/fstab
sudo fdisk -l
df -h
``` and then _paste_ the output back here. Do not summarize it. Do not describe it. Highlight the entire output of those commands and copy and paste them back here.

**Step 4**
Wait for further instructions. Do not bump your thread.

---

### Post by kleo skywalker on 2008-09-22
aysiu, my Sandisk mp3 player got hung one day - I was listening to it and turned it off, after that whenever I turn it on it remains stuck at that song (doesn't play it), none of the buttons work (including the power one - I have to pop out the battery to turn it off), and it doesn't show up when I plug it into the computer. I posted about it [here]("http://ubuntuforums.org/showthread.php?t=850035") but couldn't solve my problem. I came across this thread and ran the commands you suggested. Could you please take a look at the output and help me get my mp3 player back?

```
cat /etc/lsb-release
```
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
```

```
cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2d4fd3af-f4ca-4212-881c-a32e7f8c5d03 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=9ece016d-0cb5-4b18-bf02-d613f7d27506 /home           ext3    relatime        0       2
# /dev/sda3
UUID=7c2c72a0-6722-4e90-8708-97174cbe3075 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

```
sudo fdisk -l
```
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d475

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1223     9823716   83  Linux
/dev/sda2            1224       30268   233303962+  83  Linux
/dev/sda3           30269       30401     1068322+  82  Linux swap / Solaris
```

```
df -h
```
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  3.0G  5.9G  34% /
varrun                248M  100K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   44K  248M   1% /dev
devshm                248M   12K  248M   1% /dev/shm
lrm                   248M   39M  209M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             221G   75G  136G  36% /home
gvfs-fuse-daemon      9.3G  3.0G  5.9G  34% /home/tupush/.gvfs
```

Thanks.

---

### Post by kleo skywalker on 2008-09-28
bump

---

### Post by kleo skywalker on 2008-10-01
bump

---

### Post by zmoink on 2008-12-21
After following some tips in this thread i solve the problem with whe following commands :

First - Verify that your Sony NWZ player is connected, and is displayed in the system, with : 

> 
lsusb


It should return something like : 
> 
zmk@laptop:~$ lsusb
Bus 004 Device 005: **ID 054c:0325 Sony Corp. **


This is good!! It means that your player is recognized under the linux kernel, and under the USB port .

So, let's move on ... 
After this, let's see if the partition of the NWZ player, is listed. To do so, type : 
> 
fdisk -l


And it should return something like : 
> 
Disk /dev/sdd: 1841 MB, 1841299456 bytes
1 heads, 62 sectors/track, 14501 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdd1**               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.
Note: sector size is 2048 (not 512)

Disk /dev/sdd1: 2199.0 GB, 2199023253504 bytes
1 heads, 62 sectors/track, 17318416 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdd1p1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.


Note: this is only a sample of the result ... results MAY change a little, according to the size of the partition of mp3 player (2Gb/4Gb/8GB ... etc)
Note 2: I pasted here, only the output that refers to the NWZ player.


After this, it seems that our player is Recognized, the partition is OK, so the only things that we need to do is ... to MOUNT the partition .. 

To do so, first, let's create a folder where to mount ..
Doing the following :
> 
sudo mkdir /media/Sony


After this let's give permissions to the folder, so that every user (you inclusive ... ) can write in it .
This means that you can upload, and update the content of your player, in a glimpse ... :) 

> 
sudo chmod -R 777 /media/Sony/


At last, but not the least .. let's mount the NWZ :

> 
sudo mount /dev/sdd1 /media/Sony/


Et Voilá ... it's mounted and ready to read/write in your awesome Sony NWZ Player, check your desktop for the icon ;)  .

Hope it help!! ;)


PS: I followed this hints, to mount my own NWZ-A815 player.

---

### Post by 3rdalbum on 2008-12-22
If you're still running Hardy, then my program Blacklight (look it up on Launchpad) should do the mounting step for you when you open it, and then unmount when you close it. You need the CLI and the GUI package.

I've only tested this on my main computer which now runs Intrepid and mounts the drive perfectly; so if you could test it out for me I'd much appreciate it.

---

### Post by Uschiekid on 2011-08-05
I'm trying to mount my Sony NetMD MZ-N920, so I tried following Zmoink's advice as quoted below.      

The first step of lsusb in terminal comes up with similar results, but the next step of fdisk -l (which for me only works at all if i type sudo first) doesn't have the MD displayed at all, just all others (windows partitions, ubuntu partitions, extra external hdd).  So since his/her conclusion after that step working is "partition is ok", I assume the problem is with partitions?? anyway, I think I understand the steps to mount it, IF i knew where it was located.     

Anyone got an idea why it shows up under lsusb, but not under fdisk -l? 


Note: I just realised this may not be the proper thread to reply to since I realised this is for mp3 players not NetMd players, but I think the same question may still apply, so as of yet, I'm leaving it in this thread.  Most information on MiniDisc players are so old since no one has them anymore, but hopefully some one will have general information that works??  It seems MD players should work with QHiMDTransfer, but since I can't get it to mount... 

PS I'm using Ubuntu 10.04LTS.       


> **zmoink said:**
> After following some tips in this thread i solve the problem with whe following commands :

First - Verify that your Sony NWZ player is connected, and is displayed in the system, with : 



It should return something like : 


This is good!! It means that your player is recognized under the linux kernel, and under the USB port .

So, let's move on ... 
After this, let's see if the partition of the NWZ player, is listed. To do so, type : 


And it should return something like : 

Note: this is only a sample of the result ... results MAY change a little, according to the size of the partition of mp3 player (2Gb/4Gb/8GB ... etc)
Note 2: I pasted here, only the output that refers to the NWZ player.


After this, it seems that our player is Recognized, the partition is OK, so the only things that we need to do is ... to MOUNT the partition .. 

To do so, first, let's create a folder where to mount ..
Doing the following :


After this let's give permissions to the folder, so that every user (you inclusive ... ) can write in it .
This means that you can upload, and update the content of your player, in a glimpse ... :) 



At last, but not the least .. let's mount the NWZ :



Et Voilá ... it's mounted and ready to read/write in your awesome Sony NWZ Player, check your desktop for the icon ;)  .

Hope it help!! ;)


PS: I followed this hints, to mount my own NWZ-A815 player.

---

### Post by Uschiekid on 2011-08-06
I've now posted in a MiniDisc thread where someone has a similar issue, so if some one sees my question and has a solution, they can post it here:
[http://ubuntuforums.org/showthread.php?p=11124363#post11124363](http://ubuntuforums.org/showthread.php?p=11124363#post11124363)
so others can be helped as well.

---

