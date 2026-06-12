---
title: "How do I wipe Ubuntu?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by cklf0 on 2008-06-28
Hi. Well, after many many hours of trying to rectify my problems with Ubuntu, I've decided to go back to XP so I can use my computer again. I made the stupid mistake of getting rid of XP when installing Ubuntu (as the trial version worked great!).

Can anyone suggest what I should do from here.

My problem is Ubuntu will not recognise Cd's in my Cd Drive, so I can't perform a reinstall from the CD! I am in a bind. I am currently not connected to the web either because I need to install some software from CD.

I realise this is a sacrilege request on such a forum, but I am too frustrated and need to get my computer up and going again. 

Help has been fantastic so far, just asking for one more bit of advice before I disappear back into Windows world.....

---

### Post by sharks on 2008-06-28
put the ubuntu live cd and go to system--administration---gparted. and format the partition on which u have installed ubuntu or delete the partition

---

### Post by NovaAesa on 2008-06-28
You need to boot from a Windows CD and select install. When it comes to selecting a drive to put Windows on, you need to reformat which ever partition or drive Ubuntu was on. Sorry if this is a bit vague, I haven't had to install Windows in a while.

---

### Post by Methuselah on 2008-06-28
Yeah, windows install disks are usually bootable.
Just put it in and restart and proceed with the installation by deleting the ubuntu partition, reformatting it to ntfs and installing windows.

---

### Post by saidinesh5 on 2008-06-28
well dude, if you ask me, you should not give up on things, atleast before you try them out a bit..even i had such problems but they have soon vanished and my PC is running as smoothly as it can...but who am i to force you to stay rite??

since your statement :"I made the stupid mistake of getting rid of XP when installing Ubuntu", is slightly confusing for me, here i will give you both the options to solve your problem...

if you dont have windows and want to install windows, then you can simply put the windows CD and boot into the windows setup as you did previously and install windows ..and wipe out the ubuntu partitions either during the windows setup or after you get into windows...n your system would be ready with windows

if you already have windows on your PC and simply want to wipe out the ubuntu partition, fix your mbr 1st and then simply wipeout the ubuntu partition:
here is the info:

