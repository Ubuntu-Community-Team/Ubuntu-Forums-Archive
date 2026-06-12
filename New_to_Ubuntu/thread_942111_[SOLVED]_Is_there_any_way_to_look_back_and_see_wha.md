---
title: "[SOLVED] Is there any way to look back and see what kernels I've used?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Papa-san on 2008-10-08
I know this is probably a really stupid question, but I am having a HUGE number of problems since I did an update or upgrade a while back... I thought at the time it was an upgrade, but the only 2 kernels listed in my grub are 8.04 the top one ends in number 16 and the second one ends with 14.

Is there any way I can look back and see what modifications I have made and when? Specifically, I would like to know if I have had 7.10 on this system... 

(I really don't think I did, because I have 7.10 disks from Canonical, and the timing doesn't seem right...) I cannot find the disk I downloaded and burned to set up this system as a dual boot... 

I need to find out so I can re-install it: yet again I made the mistake of assuming that any bugs would have been worked out in the 5 months I waited after installing the initial Ubuntu OS...

---

### Post by drs305 on 2008-10-08
It is very unlikely you would still have the 7.10 kernels. However, what grub displays depends on settings. Although the default is to show all available kernels, you may have changed the settings to display only 2. 

You can see what kernels are available by looking in synaptic at "linux-image-2.6-xxxxxxx". Rather than regress, you might consider updating to a newer kernel. I believe the current general release kernel is -19. To update to the most recent recommended kernel, you can go to synaptic and choose "linux-image". It will install the current 'approved' one - you don't have to worry about the number designation.

I believe the 7.10 kernel version was 2.6.22.xx

---

### Post by kk0sse54 on 2008-10-08
You can try and update your kernel to the newest version and see if it helps with any of your bugs

---

### Post by Papa-san on 2008-10-08
I know that I installed whatever I downloaded, and that worked very well. I think the only other thing I did was this upgrade... 

My confusion comes from the fact that some of the things in the older kernel got changed to whatever the newer one has in it. (Meaning that the one that worked flawlessly for months now does not do so anymore... It has the same shared issues as the newer one...) My thought is that because I do in fact have my grub list set at 2, did it have to do an upgrade from say number 8 to number 14 before it could install 16...

---

### Post by drs305 on 2008-10-08
> **Papa-san said:**
> My confusion comes from the fact that some of the things in the older kernel got changed to whatever the newer one has in it. (Meaning that the one that worked flawlessly for months now does not do so anymore... It has the same shared issues as the newer one...) My thought is that because I do in fact have my grub list set at 2, did it have to do an upgrade from say number 8 to number 14 before it could install 16...

You grub list will chooses things such as the default OS or kernel to run, and how many you see. That is what the '2' designates - how many will be displayed on your screen. It won't remove or limit old or new kernels from your computer. However, when updating from gutsy to hardy any of the old gutsy kernels were almost certainly removed from your machine unless you made a backup.

