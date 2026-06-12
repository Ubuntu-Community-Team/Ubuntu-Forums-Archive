---
title: "hi i want to install realtek driver"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by count123 on 2008-05-23
hi i just install a new ubuntu server and  it didnt recognize my ethernet card which is realtek rtl8111

any idea how to install it A to Z (i have a USB stick i can use)

thanks

---

### Post by shifty_powers on 2008-05-23
can we have output of

```
lspci
```

please

---

### Post by stchman on 2008-05-23
> **count123 said:**
> hi i just install a new ubuntu server and  it didnt recognize my ethernet card which is realtek rtl8111

any idea how to install it A to Z (i have a USB stick i can use)

thanks

Here is the driver for that card for the PCI-E version.

[ftp://210.51.181.211/cn/nic/r8168-8.006.00.tar.bz2](ftp://210.51.181.211/cn/nic/r8168-8.006.00.tar.bz2)

There is usually a readme in the archive.

---

### Post by count123 on 2008-05-23
cant really access the comp without the ethernet card byt i will write down the last 2 lines 

intel corporation 82801g (ich7 family) smbus controller (rev 01)
ethernet controller : realtek semiconductor co., Ltd rtl8111/8168b PCI express gigabit ethernet controller (rev 02)

throughout the output it says intel 82801G for the usb and other controllers and bridges \

thanks

---

### Post by neurostu on 2008-05-23
Googling for "rtl8111 linux drivers" 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)
came up as one of the first hits:

1. Goto the website
2. Download the driver for: Linux driver for kernel 2.6.x and 2.4.x (Support x86 and x64)
3. Unzip the download.
4. Read the readme:
> 
# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8168.ko (or r8168.o in linux kernel 2.4.x)


5.post back problems.

---

### Post by stchman on 2008-05-23
This is odd, I have a PC with the 8139 10/100 and an 8169 10/100/1000 that work OOB with Ubuntu.  The 8169 is an onboard PCI-E gigabit NIC.

---

### Post by count123 on 2008-05-23
how do i access the usb stick drive?

---

### Post by neurostu on 2008-05-23
when you plug it in does it mount? 
To check this open a terminal and type:
```

cd /media/
ls

```
post the results below, you should see something like USBDrive or something like that, my usb drive is branded patriot and it shows up as /media/Patriot_Memeory/

---

### Post by count123 on 2008-05-23
nope only cdrom and cdrom0

---

### Post by count123 on 2008-05-23
nothing?

---

### Post by neurostu on 2008-05-23
ok then you need to mount it.
To find out where the device is type:
```

tail -f /var/log/messages

```
then plug in your drive and paste the message that appears below.
look for something like sda or sdb to appear.

Once that appears use that info to mount the drive.

to mount the drive first make a directory to mount to:
```

sudo mkdir /media/usbMount

```
then mount the drive with:
```

mount /dev/sdX /media/usbMount

```  where sdX is what appeared above.

---

### Post by neurostu on 2008-05-23
> **count123 said:**
> nothing?Be patient man! you posted 3 minutes ago and it takes time to get answers to these questions.

Most of the time when people are posting answers they have to go out and find the answers to your questions, using google or other linux forums, so be patient!

---

### Post by count123 on 2008-05-23
sorry for before.. thanks anyway

it gives me the following message:
mount: you must specify the filesystem type

---

### Post by neurostu on 2008-05-23
try:
```

mount -t fat32 /dev/sdX /media/usbMount
or
mount -t fat /dev/sdX /media/usbMount

```

---

### Post by count123 on 2008-05-23
unkown filesystem type fat or fat32

---

### Post by count123 on 2008-05-23
may b i can access using the Cdrom i alreay burned the driver also?

---

### Post by neurostu on 2008-05-23
oh, try FAT or FAT32, or vfat

---

### Post by neurostu on 2008-05-23
> **count123 said:**
> may b i can access using the Cdrom i alreay burned the driver also?, if you have a Cd burner that will work too.


If I can ask why do you have ubuntu server installed and not Ubuntu Desktop?

---

### Post by count123 on 2008-05-23
just tried that we need to build a new test enviorment with some linux servers thought to try ubuntu server :( anyway while typing i am dowloading the desktop edition

---

### Post by count123 on 2008-05-25
hi again

tried everything now my network doesnt work correctly...

can anyone help... i have installed now the ubuntu desktop edition i am trying to install the rtl8111 driver but without success i am getting all kind of errors when submitting the make command through the readme file any idea how to overide it?

thanks

---

### Post by count123 on 2008-05-25
ok here is the error i get any one?

root@endless-server:/home/aviv/Documents/r8168-8.006.00# make clean modules
make -C src/ clean
make[1]: Entering directory `/home/aviv/Documents/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/aviv/Documents/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/home/aviv/Documents/r8168-8.006.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/aviv/Documents/r8168-8.006.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/aviv/Documents/r8168-8.006.00/src/r8168_n.o
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c: In function â€˜rtl8168_init_boardâ€™:
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:2300: error: implicit declaration of function â€˜SET_MODULE_OWNERâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c: In function â€˜rtl8168_init_oneâ€™:
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:2600: error: â€˜struct net_deviceâ€™ has no member named â€˜pollâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:2601: error: â€˜struct net_deviceâ€™ has no member named â€˜weightâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c: In function â€˜rtl8168_rx_interruptâ€™:
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4029: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4029: warning: type defaults to â€˜intâ€™ in declaration of â€˜_yâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4029: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4029: warning: comparison of distinct pointer types lacks a cast
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c: In function â€˜rtl8168_interruptâ€™:
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4225: error: too few arguments to function â€˜netif_rx_schedule_prepâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4226: error: too few arguments to function â€˜__netif_rx_scheduleâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c: In function â€˜rtl8168_pollâ€™:
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4274: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4274: warning: type defaults to â€˜intâ€™ in declaration of â€˜_yâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4274: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4282: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/home/aviv/Documents/r8168-8.006.00/src/r8168_n.c:4285: error: too few arguments to function â€˜netif_rx_completeâ€™
make[3]: *** [/home/aviv/Documents/r8168-8.006.00/src/r8168_n.o] Error 1
make[2]: *** [_module_/home/aviv/Documents/r8168-8.006.00/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/aviv/Documents/r8168-8.006.00/src'
make: *** [modules] Error 2

---

### Post by count123 on 2008-05-25
anyone?

---

