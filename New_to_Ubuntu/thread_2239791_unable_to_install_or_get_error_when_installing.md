---
title: "unable to install or get error when installing"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by piadex2 on 2014-08-15
Dear Forummates,

I have Gigabyte EP45-DS3R motherboard. I have 2 HDDs in RAID 0 (stripe). Windows 7 pro 64bit already installed. Now I want to install Ubuntu from Ubuntu 14.04.1 64-bit LTS disk but when I got to screen choose timezone ("Where are you?") (after partitioning and stuff) always get the following message:
no entry sign then: "??? ???".

What is going on? I tried all the possibilities (I think). Got no more idea. Please help if You can.

Thank You in advance for Your help.

piadex2

---

### Post by TheFu on 2014-08-16
RAID0?   Is it FakeRAID or something built-into Windows?

DANGER WILL ROBINSON - DANGER!!!!  You could be risking your Windows install completely.
If possible, running the **boot-info** script would help us a bunch. My signature has a link.

What CPU and how much RAM do you have? Running a virtual machine may be better/easier, but only with appropriate hardware.  It won't risk your storage either.

---

### Post by Jonathan Precise on 2014-08-16
Also, try burning it again and check the SHA256 sum.

---

### Post by sandyd on 2014-08-16
1. Check the md5sum of the ISO you downloaded. There are instructions [here]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows") for windows.
2. Check the disc that you burned to make sure that its burned correctly

---

### Post by piadex2 on 2014-08-16
Dear Helpers,

1. I am gonna check the iso-s 
2. but I do not think there is a problem. Because after I created this thread I downloaded the 12.04.4 (alternate, non-live) version. And the same thing happens: after creating the new ext4 and swap partitions the install stops: fatal error when installing GRUB.
So, I think the 2 problems connected.

What is the think (or can be the thing) that prevents GRUB to install.

4. The RAID0 is the one that was created by pressing the CTRL + I (no OS but a integrated motherboard software that does not depend on any OS) then create.... So I think it should be a hardware RAID0.

What do You think?

Thanks again.

piadex2

---

### Post by sandyd on 2014-08-16
> **piadex2 said:**
> Dear Helpers,

1. I am gonna check the iso-s 
2. but I do not think there is a problem. Because after I created this thread I downloaded the 12.04.4 (alternate, non-live) version. And the same thing happens: after creating the new ext4 and swap partitions the install stops: fatal error when installing GRUB.
So, I think the 2 problems connected.

What is the think (or can be the thing) that prevents GRUB to install.

4. The RAID0 is the one that was created by pressing the CTRL + I (no OS but a integrated motherboard software that does not depend on any OS) then create.... So I think it should be a hardware RAID0.

What do You think?

Thanks again.

piadex2
It is probably a fakeraid using dm-raid, which occasionally behaves oddly under Ubuntu.

---

### Post by piadex2 on 2014-08-16
Hi,

Thanks for being so quick. How can be sure it is a "fakeraid". Is there any chance I can make ubuntu run on my system?
Thanks again.

piadex2

---

### Post by piadex2 on 2014-08-17
Hi Everyone,

Okay install is done but it is not perfect. After a little "boot-repair" finally achived a menu. But in this menu linux start loading but never finishes. Windows 7 boots nicely and everything is perfect. What can be the problem?
Thank You.

piadex2

---

### Post by TheFu on 2014-08-17
**boot-info** data please, as previously requested.

---

### Post by piadex2 on 2014-08-24
Dear TheFu,