If you really want the old version, gutsy will be supported for another 6 months (Apr 09) and you can get the download here:
[http://releases.ubuntu.com/7.10/]("http://releases.ubuntu.com/7.10/")

---

### Post by Papa-san on 2008-10-08
Well, anyways, I'll go to the '18' that is current and see what happens... I'll post the results when I have some!

EDIT:

Maybe I'm trying to do it wrong, but it doesn't seem to want to do it... I tried ```
sudo apt-get install linux-image
``` and it tells me that the newest image is installed. When I re-booted, the first one on my list was the 16. I also tried it through Synaptic (which shows #18), and though it acted like it did something, I got the same result...

---

### Post by Papa-san on 2008-10-10
> **C!oud said:**
> You can try and update your kernel to the newest version and see if it helps with any of your bugs

I've tried every imaginable method to do this, and it doesn't seem to work. What's the best way to do it?

---

### Post by smooth3006 on 2008-10-10
not to hijack your thread but isn't the newest kernel that was just released Linux 2.6.27 ? if so how can i install this, is it in the ubuntu update manager ?

---

### Post by Papa-san on 2008-10-10
My system is reporting that 2.6.24.16 is the newest and is currently installed... (However, I see that 2.6.26 is in the repositories, and though I have 'installed' it through both apt-get and Synaptic, I get the first one...

---

### Post by drs305 on 2008-10-10
> **Papa-san said:**
> My system is reporting that 2.6.24.16 is the newest and is currently installed... (However, I see that 2.6.26 is in the repositories, and though I have 'installed' it through both apt-get and Synaptic, I get the first one...

If you are sure it's installed do you select it from the grub menu or does it automatically start on boot? If the latter, it's possible menu.lst is set to keep the current (last) kernel instead of a new one. 

You can check the settings via gui after installing StartUp-Manager (see the link in my signature) or inspect the menu.lst manually to see which kernel it is selecting. StartUp-Manager is simpler to decipher.

To do that, generally you would find the line with "default  X" with X being a number. Starting at 0, count the number of 'titles' in the menu near the bottom (e.g  if "default 2", it would be the 3rd 'title' entry in the menu).

---

### Post by Papa-san on 2008-10-10
I already had startup manager. It only shows: 

Ubuntu 8.04 2.6.24-16 generic
Ubuntu 8.04 2.6.24-16 generic (recovery mode)
Ubuntu 8.04 2.6.22-14 generic
Ubuntu 8.04 2.6.22-14 generic (recovery mode)
Ubuntu 8.04 memtest86+
Windows Vista/Longhorn (loader)
Microsoft Windows XP Embedded
Last Used

Kernels to keep is set at three.

Here is the relevant portion of menu.lst: 
```
# ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root= ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=Uro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=U ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by drs305 on 2008-10-11
> **Papa-san said:**
> My system is reporting that 2.6.24.16 is the newest and is currently installed... (However, I see that 2.6.26 is in the repositories, and though I have 'installed' it through both apt-get and Synaptic, I get the first one...

First, confirm you are running hardy. You have kernels 2.6.24 and 2.6.22 both listed in your menu.lst. You can verify the kernel and version you are running with:
```

uname -r && lsb_release -a

```

The second thing to do is verify the kernel is installed. In synaptic, see which "linux-image-2.6.24-" are installed. -19 was the latest but -21 may have just been released. Any kernels installed will have the green tick box.

Alternatively, you can do a search in /boot to see which kernels reside there:
```

find /boot -name vmlinuz*

```

If you find a result such as "vmlinuz-2.6.24-19-generic", you could put this at the top of your menu.lst so it looked like this after backing up your menu.lst:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.11102008
gksu gedit /boot/grub/menu.lst

```

```

# ## End Default Options ##


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/**vmlinuz-2.6.24-16-generic** root= ro quiet splash vga=791
initrd		/boot/**initrd.img-2.6.24-16-generic**
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/**vmlinuz-2.6.24-19-generic** root=Uro single
initrd		/boot/**initrd.img-2.6.24-19-generic**

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=U ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root= ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=Uro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=U ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Once you have saved menu.lst, I would go back to StartUp-Manager and make sure you have the new kernel selected as the default. I would also strongly recommend you have the timeout set to a value which will allow you to inspect the menu so you can choose your previous kernel or recovery mode (i.e. don't have timeout set to 0).

---

### Post by Papa-san on 2008-10-11
OK, (thanks!)
```
john@john-1525n:~$ uname -r && lsb_release -a
2.6.24-16-generic
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy
john@john-1525n:~$ 
```
and```
john@john-1525n:~$ find /boot -name vmlinuz*
/boot/vmlinuz-2.6.24-16-generic
/boot/vmlinuz-2.6.22-14-generic
john@john-1525n:~$ 
```
So evidently, even though Synaptic told me it was installed, and apt-get said it (2.6.24-16-generic) was the most current image, I actually don't have 2.6.24-19-generic or -21) 
What would be an effective method of installing it?

My timeout is set to 10 seconds.

---

### Post by Papa-san on 2008-10-13
I looked in the options/settings for Synaptic, and found that it was set to NOT find kernel upgrades. I changed that, and immediately I was presented with 312 updates that had become available. 
Upon searching Synaptic, I now saw both 2.6.24-18 and 2.6.24.19 were available for installation. 

So I went ahead and marked -19 for installation. It went through the process and I re-booted. As it was doing so, I saw some errors as the text scrolled by, including that it couldn't find eth1 (my _old_ wireless).  Once it was all the way booted, I had no wireless, and iwconfig showed no wireless interfaces. Nor did it show the other 'new' one, 'wmaster0'. Here's iwconfig under -16:```
john@john-1525n:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Stonepile"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:C8:CE:62   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=79/100  Signal level=-55 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@john-1525n:~$ 

``` and here it is under -19: ```
john@john-1525n:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@john-1525n:~$
``` 


I re-booted back into -16 and went ahead with the other 311 updates. I am about ready to re-boot it again with all of those installed. I'll post the results...

---

### Post by Papa-san on 2008-10-13
So far it seems that the updates managed to work. 

Wireless is up and running. I have had it go through two screensaver/hibernate cycles successfully, so I believe I'll mark it solved.
(Seeing as how the only list seems to be what is currently installed and in the list in results from the command:```
find /boot -name vmlinuz*
```

---

