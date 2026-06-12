---
title: "Can't get going...No Mounts?"
date: 2016-05-21
forum: New to Ubuntu
---

### Post by peter249 on 2016-05-21
Hi I'm new trying to move to Ubuntu. I have downloaded Ubunto onto my laptop. I can still boot to Windows7 successfully. But if I try and boot to Ubuntu I get an error message.
Mount: Can't read/Proc/mounts.  No such file or directory.
Please help, I can't get started.
Thanks

---

### Post by mörgæs on 2016-05-21
Hi, welcome to the fora.

Are you trying to install through Wubi, that is running Ubuntu within Windows? 
Which release of Ubuntu are you installing?

---

### Post by peter249 on 2016-05-21
Hi...Sorry I couldn't see your reply.
Yes I installed through Wubi yesterday.....took over an hour.
I don't think it is "within" windows as I can chose which to boot at start-up
The Ubuntu release could be (13.04)?
I have to log in as a Guest!
The mouse is terribly jumpy.....

---

### Post by Impavidus on 2016-05-21
Neither wubi nor Ubuntu 13.04 are supported anymore. Wubi installs Ubuntu on a virtual partition on the Windows partition and uses some tricks with the Windows boot loader to make it bootable, but that no longer works with the latest Windows systems (although it may work with non-UEFI Win7 systems). Use Ubuntu 16.04 and make it a real dual boot.

---

### Post by mörgæs on 2016-05-21
Yes, if you want to keep Windows then best you can do is boot into Windows and shrink the partitions. After that install Buntu in the newly freed space.

---

### Post by peter249 on 2016-05-21
Hi...o dead o dear o dear..
I'm getting cold feet now. I guess I better keep Windows7. 
Say good bye to 18GB memory until I can find out what Partitions need shrinking and where to find them.... sounds a bit like piles?
Then think again about Windows.
Things are easy when you know how but I haven't started off very well. 
Wrong Wubi...wrong Ubuntu...
Thank you both very much for your speedy help.

---

### Post by mörgæs on 2016-05-21
Installing Ubuntu is simple, much simpler than installing Windows. We are here for guiding you.

You will say goodbye (or good day) to 18 GB of hard disk space, but is that a problem? How small is the drive?

---

### Post by peter249 on 2016-05-21
Hi Morgaes...I'm just having a moment of panicking...bit better now.
I'm not finding installing Ubuntu simple.
I remember I allocated 18GB of hard drive to Ububtu but I can't seem to find Ubuntu on the hard drive?
Windows says I have 92.2GB free of 148GB so that doesn't seem too bad.
I really want to leave Windows but I'm a bit scared to burn all my bridges in one go....
And it's raining!

---

### Post by mörgæs on 2016-05-21
Since you have 92 GB free you can just shrink the Windows partition say 20 GB. Reboot Windows after that. 

Please post again when that is done,

---

### Post by peter249 on 2016-05-21
Hi.
Went to Disk Management(c):
Right clicked Disk 0 c: 148.95GB NTFS
Shrink C:
Total size before shrink in MB 152525
Size of available shrink space in MB 67416
Enter the amount of space to shrink 67416 (High lighted)
Total size after shrink 85109
Please advise what to do...or am I in the wrong place?
Thanks

---

### Post by mörgæs on 2016-05-21
No, you are in the right one. Just reboot Windows to verify that everything is all right. 

Now do some googling and see a selection of screen shots of X/L/K/Ubuntu and decide which look and feel you prefer. If the computer is old then only the two first ones are recommended.

---

### Post by Impavidus on 2016-05-21
When you installed using wubi, it must have left a clean uninstaller for Ubuntu. I never used wubi and I haven't used Windows in a long time, so I can't say exactly where. You can use the wubi uninstaller to cleanly remove wubi/Ubuntu and the entry in the Windows boot menu. Best to do that first.

Your wubi system is in a huge file called root.disk on your Windows partition. A real dual boot is on a partition of its own. Disk usage is the same, but you'll move it from inside the Windows partition to outside of it.

You can use Windows disk management to shrink your Windows partition. You may have to pay attention to the 4 primary partition limit. Show us your current partitioning and we may be able to suggest the best way to make 20GB of unallocated space.

---

### Post by peter249 on 2016-05-21
Hi morgaes.
Thanks for the reply.
My laptops a bit old...say 2009. I use it mostly for the internet, News - Email - Sudoko - Ebay - things like that. 
I do Skype the wife when I'm away! but there may be an alternative? 
I would appreciate any recomendation as to which Ubunto x or L, as long as it's not 13.04!
Thanks

---

### Post by peter249 on 2016-05-21
Thank you Impavidus. I found 'Uninstall Wubi' somewhere! ran it, re-booted, and Ubuntu has gone!
Happy me, it was niggling me knowing it was still there....thank you again.
Sorry I don't know yet how to add an image......

---

