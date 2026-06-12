---
title: "Newbie can't get internet connection"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by DexInHawaii on 2013-03-28
This is my very first attempt at installing an OS other then OSX and Windows.  I have an Acer Aspire 3690 Celeron M Laptop.  I installed Ubuntu 12.04 via usb.  Everything seems to be working fine except for the Network Connection!  It keeps asking me to connect.  I have the Network Name and the Password correct but for some reason it just does not work.  I have no problem with network connections (wired or wireless) when I boot in Windows Vista.  Do I need to install a different version or is there a fix I need to do with the existing 12.04?  I have a netgear router and roadrunner cable access.  

I originally installed 12.10 and had the same problem.  I searched posts and did several different things with terminal.  I don't know what I did but 12.10 stopped loading!  I erased my thumb drive and loaded 12.04.  Same problem - different distro.  So before I do any more damage, I was hoping to get some guidance.  

I notice some posts with the output from a command in terminal.  I am not sure how to do that in this environment.  I am guessing I would have to cut and paste onto the usb drive and transfer to my Mac and send to you.  Please advise on this procedure also as necessary.

Any help would be greatly appreciated!!!

Thanks

---

### Post by kc1di on 2013-03-28
Welcome to Ubuntu DexInHawaii,

May be able to help but first I need to know what your wireless card is.

If you can go to a terminal and type the following command and list the output here it would help us. 
```
lspci
```

do you have the ability to connect the machine to a hardwired LAN connection? if so do that and go to system settings and then click on additional drivers.
if it offers you wireless driver install it and reboot see if it works then. 
good luck

---

### Post by DexInHawaii on 2013-03-28
Aloha Dave,

Thanks for your reply.  I do not have internet  connection (wired or wireless).  I did find a Broadcom STA wireless  driver, installed, reboot.  Rec'd "Problem in initramfs-tools  - This is  not an official Ubuntu package.  Please remove any third party package  and try again."  - This msg may be refering to the Broadcom wireless  driver.  I went back in and tried to removed the driver.  it seems to be  stuck...can't remove...did I tell you I am new at this?

As far  as what type of wireless card.  I got an output but don't know how to  post it...actually, I can't even find it!  I saved the output as a text  file.  I take out the thumbdrive, plug it into my mac and I can't find  the file on the thumb drive.  I thought I saved it into the documents  folder.  But I cannot find the documents folder.  What am I missing?

---

### Post by ac5jw on 2013-03-28
Hi, I had a similar problem installing Ubuntu for the first time.  I was confused about entering my details in the Network Manager or Connection Manager.

As it turns out, I was already logged in through my ISP modem box and so I did not have to set my password or login name in Ubuntu.  But I do have to log in to the ISP box to activate the connection if the box is off for a long time.  Power outages are not a problem.  And I do use my connection manager to set my DNS preferences and to name the connection to something more useful than "wiredconnection1"

---

