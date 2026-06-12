---
title: "Wifi Troubles. Please Help"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by ArcticWolfy2882 on 2008-08-04
Hello ladies and gentlemen of the Linux Realm :D.

Since I'm posting in this section I guess you can tell I'm somewhat new at linux. Well to cut to the chase here is my dilemma. 

I have my laptop dual partitioned with Windows Vista Home Edition and Ubuntu (Hardy Heron)

I have a Toshiba Satellite A205-S5804 Laptop.

The device I am having trouble with is the Realtek Wireless 802.11g 54Mbps USB 2.0 Network Adapter.

Now I was browsing through the forums and found a way of installing the driviers and such as follows...

"The windows driver must be the WinXP driver for your card. I did a little searching, and came up with this one from Toshiba's European web site:
[http://support1.toshiba-tro.de/tedd-...1120145654.zip](http://support1.toshiba-tro.de/tedd-...1120145654.zip)

After you unzip it, go to the folder /Wireless Network Driver Realtek/RTL8187B/WINXP. In there you will find these files:

net8187b.cat
net8187b.inf
rtl8187B.sys

NDISwrapper uses the .inf file for the setup and configuration, and you need to give the path to the file. If the username is pnp, then you would enter this (as root):

ndiswrapper -i /home/pnp/Wireless\ Network\ Driver\ Realtek/RTL8187B/WINXP/net8187b.inf

The reason for the backslashes is because of the spaces in the folder name. If you don't get any errors, then check to see if it is properly installed with this command

ndiswrapper -l

If everything looks good, then enter these commands, one at a time (as root):

ndiswrapper -m
ndiswrapper -ma
ndiswrapper -mi

Now it is best to reboot, and then configure the wireless as a network card.
__________________"

Everything appears to be installed but wlan0 is not showing up at all. Only thing that works is my ethernet connection. 

If anyone could help a newbie out it would be greatly appreciated. Thank you for your time in reading this post. Have a nice day everyone.

---

### Post by pytheas22 on 2008-08-04
Sounds like a problem with ndiswrapper not being loaded.  Please open a terminal (Applications>Accessories menu), type in these commands (one line at a time) and post the output so that we can figure out what's going on (you can copy text from the terminal by highlighting it, right-clicking and selecting copy; paste into Firefox with control-v):
```

lsmod | grep ndiswrapper
lshw -C Network
ndiswrapper -l
uname -n
```

---

### Post by cdtech on 2008-08-04
"iwconfig" would be a good sign to see if the wireless network is up.

**P.S.**
bumping a thread does not help those who try to answer the "unanswered post".

---

### Post by ArcticWolfy2882 on 2008-08-05
This is what I get
_______________________________________________________
foxy@foxy-laptop:~$ lsmod | grep ndiswrapper
foxy@foxy-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:df:90:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
foxy@foxy-laptop:~$ ndiswrapper -l
net8187b : driver installed
foxy@foxy-laptop:~$ uname -n
foxy-laptop
foxy@foxy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

foxy@foxy-laptop:~$

---

### Post by pytheas22 on 2008-08-05
Thanks for the information.  I think you have the wrong Windows driver installed into ndiswrapper.  Please post the output of these commands so that we can figure out exactly what to do:

```

lsusb
uname -m
```

Sorry to have to ask for output a second time, but once I see that stuff, it should be easy to list steps to get the wireless working.

---

### Post by ArcticWolfy2882 on 2008-08-07
I apologize for the delay. hectic schedule. here is the feedback
_______________________________________________________________

foxy@foxy-laptop:~$ lsusb
Bus 007 Device 003: ID 1516:8628  
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
foxy@foxy-laptop:~$ uname -m
x86_64

________________________________________________________________

Hopefully this will suffice

---

### Post by bobnutfield on 2008-08-07
This chipset (I have it and it works with the Win98Drivers very well), is for some odd reason an internal USB.  Here is a link that suggests a way to get it working.  I used Ndiswrapper with the Win98 driver.  If you cannot get it going with this link, post back and I will walk you through what I did.

[http://ubuntuforums.org/showthread.php?t=839108&highlight=Realtek+8187b]("http://ubuntuforums.org/showthread.php?t=839108&highlight=Realtek+8187b")

Please note that this thread uses a different means to get this chipset working.  Both work, but I preferred Ndiswrapper.

---

### Post by appi2012 on 2008-08-07
Try typing:
```
sudo modprobe ndiswrapper
```
That should work. To make it start on boot up. type this:
```
gksu gedit /etc/rc.local
```
and add:
"modprobe ndiswrapper" (without quotes) after the blue comments (before "exit 0"

---

### Post by pytheas22 on 2008-08-07
> This chipset (I have it and it works with the Win98Drivers very well), is for some odd reason an internal USB. Here is a link that suggests a way to get it working. I used Ndiswrapper with the Win98 driver. If you cannot get it going with this link, post back and I will walk you through what I did.

[http://ubuntuforums.org/showthread.p...=Realtek+8187b](http://ubuntuforums.org/showthread.p...=Realtek+8187b)

Please note that this thread uses a different means to get this chipset working. Both work, but I preferred Ndiswrapper.

Yes, since you have a Realtek chipset, that tutorial should get it installed using native drivers.  You should remove ndiswrapper first with the command:
```

sudo apt-get remove --purge ndiswrapper
```

Or, if you prefer to use ndiswrapper instead of the native drivers (either way should work equally well), run these commands it it should make the card work:
```

sudo ndiswrapper -r net8187b
wget http://download2us.softpedia.com/dl/16304d451d73a109dc21674670ef15e3/489b401a/300025580/drivers/network/win_8187B_6.1063_RtlWlan_402.zip
unzip win_*
cd Realtek*/VistaX64
sudo ndiswrapper -i net8187b.inf
sudo ndiswrapper -a 0bda:8197 net8187b
```

I think that should work.  A possible issue is that your system is 64-bit, so you need to use 64-bit drivers.  All of the tutorials that I found for your card (like this [one]("http://ubuntuforums.org/showthread.php?t=839108&highlight=Realtek+8187b")) are written for 32-bit systems and say to use the Windows 98 drivers, but obviously there are no Windows 98 64-bit drivers, so we have to use the Vista ones.  But I think that it should still work, so give it a try if you don't want to use the native drivers.

---

### Post by bobnutfield on 2008-08-07
If the OP has a 32bit system and opts for Ndiswrapper with the Win98 driver, please note that there is a required edit to the .inf file prior to installing it to get it to work.  I will provide that edit if the OP so desires.

---

### Post by pytheas22 on 2008-08-07
> If the OP has a 32bit system and opts for Ndiswrapper with the Win98 driver, please note that there is a required edit to the .inf file prior to installing it to get it to work. I will provide that edit if the OP so desires.

Thanks for pointing this out, but he does have 64-bit, as the output below shows:

```
foxy@foxy-laptop:~$ uname -m
x86_64
```

Also from what I read, if you don't want to edit the .inf file, you can just force ndiswrapper to use the Windows driver with the -a argument, which I included in the instructions above.  So it should work fine without having to edit the .inf stuff.

---

### Post by ArcticWolfy2882 on 2008-08-07
Just tried the whole shebang in you link and the others to follow. Unfortunately, like a rock and a hard place, my wifi is still a no go. 

I followed what was done here

[http://ubuntuforums.org/showthread.php?t=839108&highlight=Realtek+8187b](http://ubuntuforums.org/showthread.php?t=839108&highlight=Realtek+8187b)

and then i followed what was done here

[http://ubuntuforums.org/showthread.php?t=792092&highlight=rtl8187b](http://ubuntuforums.org/showthread.php?t=792092&highlight=rtl8187b)

---

### Post by bobnutfield on 2008-08-07
The second post is the method I would have walked you through.  It worked for me.  What do you get when you type:

> modprobe ndiswrapper

If you followed all of the other steps, ndiswrapper should be listed when you type:

> sudo lsmod 

---

### Post by ArcticWolfy2882 on 2008-08-07
I took the method you mentioned for the inf file for the 98 driver and applied it to the vista64 inf file and so far hardware is present but the network settings does not show anything other then wired connection or point to point

---

### Post by bobnutfield on 2008-08-07
Ah, I am running 32bit Ubuntu.  I'm afraid I have never tried on a 64bit system, so I cannot testify to how it would work.  It deifinitely works on 32bit, as I have used the same method on four different distros, all successfully.  I will talke a look and see what I can find about it and post back.  Hopefully, someone else who has successfully gotten the 8187B on 64bit will chime in.

---

### Post by ArcticWolfy2882 on 2008-08-07
I'll attempt to tinker around with it. I appreciate your help and everyone else who gave me feedback if they are reading this post.

---

### Post by bobnutfield on 2008-08-07
I have just read a number of posts in this forum and in others, and unfortunately, they all say that this particular chipset will only work with 32bit systems in Linux.  Attempting to use a 64bit driver hangs the system.

---

### Post by ArcticWolfy2882 on 2008-08-07
So would I have to use a different driver or would i have to move to xubuntu?

---

### Post by pytheas22 on 2008-08-07
> I have just read a number of posts in this forum and in others, and unfortunately, they all say that this particular chipset will only work with 32bit systems in Linux. Attempting to use a 64bit driver hangs the system.

That may be true (I didn't see those posts, do you have any links?), but let's at least make sure that it will cause problems (if it does, it shouldn't break anything, so don't worry about running these commands).  Run this code and see what happens; please post the output:
```

sudo rmmod ndiswrapper
sudo modprobe --verbose ndiswrapper
sudo ifconfig wlan0
dmesg | grep -e ndis -e wlan
iwlist scan
```

If this still doesn't work, the native driver approach should...

---

### Post by ArcticWolfy2882 on 2008-08-07
foxy@foxy-laptop:~$ sudo rmmod ndiswrapper
[sudo] password for foxy: 
foxy@foxy-laptop:~$ sudo modprobe --verbose ndiswrapper
insmod /lib/modules/2.6.24-20-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko 
foxy@foxy-laptop:~$ sudo ifconfig wlan0
wlan0: error fetching interface information: Device not found
foxy@foxy-laptop:~$ dmesg | grep -e ndis -e wlan
[   38.988863] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.419146] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   39.419159] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   39.419166] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   39.419172] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   39.419179] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   39.419187] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   39.419194] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   39.419200] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   39.419227] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   39.419240] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   39.419247] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   39.419259] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   39.419273] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   39.419282] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   39.419289] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   39.419295] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   39.419301] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   39.419310] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   39.419315] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   39.419319] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   39.419323] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
[   39.419832] ndiswrapper (load_wrap_driver:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[   39.419930] usbcore: registered new interface driver ndiswrapper
[ 2404.823547] usbcore: deregistering interface driver ndiswrapper
[ 2404.824138] ndiswrapper (ntoskernel_exit:2708): object ffff810028516830(2) was not freed, freeing it now
[ 2405.184560] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2405.450072] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 2405.450086] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
[ 2405.450474] ndiswrapper (load_wrap_driver:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[ 2405.450511] usbcore: registered new interface driver ndiswrapper
[ 2442.490796] usbcore: deregistering interface driver ndiswrapper
[ 2442.491178] ndiswrapper (ntoskernel_exit:2708): object ffff8100280ce830(2) was not freed, freeing it now
[ 2442.514916] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2442.526137] usbcore: registered new interface driver ndiswrapper
[ 2516.907923] usbcore: deregistering interface driver ndiswrapper
[ 2516.931759] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2517.191848] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 2517.191865] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
[ 2517.193255] ndiswrapper (load_wrap_driver:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[ 2517.193307] usbcore: registered new interface driver ndiswrapper
[ 2575.957483] usbcore: deregistering interface driver ndiswrapper
[ 2575.957895] ndiswrapper (ntoskernel_exit:2708): object ffff8100281bec30(2) was not freed, freeing it now
[ 2575.981572] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2575.992536] usbcore: registered new interface driver ndiswrapper
[ 2703.584925] usbcore: deregistering interface driver ndiswrapper
[ 2716.266202] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2716.277480] usbcore: registered new interface driver ndiswrapper
foxy@foxy-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

foxy@foxy-laptop:~$

---

### Post by bobnutfield on 2008-08-07
> **pytheas22 said:**
> That may be true (I didn't see those posts, do you have any links?), but let's at least make sure that it will cause problems (if it does, it shouldn't break anything, so don't worry about running these commands).  Run this code and see what happens; please post the output:
```

sudo rmmod ndiswrapper
sudo modprobe --verbose ndiswrapper
sudo ifconfig wlan0
dmesg | grep -e ndis -e wlan
iwlist scan
```

If this still doesn't work, the native driver approach should...

On page 6 of the thread that you followed, two users state that only the 32bit version of Ubuntu will work with these windows drivers.  However, one poster did write this:

>  Re: HOWTO: Get RTL8187B (ID: 8197) Working. Step by Step
After tinkering with the driver some more I found that I can get the driver to install properly in ndiswrapper if I add the line

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

under the "IDs for X64" section as well.
I can't believe it took me so long to figure that out since I'm running 64 bit version of Hardy!

(Also, I used the X64 driver to get it to work.)
icdelg is offline Report Post   	Reply With Quote

It may be worth reading a little more into that thread.

---

### Post by ArcticWolfy2882 on 2008-08-07
That is the modification I have been making to all the appropriate *.inf files

---