### Post by Impavidus on 2016-05-21
Use "+ Reply to Thread" or, if using the quick reply, click "Go Advanced". Then you can add a picture as attachment.

2009 is a bit older, but it may still be good enough for Ubuntu or Kubuntu. That depends on the amount of RAM and the graphics hardware. The lighter flavours should work too.

---

### Post by him610 on 2016-05-21
FWIW, I have three machines, two laptops and one desktop, with Bios date of ~2008. Two have 4GB memory, one has 2.8GB memory. All three have/had LTS 16.04 Ubuntu installed on them recently. There is no problem running Ubuntu 16.04 on machines that are eight years old.

---

### Post by peter249 on 2016-05-22
There should be an attachment here.
Screenshot of 'Disk Management'
If not then I got it wrong......nothing is very straight forward.

---

### Post by mörgæs on 2016-05-22
> **peter249 said:**
> 
My laptops a bit old...say 2009. I use it mostly for the internet, News - Email - Sudoko - Ebay - things like that. 
I do Skype the wife when I'm away! but there may be an alternative? 
I would appreciate any recomendation as to which Ubunto x or L, as long as it's not 13.04!


It sounds like there will be no obstacles to switching to Buntu, and the disk layout is also fine. 

Next step is to download the 16.04 release of the Buntu you like the most, say Xubuntu. You will find the link at the top of this page where it says 'Ubuntu community'.

---

### Post by Impavidus on 2016-05-22
Your partition layout is quite simple, which makes things easy. You can defragment the C partition using Windows tools and then shrink it to create space for Ubuntu. Create about 20 to 40 GB unallocated space. Reboot Windows a couple of times to let it run all its filesystem checks.

Create a live disk (usb drive, dvd works too, bit is a bit old-fashioned) and boot from it. Make sure everything works. You can try different flavours to determine which you like most.

You don't have a separate data partition in Windows. It's not entirely safe to directly write data to the Windows C partition, so if you want to share data between Ubuntu and Windows I suggest you create a separate data partition. If you don't want that, you can still share data using an external drive, but that's less convenient. You can create the shared data partition and the partitions for Ubuntu (root and swap) while running the live session.

---

### Post by peter249 on 2016-05-22
Hi. I've done a diskfrag, run Ccleaner and rebooted several times and everything seems to still be working.
Now, to create 30GB of space for Ubuntu I need to shrink C: partition by a total of 30GB - 30000MB?
In disk Management/Shrink C:
Where it says, 'Enter the amount of space to shrink in MB' I type 30000 and click shrink?
Hope I'm doing all this in the right order?
Thanks.

---

### Post by Impavidus on 2016-05-22
Shrinking by 30000MB seems about right. I don't know what the Windows tool looks like, but I guess it's reasonably self-explanatory. Windows won't let you do things to its partition that will make it unbootable. After resizing, reboot Windows a few times to let it run further checks.

---

### Post by peter249 on 2016-05-22
Shrunk!......only giving 29.3GB  Unallocated for some reason but there we are.
I'm away from home at the moment so I don't have a USB memory stick or a CD to load or burn Xubuntu to, so can I load it straight onto my c: drive somehow?
Thanks

---

### Post by Impavidus on 2016-05-23
There are some possibilities to load the iso from the hard drive, but I think you'd need the grub boot loader already – which you don't have, as that will only be installed with Ubuntu. So you really need that live usb or live dvd.

---

### Post by peter249 on 2016-05-23
OK Impavidus, I'm a bit disappointed not to be able to complete the instillation now but what must be must be. 
When I get home I'll buy a usb drive (size)? 
Then get back to you.
Thanks for all your and Morgaes help.

---

### Post by mörgæs on 2016-05-23
Any USB stick 2 GB or larger will do.

---

### Post by peter249 on 2016-05-23
HI! Just managed to obtain a Kingstone usb stick with 3.11GB free of 3.64.
Hope you are as happy as I am?....hahahah........bet you will be pleased to see the back of me.
But thanks.

---

### Post by peter249 on 2016-05-23
Hi, I'm back again..sorry.
I've downloaded [COLOR=#000000] [/COLOR][xubuntu-16.04-desktop-amd64.iso]("http://cdimages.ubuntu.com/xubuntu/releases/16.04/release/xubuntu-16.04-desktop-amd64.iso") and its in my downloads folder in 'C' drive.
[COLOR=#000000][/COLOR]Do I just copy it into my usb memory stick and run it from there?
And what about the new allocated partition on my 'C' drive?
Bet these are silly questions but thats my level at the moment......I'll improve.....hope...
Thanks

---

### Post by oldos2er on 2016-05-23
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by peter249 on 2016-05-24
Just like to say thank you to everyone for their help.

---

### Post by mörgæs on 2016-05-24
You're welcome.
If the problem is solved please mark the thread so.

---

### Post by mörgæs on 2016-05-24
Thanks for marking it solved. 
For other users who might find the tread: Would you mind posting a few words about what you did to install?

---

