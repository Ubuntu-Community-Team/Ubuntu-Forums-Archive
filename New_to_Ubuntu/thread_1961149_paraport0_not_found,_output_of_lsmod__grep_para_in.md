---
title: "paraport0 not found, output of lsmod | grep para* included"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by Kneegrowplease on 2012-04-18
I had it working before, then I did some god knows what late one night copying and pasting code into my terminal and now I'm screwed.


```
pedro@pedro-ET1330:~$ lsmod | grep para*
parport_pc             36962  0 
parport                46562  2 parport_pc,ppdev
```


it used to look similar to this:

```
 lsmod | grep para*
parport_pc             44200  1 
parport                50096  3 ppdev,lp,parport_pc
```



I'm using a pci card with 2 rs-232 and 1 db25 parallel port

on 11.10 Oneric 64


BTW, been searching google for like 12 hours



Here's the solution I found::guitar:




> Exclamation Re: PCI-Parallel Card Install
NetMos Technology PCI 9865 Parallel Controller card install how-to for Ubuntu

Well, I do not have a parallel port on my computer so I bought a cheap card on Ebay. It is a no name card that came with a driver cdrom and a Linux driver called msc9865_Linux. I couldn't "Make" or "compile" anything from the driver. The instructions were to vague and after googling, it seems the driver was to old and the manufacturer stopped supporting it. I eventually found a tutorial by Lazly at [http://lazly.hu/q/netmos-technology-...tu-904-english](http://lazly.hu/q/netmos-technology-...tu-904-english) which worked for me. It was not very detailed but I managed. Even though it is already in English, I modified and rewrote it here so it makes more sense and added more detailes.

Im using ubuntu 8.10 but this will work with 9.04 and others. As I explained above, I too tried to install an old printer with a parallel card and was going around in circles with the driver and installation instructions. I googled 'til my fingers were raw and still nothing. However, the following how-to solved my problem without using any driver!

First, make sure your system "sees" the card with the following:
$ sudo lspci
...
03:06.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller
...
Scroll down until you see something similar to the above. As you can see, my system sees the card and identified the parallel port. By the way, there were two serial ports listed on the same card. Which I will not be using. Anyway,...

$ sudo cat /proc/ioports | grep parport
<nothing>

$ sudo modprobe -r lp
$ sudo modprobe -r parport_pc

$ sudo lspci -v
...
03:06.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03)
Subsystem: Device a000:2000
Flags: bus master, medium devsel, latency 64, IRQ 10
I/O ports at e000 [size=8]
I/O ports at d800 [size=8]
Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [48] Power Management version 2
...
Note the I/O port above listed as being at e000. It will probably be different on yours. In the following command replace mine with whatever yours may be.

$ sudo modprobe parport_pc io=0xe000
$ sudo modprobe lp

$ sudo /etc/init.d/cups restart

At this point, my printer started printing so I stopped, but you may need to install your printer drivers. If that is the case, Use the official Ubuntu printer setup GUI.

Before you reboot your system, you still need to edit a couple of files so you can keep printing when the system is restarted. The first file, has to be created and the info added to it. The second file should already exist so you just need to add the line to it. So go ahead and create the file "parport_pc" in the directory as indicated below. Then edit it with your fav text editor. I used Nano in my examples.

$ sudo nano /etc/modprobe.d/parport_pc
options parport_pc io=0xe000

Once the file "parport_pc" is created and the option above is added, edit the next file to make sure it all works after rebooting.
$ sudo nano /etc/modules
...
parport_pc
lp
...

That's all. I've been using Ubuntu for a year now and love it but I'm not an expert so maybe other here can further help you along. I hope this method helps others. Later, JoeCrow

---

### Post by Kneegrowplease on 2012-04-18
Ok, I found the code I used to "F" up my paraport....




> Re: can't find lpt port
Problem solve.
Code:

maxwell@Maxwell-pc:~$ modprobe parport
maxwell@Maxwell-pc:~$ sudo modprobe parport_pc io=0x378 irq=7
maxwell@Maxwell-pc:~$ lsmod | grep par
parport_pc             31940  1 
parport                35340  3 parport_pc,ppdev,lp
maxwell@Maxwell-pc:~$ sudo rmmod lp


then I did ALL of This:

For parallel port on Ubuntu we found some good Fixes
listed as below

parport is missing on your /dev/partport0
then please follow this
on terminal ;
sudo mknod -m 666 /dev/parport0 c 99 0
ur password:
then it should be avialble for use

or

For Edgy or Dapper please remove the lp module from /etc/modules and reboot.
on terminal;

sudo gedit /etc/modules
and remove lp save the file.


I know, Stupid. I promise not to do it again, please help Or I'll be forced to reinstall. I'm currently upgrading to 12.04 in a hope it will magically cure all my woes....

---

### Post by Kneegrowplease on 2012-04-21
I got my jtag to work through parport0 by doing ```
sudo rmmod lp
```

---

