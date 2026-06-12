---
title: "Newbie with a few problems"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by d3rek on 2008-08-30
hi, completely new to ubuntu (and linux in general).

I installed it on an old gateway pc someone gave to me.  I've been having a few problems.

one is the internet connection.  At first it wasn't recognizing the nic at all.  I got that fixed, then it wouldn't connect.  I tried some things and now it's not recognizing the card again.  i'm trying to connect at work through the lan.

the other problem is sometimes if it sits too long it just freezes completely.  is this a motherboard or hard drive problem?

please help.

---

### Post by Crafty Kisses on 2008-08-30
What are your system specs?

---

### Post by gmxgeek on 2008-08-30
What are the make and model of the network card? Most hardware in ubuntu "just works"

Also, are you using a proxy by chance?

---

### Post by d3rek on 2008-08-30
pentium 4 
256mb ram
nic: 3com 3c905c

I added 

alias eth0 3c905c
alias eth1 3c905c

to /etc/modules

and

auto eth0
iface eth0 inet dhcp

auto eth1 
iface eth1 inet dhcp

this got the icon up in the top right to show a connection and the weather icons showed up, but then I couldn't connect to any web pages...now it's back to not recognizing the nic

---

### Post by gmxgeek on 2008-08-30
Can you post the output of lspci please?

Also of
```

cat /etc/network/interfaces

```

---

### Post by d3rek on 2008-08-30
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
02:0b.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:0d.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)

and no, no proxy

---

### Post by gmxgeek on 2008-08-30
okay, so it looks like it sees your NIC just fine. Can you post the output of the file mensioned above?

---

### Post by d3rek on 2008-08-30
oh and cat /etc/network/interfaces: 

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

---

### Post by gmxgeek on 2008-08-30
All right. Can you launch up Network Manager and see if the device is listed there?

---

### Post by d3rek on 2008-08-30
It isn't.

---

### Post by gmxgeek on 2008-08-30
I am going to assume you haven't installed the drivers for it yet, is that correct?

Also, try deselecting Enable Networking, and then reselecting it. There is an old bug that this sometimes fixes.

---

### Post by d3rek on 2008-08-30
No, I haven't.

---

### Post by gmxgeek on 2008-08-30
Okay, a few more output stuff :P

can you post
```

ifconfig -a

```

---

### Post by d3rek on 2008-08-30
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102100 (99.7 KB)  TX bytes:102100 (99.7 KB)

```

---

### Post by gmxgeek on 2008-08-30
Now that is problematic. Looks like it isn't loading your card, not just a null connection. So, we know that your card is detected, from lspci, but not activated, and doesn't show in Network Manager.

My advice would be to track down some drivers for the card and try to install them. I checked the repos, but I don't think they are there. Perhaps try the 3com website?

[http://www.3com.com/products/en_US/downloadsindex.jsp](http://www.3com.com/products/en_US/downloadsindex.jsp)

---

### Post by d3rek on 2008-08-30
Ok, I'll give that a try.  not completely sure how to install it from the tar.gz and the instructions aren't for Ubuntu.   

The weird thing is that it was recognized, showed up in network manager...and now it isn't.

---

### Post by gmxgeek on 2008-08-30
```

tar -xzf filename.tar.gz

```

that will extract it from the tarball, and inside should be some sort of executable or source

I'll help you install if you like.

---

### Post by d3rek on 2008-08-30
Thanks so much.

yeah, I extracted it to the desktop.

there's a file: install3c90x

when I click it, nothing happens.

---

### Post by gmxgeek on 2008-08-30
try opening a terminal, then cd to that directory then type
```

chmod +x ./install3c90x
sh ./install3c90x

