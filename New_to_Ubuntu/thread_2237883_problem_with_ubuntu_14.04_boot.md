---
title: "problem with ubuntu 14.04 boot"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by projjwal-das on 2014-08-04
Hi, I'm a newbie in Ubuntu. I've installed ubuntu 14.04 in my laptop, which has the below config --
Intel(R) Core(TM)2 CPU, T5200  @ 1.60GHz
2 GB RAM, 160 GB HDD

Below is the space allocation (and the current status) that I did during the ubuntu installation --

root - 31 GB - 26 GB free (15.3% full)
swap - 4.1 GB
var - 3.1 GB - 1.8 GB free (43% full)
tmp - 3.1 GB - 2.9 GB free (4% full)
boot - 15 GB - 15 GB free (3.1% full)
home - 104 GB - 61 GB free (40.8% full)

Does this space allocation sound good?

This linux installation was working fine until last week. But now, whenever I'm trying to boot it, I see a series of "^[[5~" over my screen and the screen starts to flash. However, I'm able to boot the same through ubuntu recovery mode. 
I've also tried to install a fresh version of ubuntu, but whenever I put the live cd, the screen starts to flash. I wonder if it has anything to do with my graphics. I've done fair bit of google, but to no avail. Any help will be highly appreciated. :)

---

### Post by Impavidus on 2014-08-04
The partitions are OK, in the sense that this will work reliably. It's not ideal though. Most people don't create separate /var and /temp (although there may be cases where it's good to have them) and you only need /boot in case of LVM or full disk encryption and even then 300MB should do.

It seems you have a problem with the graphics driver. Which graphics card have you got?

---

### Post by projjwal-das on 2014-08-04
I don't have any! :-|

---

### Post by Bashing-om on 2014-08-04
> **projjwal-das said:**
> I don't have any! :-|

No ??
show us the output of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

``` to see what is going on here !

[INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-08-04
> **Impavidus said:**
> Most people don't create separate /var and /temp (although there may be cases where it's good to have them) and you only need /boot in case of LVM or full disk encryption and even then 300MB should do.

^^^
This.

I will add that there is no need for a 4Gb /swap as you have 2Gb RAM. 2Gb is fine even if you have more RAM that that. Standard. If use hibernation regularly, then you would want it the same size as your installed RAM. 2Gb. 

When you put the install disk in the screen starts to flash? You mean when you boot from it and try to install it doesn't get to the options 'Try Ubuntu' 'Install Ubuntu', but goes directly to a flashing screen?

Good luck.

---

### Post by projjwal-das on 2014-08-05
> **Bucky Ball said:**
> ^^^

When you put the install disk in the screen starts to flash? You mean when you boot from it and try to install it doesn't get to the options 'Try Ubuntu' 'Install Ubuntu', but goes directly to a flashing screen?

Good luck.

Yes, it opens the loading screen like below..
[http://3.bp.blogspot.com/_PtyHEChBKZw/S9ohLgAFKhI/AAAAAAAAf8w/pfD9bNegtig/s400/10.jpg](http://3.bp.blogspot.com/_PtyHEChBKZw/S9ohLgAFKhI/AAAAAAAAf8w/pfD9bNegtig/s400/10.jpg)

and the screen starts to flash, and it remains in the same state, and doesn't do anything else.

---

### Post by Bashing-om on 2014-08-05
projjwal-das; Morning !

How 'bout we back up, regroup - cover our bases:
Did you verify the .iso's integrity ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
How did you burn the image, and from what operating system ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
And the last check - Does the image boot to "try ubuntu" and "check disk for defects"?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

If all those check, next is to look at the hardware.

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by projjwal-das on 2014-08-05
> **Bashing-om said:**
> No ??
show us the output of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

``` 



Here are the outputs --

projjwal@projjwal-HP-530-Notebook-PC:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30d5]
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30d5]
projjwal@projjwal-HP-530-Notebook-PC:~$ sudo lshw -C display
[sudo] password for projjwal: 
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GSE Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list
       configuration: latency=0
       resources: memory:f0400000-f047ffff ioport:3000(size=8) memory:e0000000-efffffff memory:f0480000-f04bffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f057ffff

---

### Post by Bashing-om on 2014-08-05
projjwal-das; The news is not all bad:
From:
> 
Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)

We know now what the graphics are -> But, but
> 
*-display:0 UNCLAIMED ; configuration: latency=0

We also know that no graphics driver is loaded.

As the case is, I know nothing about Intel graphics and those who do have that experience will have to advise on what it will take to get a driver loaded ( integrated graphics, yuk ).

[INDENT][INDENT]just a bit of progress
[/INDENT][/INDENT]

---

### Post by projjwal-das on 2014-08-07
Thanks for pointing out the problem at least. I'll try google as well. :)

But just a curious question, how did it perform normally until last week then? :confused:

---

### Post by oldfred on 2014-08-07
Intel's driver should just be loaded. The only one is the open source version.

On my system:
      ```
         *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
....
             configuration: [COLOR=#ff0000]driver=i915[/COLOR] latency=0


```    

It does look like they have install specific versions. Not sure of differences as it has just installed with my system.

xserver-xorg-video-intel-lts-trusty
xserver-xorg-video-intel

---

### Post by fkkroundabout on 2014-08-07
yes i always have the the flashing screen covered pixels of random colours with an ATI 6670 - i always have to use nomodeset [hit the F buttons when the ubuntu logo pops up, then F6 when that option appear] to boot and install, then change graphics driver after

---

