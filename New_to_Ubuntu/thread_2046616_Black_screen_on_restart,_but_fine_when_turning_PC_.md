---
title: "Black screen on restart, but fine when turning PC on"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by BillVonBuckby on 2012-08-23
I've recently replaced a corrupted Windows 7 with the newest Ubuntu. All very nice however whenever I restart from Ubuntu instead of rebooting the computer (Zoostorm Netbook) shows a black screen and doesn't do anything. The only solution has been to force shut down by pressing and holding the power key, and then turning the computer back on at which point it boots up fine. When the black screen does appear on restart I tried turning the brightness up as per suggestions on the forum but this hasn't done anything.

There isn't the same problem when I first switch the netbook on and it shuts down fine when I try to from inside Ubuntu, its just when I try to restart (which I obviously need to do a fair bit at the moment because of all the updates). I've reinstalled three times and still have the same problem. 

Any suggestions gratefully received!

---

### Post by Lisiano on 2012-08-23
I don't know how to fix this, but please provide the following information to those who can.
Open a terminal (Ctrl+Alt+T) and type in this
```
lspci
```
After that, copy paste everything you see in the terminal, here.

Also please surround the output with [noparse]```
these tags
```[/noparse].

---

### Post by BillVonBuckby on 2012-08-23
Thanks! here:

```
 bill@Bill-Freedom-10-270:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
bill@Bill-Freedom-10-270:~$ 

```

---

### Post by Bashing-om on 2012-08-23
Bill & others,

 Just a thought, is plymouth loading faster than the graphics mod ?
If a "sleep 15" in /etc/rc.local were edited in; Would it resolve this problem?

 regards <==BDQ

---

### Post by NikTh on 2012-08-23
Hi , 
for reboot issues we can try a parameter through grub (in kernel) and see if solve the problem.

From terminal (ctrl+alt+t) 

```
gksudo gedit /etc/default/grub
```at the opened window , find the line 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** and make it like this 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=a,w"**
save the document and run in terminal 
```
sudo update-grub
```then reboot your system with below command
```
sudo reboot
``` and when login again , try to see if restart fixed.
Thanks

---

### Post by BillVonBuckby on 2012-08-24
NikTh - I tried this but when I typed "sudo reboot" it just did what it did when I've tried to restart previously... have you got any other ideas?

Bashing-om - I'm still new to this lark, where / how would I insert the code that you have suggested?

thanks all for your help :-)

Bill

---

### Post by NikTh on 2012-08-24
Hi , 
can you please give the results of 
```
cat /proc/cmdline 
lspci -nnk | grep -iA2 vga
cat /etc/rc.local
```
Thank you

---

### Post by BillVonBuckby on 2012-08-24
Hello,

```
 
bill@Bill-Freedom-10-270:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=91b00cf7-ea79-4dab-88c2-3b390c2e8f45 ro quiet splash reboot=a,w vt.handoff=7
bill@Bill-Freedom-10-270:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
    Subsystem: Device [1b7d:0002]
    Kernel driver in use: i915
bill@Bill-Freedom-10-270:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

thanks!

---

### Post by NikTh on 2012-08-24
OK , 
you can remove the reboot=a,w from /etc/default/grub if effect is nothing. Do not forget to run ```
sudo update-grub
``` after you save the document. 

and here I found a bug with your problem and same graphics [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/897665](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/897665) , it seems that Xorg not cooperate well with the card (?)

Try to update the Xorg and card drivers with below commands and see if your problem fixed.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get dist-upgrade
```reboot 
Thank you.

---

### Post by BillVonBuckby on 2012-08-24
Hello,

I tried those two things (the second one made it update for about half an hour?), rebooted from terminal and its still doing it sadly.

---

### Post by NikTh on 2012-08-24
Hi , 
out of ideas.... sorry.. 

**1.** Do you want to try the Ubuntu 12.10 (Unstable) version ? It has the kernel 3.5 , maybe 3.5 corporates better (?) , not sure , but worth to test it. 

Download from here --> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) 
burn it to a Usb , with Unetbootin --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
and test if works properly. 

**2.** Maybe you can try a workaround like Bashing-Om suggested ? It is not a solution , but you can do your job until fixed. (I assume with some update). 

Try this workaround 
Open a terminal and
```
gksudo gedit /etc/rc.local
```It will open the rc.local file and you will add some commands **before exit 0** . exit 0 must be the last (always).

add bellow with order 
```
sleep 3
chvt 2
sleep 2
chvt 7
```save the document and reboot to see the effects. 

Thank you.

---