Sorry for answering so late.
Here is the boot-info:
[http://paste.ubuntu.com/8136000/](http://paste.ubuntu.com/8136000/)

So: why ubuntu can not load? Stops in the middle of the loading and starts telling me that something is wrong.
Then I would like to set Windows 7 as the default OS when it is asked.

Thank You very much for Your help in advance.

piadex2

---

### Post by piadex2 on 2014-08-24
Dear Forummates,

I have additional information concerning ubuntu loading failure. I will write it down here what I can see on the screen:

...
init: plymouth-upstart-bridge main process (456) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
Adding 6000124k swap on /dev/mapper/iswdgcacbehbe_filmszerk4. Priority:-1 extents:1 across:6000124k FS

"filmszerk" is the name of my fakeraid 0 array.

I hope this info will help us.

Thank You.

piadex2

---

### Post by bohicaman on 2014-08-24
I'm brand new to Ubuntu. I don't know a thing about this forum either! (most of it is not understandable to a novice forum user!!!! So I don't even know if I'm in the right place!) Anyway, I have spent the last three days trying to install Ubuntu 14.04.1 onto my system. It is a  Windows7 Home Premium, with SP1. 64 bit, with 3.40 gigahertz Intel Core i7-4770, on a ASUS computer. I have 16GB RAM with a 2TB C: drive, and a separate 1TB D: drive. 

I have downloaded the file, "ubuntu-14.04.1-desktop-amd64.iso" and burned it directly to DVD using the recommendation listed on the Ubuntu site (which basically copied the file) and also burned that file using "ImgBurn 2.4.4.0" which un"ziped" the file and put 14 folder and files on the DVD. I also partitioned 248GB of unallocated space on my C: drive. I then, as directed by your site, re-booted with the first, single file DVD after setting the boot order to include the DVD drives. The system just re-booted to Windows. I then placed the 2d DVD in and re-booted. I got the Ubuntu startup screen listing a bunch of install/disk checking selections. I chose INSTALL UBUNTU and pressed enter. I got the pick a language screen. I chose English. I again pressed Enter. The screen went to black, displayed Ubuntu and 5 dots under the word flashed in sequence left to right in red. Then the all stopped in red and the systems locked up. I repeated this procedure several times. During the process, I pressed ESC button and got a screen of rapidly scrolling computer statements. Several of these said something like, LINE 7 and then something about NO MEDIUM FOUND.

So, now that I am totally pissed off and frustrated, can someone tell me how to load this OS onto my computer????????? Obviously this site is not up to date with it's own product!!

---

### Post by mozalmy on 2014-08-25
Here is a well written tutorial about partitioning your disk. Check out the RAID section. It might give you some idea on how to deal with the issues you are facing.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by mozalmy on 2014-08-25
> **bohicaman said:**
> I'm brand new to Ubuntu. I don't know a thing about this forum either! (most of it is not understandable to a novice forum user!!!! So I don't even know if I'm in the right place!) Anyway, I have spent the last three days trying to install Ubuntu 14.04.1 onto my system. It is a  Windows7 Home Premium, with SP1. 64 bit, with 3.40 gigahertz Intel Core i7-4770, on a ASUS computer. I have 16GB RAM with a 2TB C: drive, and a separate 1TB D: drive. 

I have downloaded the file, "ubuntu-14.04.1-desktop-amd64.iso" and burned it directly to DVD using the recommendation listed on the Ubuntu site (which basically copied the file) and also burned that file using "ImgBurn 2.4.4.0" which un"ziped" the file and put 14 folder and files on the DVD. I also partitioned 248GB of unallocated space on my C: drive. I then, as directed by your site, re-booted with the first, single file DVD after setting the boot order to include the DVD drives. The system just re-booted to Windows. I then placed the 2d DVD in and re-booted. I got the Ubuntu startup screen listing a bunch of install/disk checking selections. I chose INSTALL UBUNTU and pressed enter. I got the pick a language screen. I chose English. I again pressed Enter. The screen went to black, displayed Ubuntu and 5 dots under the word flashed in sequence left to right in red. Then the all stopped in red and the systems locked up. I repeated this procedure several times. During the process, I pressed ESC button and got a screen of rapidly scrolling computer statements. Several of these said something like, LINE 7 and then something about NO MEDIUM FOUND.

So, now that I am totally pissed off and frustrated, can someone tell me how to load this OS onto my computer????????? Obviously this site is not up to date with it's own product!!

Ubuntu 14.04 iso is only 981MB in size. How did you end up having them in two separate DVDs? :confused:

ImgBurn is probably the best cd/dvd burning software available at the moment. You should just start ImgBurn, insert a blank dvd, load the iso image, set the burning speed and burn. That's it. You will be able to boot from the DVD and try Ubuntu before installing it.

Here is a tutorial on how to setup Ubuntu-Windows 7 dual boot: [http://www.youtube.com/watch?v=0W7XYAB4cLc](http://www.youtube.com/watch?v=0W7XYAB4cLc)

---

### Post by piadex2 on 2014-08-25
Hi.

Please, make another thread for this or find the proper thread for your topic because we are talking about a totally different thing.
Thank you for understanding.

piadex2

---

### Post by piadex2 on 2014-08-25
Dear Helpers,

Please check out the 11th post. There is a detailed info on the boot (as previously requested).
Thank You for Your help in advance.

piadex2

---

### Post by Abdul-Azeez_Ajibol on 2014-08-25
Hello, 
I am new to ubuntu and when trying to install the ubuntu 14.04 alongside my windows 8.1, it said it could not find any installed os on my disk and I tried to cancel, however I could not. Now my computer says no boot device found and I cant even boot into my windows. Please help... I have too much stuff I cant afford to lose on the windows.
I just saw my mistake, I forgot to uncheck the format harddisk button before proceeding.  Although I cancelled after. Is there no way I can recover my windows installation and my files? Harddisk properties shows empty  now.
Thank you

---

### Post by piadex2 on 2014-08-26
Hi pal,

Wrong thread please find a suitable one.
Thanks.

p.

---

### Post by piadex2 on 2014-08-26
[COLOR=#000000]Dear TheFu,[/COLOR]

[COLOR=#000000]Sorry for answering so late.[/COLOR]
[COLOR=#000000]Here is the boot-info:[/COLOR]
[http://paste.ubuntu.com/8136000/](http://paste.ubuntu.com/8136000/)

[COLOR=#000000]So: why ubuntu can not load? Stops in the middle of the loading and starts telling me that something is wrong.[/COLOR]
[COLOR=#000000]Then I would like to set Windows 7 as the default OS when it is asked.[/COLOR]

[COLOR=#000000]Thank You very much for Your help in advance.[/COLOR]

[COLOR=#000000]piadex2[/COLOR]

---

### Post by TheFu on 2014-08-26
Your system appears to be using fakeRAID. I don't have any experience with that and wouldn't presume to suggest any course of action.  Please be very careful with this setup. Data loss is a real danger since it is an unusual setup for most Linux installs.

I would use a non-RAID partition for a first-attempt Linux installation and I'd ignore all the other storage during the install.  Definitely - you must pick the exact partition where the / partition and another partition for swap. 20G for / is fine to get started - if you don't load many GUI programs, 10G is fine.  I don't think I'd run boot-repair either - with a strange setup, it could do unexpected things.

As to making Windows the default boot again - Windows must be booted by the Windows boot-loader. With a Linux install, grub must boot first, then chain to Windows-boot, then to the Windows OS.  That means you'll need to modify the grub menu and select Windows-boot as the default.  Of course, you could remove grub and have Windows fix the boot loader - this will effectively remove the Linux boot capability.

If you want to research more - I'd google for "fakeRAID ubuntu" and "grub2 change default boot".
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order) was found here.

Sorry that I can't help more.

If you want to setup a 2 partition Linux system (/ and swap) without RAID-anything, let me know.

---

