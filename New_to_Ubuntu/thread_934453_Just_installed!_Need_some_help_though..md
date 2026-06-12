---
title: "Just installed! Need some help though."
date: 2008-09-30
forum: New to Ubuntu
---

### Post by tjkoch on 2008-09-30
Hey everyone, 

After trying for a while I was able to finally install Ubuntu successfully on my computer. I am having 2 problems though which I need to correct, one is a networking problem.

1. I cant go online while in Ubuntu? I thought it would setup my networking automatically but it didn't. Tried browsing around see if there was any auto network setup but there wasn't.

Anyway I loaded back into Windows and went into my Router to find some info. I am using Verizon Fios btw. Anyway I got all my info that it looked like I would need, ip, dns, gateway, netmask, and mac address. I booted back into Ubuntu and tried typing everything in manually, I did so but nothing happened. I checked my Bios to see if I have something disabled which shouldn't be but that didn't help either. Not really sure what I need to do to get online.


2. Is there I way I can avoid the bootloader screen and have the machine automatically go into Vista every time, and if I want to go into Ubuntu I will push a key during bootup while it is displaying my computer & bios info?

---

### Post by waspbr on 2008-09-30
are you trying to access a wireless network or a wired one?

---

### Post by m10 on 2008-09-30
u may use ur live cd to repartition/change size of it
when booted go to system->administration->Partition editor

you may also install gparted (the Partition editor on the lve cd) on ur installed ubuntu either through synaptics or via terminal 
```
sudo apt-get install gparted
```

---

### Post by porchrat on 2008-09-30
You don't necessarily have to give it back to Vista.  You can create a new partition using a program called gparted which is available in the repositories, get it using synaptic package manager (go to system ---> administration ---> synaptic package manager.

If you create a NTFS partition then it should be readable by both vista and ubuntu...meaning you can put documents etc. in there and both operating systems can read and write to it.

Hope that helps.

As for the networking issue you need to be a little more specific about what you are trying to do...wired/wireless, laptop/desktop.  Wireless connections are often a problem with Ubuntu and lucky for you there are plenty of guides.

---

### Post by Tatty on 2008-09-30
2.  You need to boot into a ubuntu liveCD then go to System->Administration->GNOME Partition Editor.

This will load Gparted from where you can edit your partitions.  Note that you cannot alter the partitions on a mounted drive, which is why you must boot into a liveCD.

Make sure you backup everything first just in case of disaster!  Also scandisk and then defrag your windows partition 3 times beforehand.

3.  You just need to edit your grub, can you open a terminal and post the output of:

```
cat /boot/grub/menu.lst
```

---

### Post by m10 on 2008-09-30
as for the bootloader u can
in a terminal:
```
sudo gedit /boot/grub/menu.lst
```

the text editor should come up

find the section similar to this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```
change that last 0 according to ur windows position in ur boot menu
(maybe 4 ?)


note: that is the first thing that comes to mind.. though there may be a better solution..

---

### Post by Tatty on 2008-09-30
> **m10 said:**
> as for the bootloader u can
in a terminal:
```
sudo gedit /boot/grub/menu.lst
```


Just a quick correction, for graphical apps such as gedit you should use gksu, so:
```
gksu gedit /boot/grub/menu.lst
```
:)

---

### Post by tjkoch on 2008-09-30
Ok I fixed my partitioning problem so I editted that out of my initial post. I also changed my initial question about the bootloader, I guess I wasn't specific enough. However my main problem is still here. :(

I am trying to connect using a wired connection. I am using Verizon Fios which pretty much forces you to use their router because you can't connect directly to their modem.

I was browsing through things and I have no Network Connections setup. I also have no Network hardware setup either. I tried installing an ethernet connection on eth0 and eth1 but there is nothing there. I am using a Asus p5q-pro motherboard with onboard ethernet. How do I find out what my ethernet device address is? 

Am I going about this all wrong? Is there another better way to this, like some kind of program that will autofind and install it? Why wasn't it found during my installation? Anyway guess I'm just a bit upset because I thought install would be easy, hehe.

---

### Post by Tatty on 2008-09-30
For the bootloader, what you want can be done, please open a terminal post the output of:
```
cat /boot/grub/menu.lst
```

---

### Post by tjkoch on 2008-09-30
Tatty:

default=1
timeout=5
splashimage=(hd1,1)/grub/splash.xpm.gz
hiddenmenu
title Linux
   root (hd1,1)
   kernel /vm-linuz...... rhgb quiet
   initrd /initrd.....
title Vista
   rootnoverify (hd0,0)
   chainloader +1

I didn't type everything out because I'm on a laptop looking at it on my desktop. If you need full kernel info etc let me know.

---

### Post by tjkoch on 2008-09-30
To give you guys a bit more info about my Internet connection problem since I'm looking at my desktop.

My Network Configuration shows No Devices, or Hardware setup. My DNS and Hosts Tabs are also blank.

I tried adding an ethernet device on eth0 and eth1 but I am just guessing with all of this. Anyone know what might be wrong?

---

### Post by mikewhatever on 2008-09-30
Can you post the output of the following to show us your network card:
> sudo lshw -C network

Is your router connected to the computer via an ethernet cable or a usb one?

---

### Post by tjkoch on 2008-09-30
Mikewhatever: I'm connected through an ethernet cable.

I tried doing that sudo command but for some reason it isn't accepting my sudo password. Is it the same as my root password? When I type 'su' and put in my password it works but not when doing your command?

---

### Post by gpsmikey on 2008-09-30
I think you are going to have to find drivers for that ethernet controller on the motherboard.  Check the Asus site for linux drivers -- seems to me I had to load drivers for windows also for that board to be able to talk to the world.

mikey

---

### Post by Tatty on 2008-09-30
> **tjkoch said:**
> Tatty:

default=1
timeout=5
splashimage=(hd1,1)/grub/splash.xpm.gz
hiddenmenu
title Linux
   root (hd1,1)
   kernel /vm-linuz...... rhgb quiet
   initrd /initrd.....
title Vista
   rootnoverify (hd0,0)
   chainloader +1

I didn't type everything out because I'm on a laptop looking at it on my desktop. If you need full kernel info etc let me know.

Ok, since you obviously cant post the whole file now ill just explain:

back up yuor current menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

load menu.lst for editing:
```
gksu gedit /boot/grub/menu.lst
```

scroll down until you see some entries which look similar to this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f865e5d8-65fc-4b7b-8e58-17d737d61600 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Count down each one of those entries (starting at 0) until you find an entry for windows.

Remember that number you counted up to then go back to the top of the file and find this:
```
default		0
```

now just change that number to the number of your windows grub entry.  It should now boot into windows by default.

If you read down you also find an option there for how long you want to wait at the grub screen, and an option to hide the grub menu.

---

### Post by mikewhatever on 2008-09-30
> **tjkoch said:**
> Mikewhatever: I'm connected through an ethernet cable.

I tried doing that sudo command but for some reason it isn't accepting my sudo password. Is it the same as my root password? When I type 'su' and put in my password it works but not when doing your command?

Etherneet is a better way, one thing less to worry about.
The password should be the one you've chosen during the installation. Not sure why it doesn't work with sudo. Did you get your card's info?

---

### Post by tjkoch on 2008-09-30
I found some Linux drivers on the Asus site for this mobo. Do I install them the same way I flash my Bios or is there another method? I hope that will do the trick...

Any other ideas what can be wrong?

---