[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

but i again advice,to check for a solution for your problems first...cuz if the CDROM aint working ,it can b due to a 1000 reasons...so figure them out first..and if it is a hardware problem then im sure you cant install windows either, before you get that problem fixed!!
neways
hope your problems get solved..
all da best

---

### Post by NovaAesa on 2008-06-28
I'm just remembering thath when you buy a computer sometimes (in AU anyway) they don't give you a Windows CD but instead a recovory partition. You should be able to boot from that partition if that is the case. If you deleted that partition when you installed Ubuntu, then you had better get on the phone with whoever sold you the machine.

---

### Post by lisati on 2008-06-28
> **NovaAesa said:**
> I'm just remembering thath when you buy a computer sometimes (in AU anyway) they don't give you a Windows CD but instead a recovory partition. You should be able to boot from that partition if that is the case. If you deleted that partition when you installed Ubuntu, then you had better get on the phone with whoever sold you the machine.
This is true of my desktop. Some computers have a "Recovery disk" instead of a recovery partition (e.g. some Toshiba laptops)

I wish the OP all the best in sorting things out.

---

### Post by hyper_ch on 2008-06-28
well, does yuor cd drive work at all?

for installting ubuntu you did have to create a bootable cd... can you still boot from that cd?

---

### Post by NovaAesa on 2008-06-28
I think s/he mean the drive doesn't work from within Linux.

EDIT: yep, that's what these threads seem to indicate:
[http://ubuntuforums.org/showthread.php?t=842065](http://ubuntuforums.org/showthread.php?t=842065)
[http://ubuntuforums.org/showthread.php?t=836977](http://ubuntuforums.org/showthread.php?t=836977)
[http://ubuntuforums.org/showthread.php?t=837001](http://ubuntuforums.org/showthread.php?t=837001)

---

### Post by geo909 on 2008-06-28
+1 that this is not an ubuntu matter. It's like when you install XP, the fact that something else (ubuntu) is installed doesn't make any difference to the windows installer! The guy does not need to use gparted from a livecd to partition the disk, the XP cd can do that. Even if ubuntu doesn't see your drive (?) that will not make any difference.


 Check if your laptop comes with a recovery partition, as NovaAesa said.
Unfortunately they sell laptops this way in Greece very often. If this is the
case, ignore the rest of the post.

 If not, just put a XP cd in the drive and reboot. Don't mess up with live CDs and partitioners.

If the laptop does not boot from the cd, you should reboot again to bios this time (something 
like pressing del or F2 or something when the machine just boots) and change the boot order.

Ok, when boot from XP's CD, you will see a blue screen and windows cd will guide you through 
the process. A bit later you will need to set up the partitioning of your disk. Using the keys 
that the screen indicates you wipe all the partitions (you will probably have two, linux and 
swap), then create a new partition in the empty space and you install XP there. When asked for 
the format, choose NTFS.

 Post any problems you have.

---

### Post by hyper_ch on 2008-06-28
Nova:

I wonder if the drive still works at all...

---

### Post by bigken on 2008-06-28
use the live cd and run gparted look for a recovery partition if its there make it bootable 
restart the pc and your recovery will start

---

### Post by waspbr on 2008-06-28
that happens a little too often when people just completely switch Operating systems  without any prior knowledge of the new system. Using a new operating system is a process, you shouldn't rush things

You should be able to boot from you windows XP CD format the ubuntu partition and reinstall XP.

Next time if you are going to try out a new operating system try dual booting first

---

### Post by cklf0 on 2008-07-06
Thanks to all have responded. It is much appreciated. Yes, lesson learnt about doing a complete switch, but the trial version worked so well I was pretty confident that the full version would also.

My CD Drive worked initially as I had to use it to install. Worked fine when I was trialling Ubuntu, but has stopped since installing the full version.

Unfortunately, I need the CD working so I can install my USB Wireless Device. As such, I am doing searches etc form home laptop and hopping on to Home Desktop (Ubuntu) to try and make things work.

I can't use the CD at all. I have gone into BIOS, made CD first, second and third choice and still no luck. It doesn't matter if I use the Ubuntu ISO or my Windows XP CD.

Any suggestions from here would be greatly appreciated. Have spent too many hours doing searches, but my home desktop computer is now essentially useless as I can't access the internet/email and can't use my CD.

Thanks again for all your help!

---

### Post by nothingspecial on 2008-07-06
It may be that your cd drive is broken and you need a new one.
If it is Ubuntu that`s messed with it then it should still work before you boot ubuntu.
I have a laptop with a broken cd drive and when I hosed my system (as I often do), I was at a loss untill I found this -

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

If you can get a wired internet connection it will allow you to install another linux distribution so if it is Ubuntu that has broken your cd drive you can see if it works with something else.

This is a pretty drastic measure but it might help you, however I believe you just need a new cd drive.

---

### Post by aktiwers on 2008-07-06
Does the Ubuntu CD boot if you put it in the drive and reboot the PC?
Could also be your Windows CD that is screwed up?

---

### Post by Tikkun olam on 2008-07-06
> **cklf0 said:**
> Thanks to all have responded. It is much appreciated. Yes, lesson learnt about doing a complete switch, but the trial version worked so well I was pretty confident that the full version would also.

My CD Drive worked initially as I had to use it to install. Worked fine when I was trialling Ubuntu, but has stopped since installing the full version.

Unfortunately, I need the CD working so I can install my USB Wireless Device. As such, I am doing searches etc form home laptop and hopping on to Home Desktop (Ubuntu) to try and make things work.

I can't use the CD at all. I have gone into BIOS, made CD first, second and third choice and still no luck. It doesn't matter if I use the Ubuntu ISO or my Windows XP CD.

Any suggestions from here would be greatly appreciated. Have spent too many hours doing searches, but my home desktop computer is now essentially useless as I can't access the internet/email and can't use my CD.

Thanks again for all your help!Just to clarify,

1. You have Ubuntu installed?
2. You want to reinstall XP?
3. Your CD drive neither runs the Ubuntu or XP  CD?
4. you have no internet connection?

If I understand correctly you primarily need to reinstall XP without having your CD drive operational and you have no internet connection on this computer.

If you have another computer and a USB flash drive device perhaps you can load the XP CD (if I remember correctly XP is on a DVD) on a flash drive device. 

I will confirm that you don't need to do anything with Grub if you simply want to reinstall windows, the process is pretty easy overall. The windows installer should have a partitioner that is pretty automatic.

Once you have reinstalled Windows, you can also reinstall Ubuntu simply set up a dual boot system this is pretty easy and if you need help and direction please post here.

I encourage you to do both, reinstall Windows, and reinstall Ubuntu. 

Run both on a dual boot system, don't make the full change until you are ready to.

I understand that these times can be frustrating, we have all been there. Please stick with it and let us know if you need further help. 

Good Luck and keep us informed on this thread we will all try to help you with your immediate problem. & help you if you would like to set up a dual boot system with XP/Ubuntu.

---

### Post by nothingspecial on 2008-07-06
I hadn`t realised you can`t get an internet connection.
Sorry.
 Unetbootin (linked in my previous post) will also let you create a "live cd" on a usb thumb drive. If you use it on your working computer,

 [SIZE="5"]Make sure you select the thumb drive during the install process or you could install a new os on your working pc[/SIZE]

Good Luck

---

