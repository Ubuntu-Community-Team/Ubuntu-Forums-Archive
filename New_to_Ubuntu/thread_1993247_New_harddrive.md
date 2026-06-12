---
title: "New harddrive"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by nessy777 on 2012-06-01
My harddrive recently failed on my dell inspiron (had windows vista installed) my new harddrive is due to arrive soon. Apologies if this is a basic or obvious  question. I plan on using ubuntu only, is it just a case of popping in the new harddrive and then installing (from usb stick or cd?) 
Thanks

---

### Post by westie457 on 2012-06-01
> **nessy777 said:**
> My harddrive recently failed on my dell inspiron (had windows vista installed) my new harddrive is due to arrive soon. Apologies if this is a basic or obvious  question. I plan on using ubuntu only, is it just a case of popping in the new harddrive and then installing (from usb stick or cd?) 
Thanks

Hi welcome to the forum.

That is about right. One piece of advice though, plug in an ethernet cable or the installation might get stuck on one part.

Any problems just ask, someone will help you.

---

### Post by oldfred on 2012-06-01
Yes you can, but if you want more than the default partitions of / (root) and swap you will have to plan what partitions you want and maybe partition in advance. But everyone's needs vary.

I prefer to have a smaller / (root) of about 25GB  and separate /home or even /data partition. 

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by deadflowr on 2012-06-01
As long as you follow the proper installation for the new hardware, everything should go smoothly. Worst case scenario is you find out the failure is on the pc side and not the hard drive's side(unlikely) Definitely follow westie457's advice and install with a wired connection as wireless connections during installs(though much improved over time,IMO) can be sporadic.
On a side note have you done a test run from a livecd/usb? you can run it without a hard drive. Get a good feel for the layout.

---

### Post by CJ_Hudson on 2012-06-01
Installation of Ubuntu is quite simple and much quicker than installing Vista etc. All good advice above.
I think most of the problems with various network adapters are fixed now, it used to be quite difficult with earlier versions of Ubuntu with some laptops to get wireless (Wi-Fi) working. 
Have a wired ethernet connection plugged in as you do the installation so Ubuntu can "get" the updates in needs straight away to complete the installation.

---

### Post by nessy777 on 2012-06-01
Thanks so much guys, I really appreciate it. It's quite rare nowadays to see such a friendly forum where so many are willing to help.
I will let you all know how it goes :p
Once again thanks.

---

### Post by nessy777 on 2012-06-02
> **deadflowr said:**
> As long as you follow the proper installation for the new hardware, everything should go smoothly. Worst case scenario is you find out the failure is on the pc side and not the hard drive's side(unlikely) Definitely follow westie457's advice and install with a wired connection as wireless connections during installs(though much improved over time,IMO) can be sporadic.
On a side note have you done a test run from a livecd/usb? you can run it without a hard drive. Get a good feel for the layout.
Going to test using USB today first.
Just to make sure I'm doing the right.
I have 2gb stick which I have formatted, I've downloaded the Universal USB installer and have been prompted to browse and select Ubuntu ISO (I ticked the option to download the ISO within the installer) After downloading Ubuntu it is not showing as ISO? Not sure if that matters? Anyway everything seemed to go ok, as in the guide and the installer stated the process was complete transfering over to USB I then ensured the laptop would boot from the USB first.
The process the started but became stuck on a Ubuntu logo.
Not sure where I'm going wrong?
 
Hope someone can help
 
Thanks

---

### Post by nessy777 on 2012-06-02
Update. I tried it on another computer (with working hard drive) and managed to get it the test running:) 
I thought on my (non-working) laptop it could be something other than the hard drive that has failed. However, I then revoved the hard drive from the laptop, tried again and got it running:):)
Only slight issue is I couldnt get wireless as it states the firmware was missing (wired was fine) How would I solve this?
Just need to wait for my new hard drive before installing fully (i'm assuming this will be ok?)
 
Cheers:):):)

---

### Post by Jimmyfj on 2012-06-02
> **deadflowr said:**
>  Definitely follow westie457's advice and install with a wired connection as wireless connections during installs(though much improved over time,IMO) can be sporadic.


This is simply NOT true. Wireless install is (depending on your hardware) as easy as installing hooked to a cable. All you need to do is boot up your system from a Live-Cd. Click on "Try Ubuntu" and wait for the system to fully load. 

After that you can set up your wifi, log-on to the Internet and once you're on-line hit the "Install Ubuntu to disk" icon and you're rolling.

---

### Post by nessy777 on 2012-06-02
> **Jimmyfj said:**
> This is simply NOT true. Wireless install is (depending on your hardware) as easy as installing hooked to a cable. All you need to do is boot up your system from a Live-Cd. Click on "Try Ubuntu" and wait for the system to fully load. 
 
After that you can set up your wifi, log-on to the Internet and once you're on-line hit the "Install Ubuntu to disk" icon and you're rolling.
Problem now is that i cant seem to enable wireless.
I have the option to activate the driver but this doesnt seem to work? Any help would be appreciated
 
I can however connect wirelessly by using a wireless dongle (but would like to use the built in wireless)

---

### Post by inashdeen on 2012-06-02
what happened when you click activate driver?

---

### Post by nessy777 on 2012-06-02
> **inashdeen said:**
> what happened when you click activate driver?

I have now done a full install and all ok:cool:

---

