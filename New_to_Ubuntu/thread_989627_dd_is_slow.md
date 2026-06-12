---
title: "dd is slow"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Zularan on 2008-11-21
Long story short I lost my home directory.  I was removing a user from Vista and despite telling it to keep the files, it seemed to remove them anyway, around 100g.

Pretty sure it's using usb2 speeds, this is the output of lsusb

```
Bus 005 Device 012: ID 0d49:7410 Maxtor 
Bus 005 Device 009: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 005 Device 008: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 005 Device 007: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 06a3:075c Saitek PLC X52 Flight Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 046d:c227 Logitech, Inc. 
Bus 001 Device 008: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 007: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 001 Device 006: ID 046d:c226 Logitech, Inc. 
Bus 001 Device 005: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```



My home folder was it's own separate ext3 partition on the same hdd and I'm trying to clone it first before I start recovering the data as I really can't afford to lose it.

I ran ```
sudo modprobe ehci_hcd
``` to make sure usb2 drivers were going.  I want to clone it to an image on a usb drive.

then 

```
sudo dd if=/dev/sda3 of =/media/Maxtor/recover.img
```

It starts of quick doing around 1gb a min but really started to slow down around the 10gb mark (size of the recover.img file).
I left it on over night and it's only upto 20gb (10hours).  This is going to take forever at this rate as I have 170gb for it to clone. Any reason it's bogging down like this?

Is there any alternatives to 'dd' ? I tried out partimage but I need a bit by bit copy not just legit files so I can attempt to recover the deleted ones.

I'm using the Ubuntu dvd so nothing gets mounted as it starts as I really can't afford to lose my home folder permanently.

---

### Post by LowSky on 2008-11-21
OK I dont understand wha you are talking about at all?

So from what I can read, you were deleting a user account under Vista..right? Do you mean a Windows account or an Ubuntu account? 

now you backing up your /home partition onto a usb attached hard drive.. corrrect?
and your doing so from a live CD?

If your doing it from a live cd, it is running everything from your RAM so it will take a long time, sorry no  two ways about it

---

### Post by louieb on 2008-11-21
May have to play with the buffer size. Pretty good thread on the dd command here.[Learn the DD command - LinuxQuestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=362506")

---

### Post by caljohnsmith on 2008-11-21
If you want to speed up dd, just use a larger block size like:
```
sudo dd if=/dev/sda3 of=/media/Maxtor/recover.img bs=10M conv=notrunc
```
Give that a shot, and I think you will see a significantly shorter copy time. :)

---

### Post by Zularan on 2008-11-21
That's pretty much correct, I removed a windows user in Vista (not a Ubuntu one). I had the My Documents/My Pictures etc pointing to my /home/user folder on another partition which worked quite well as I use both OS's often.  When I removed the Vista user it asks if I wanted to delete or keep the user's files, even though I selected 'keep', Vista removed my /home/user dir.

I'm pretty new to 'dd' and will play around with the block size options.  Right now it seems to start off fast but slowly grinds to a halt.  It's done 8gb since I've typed this so it looks like we're winning now.  

Thanks, I'll let you know if it did the trick, thanks for the responses and tips.

---