```

That will make it executable, and then run it for you

---

### Post by d3rek on 2008-08-30
after sh ./install3c90x it returns: 

45:  Syntax error: end of file unexpected (expecting "fi")

---

### Post by gmxgeek on 2008-08-30
see if cat of that file outputs anything. That looks like an error in the driver (expecting fi means that someone forgot an end to their if statement before they ended the script). Where did you get this file from?

---

### Post by d3rek on 2008-08-30
from the 3com website: [http://support.3com.com/infodeli/tools/nic/linuxdownload.htm](http://support.3com.com/infodeli/tools/nic/linuxdownload.htm)

```
#!/bin/csh -f

if (`id -u` != 0) then
    echo "You must have root priveleges to install the 3c90x driver module."
    echo "Installation of 3c90x driver module failed."
    exit 1
endif

set kernel_release=`uname -r`

echo "Attempting to install the $kernel_release version of the 3c90x" 
echo "driver module."
echo "You are running the $kernel_release version of kernel release..."

set module_dir = /lib/modules/$kernel_release/net


if (! -d i486/$kernel_release) then
    echo "The 3c90x driver module was not built for this kernel release."
    echo "You will need to compile the driver yourself."
    echo "Installation of 3c90x driver module failed."
    exit 2
endif

if (! -d $module_dir) then
    echo "Module directory $module_dir not found; can't install."
    echo "Installation of 3c90x driver module failed."
    exit 3
endif

echo "Found modules directory $module_dir"
echo "Copying the driver module into the modules directory."
cp i486/$kernel_release/3c90x.o $module_dir

echo "Updating module dependencies..."
/sbin/depmod -a
if ($status != 0) then
    echo "Update of module dependencies failed... perhaps you've updated your system?"
    echo "You may need to compile the driver yourself."
    echo "Installation of 3c90x driver module failed."
    exit 4
endif

echo "Installation of 3c90x driver module was successful."

```

---

### Post by gmxgeek on 2008-08-30
Okay, now, i am no expert in bash scripts, but i'm pretty sure those endif's should be fi's, so try 
```

gedit ./install3c90x

```

and change all the endif's to fi, and then save and try running it again

---

### Post by d3rek on 2008-08-30
hahah. this is crazy...but I'm learning a lot.  it says 'you will need to compile the driver yourself'.

---

### Post by gmxgeek on 2008-08-30
Yay! :)

Okay, look on their website for a source code package. We will build this bad boy ourselves.

---

### Post by d3rek on 2008-08-30
these are the files in the dir (other than the install and readmes):

i486(folder)
3c90x.c
3c90x.h
compile_SMP
compile_UP
patch-2.0.36
patch-2.2.5

---

### Post by gmxgeek on 2008-08-30
listings of complile_SMP and compile_UP?

---

### Post by d3rek on 2008-08-30
I ran the commands in both, they both return a TON of errors in 3c90x.h & 3c90x.c!

I might just look around here for a different nic.

---

### Post by gmxgeek on 2008-08-30
I would suggest it if you can't get some drivers to install. I would recommend a linksys, since they usually work straight out of the box in all cases i have had. I haven't had too much luck with 3com myself.

So, see if you can find some working drivers, and if not, i'd go with a new nic

---

### Post by d3rek on 2008-08-30
Thank you so much for your help.  If nothing else I learned a bunch of commands!

---

### Post by gmxgeek on 2008-08-30
Any time. Just keep trying, and ALWAYS ask for help if you need it. I'm pretty new to ubuntu myself, so sorry i couldn't be more help.

---

### Post by eru777 on 2008-08-30
Try hard resetting the modem too . (if it's ethernet connected)
BY that I mean press the reset button, hold it for 10 seconds, release any cables connecting to it, keep on pressing for another 10 seconds, then leave for 5-10 minutes by itself and try again (u have to make the config/username etc from scratch, but thats what fixed my problem when the card did not see the modem from ethernet)

---

### Post by d3rek on 2008-08-30
thanks eru77.  I ended up just swapping it out with another one I lifted from an old computer at work.  It was the same exact model but from 2000 instead of 1998.  It worked perfetly, no problem.

---

### Post by gmxgeek on 2008-08-30
glad to hear you got it working :)

---

