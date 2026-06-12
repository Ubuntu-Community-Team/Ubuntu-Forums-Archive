---
title: "Looking for small ubuntu variants frugal install"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by nooby on 2008-07-29
Search gave nothing so hope it is ok to ask here. 

I'm fond of small live distros that can work from cd or dvd 
or frugal install on a one partition hd. I prefer to not have 
to do a partition. 
Xfce look promising. Only that one make them small enough? 

so far I have set up these linuxes in my menu.lst


title Puppy Linux 4.00
kernel (hd0,0)/puppy400/vmlinuz PMEDIA=satahd PDEV1=sda1 psubdir=puppy400 keyb=se 
initrd (hd0,0)/puppy400/initrd.gz
boot

title Nimblex 2008
root (hd0,0)/nimblex
kernel /nimblex/vmlinuz-nx08 from=/mnt/hda1/nimblex/NimbleX-2008.iso ramdisk_size=6666 root=/dev/ram0 rw vga=791 autoexec=telinit~4 changes=/nimblex.data
initrd /nimblex/initrd-nx08.gz 

title Slax 2007
root (hd0,0)/slax
kernel /slax/vmlinuz from=/mnt/hda1/slax/slax-6.0.7.iso ramdisk_size=6666 root=/dev/ram0 rw vga=791 autoexec=telinit~4 changes=/slax.data
initrd /slax/initrd.gz 


title SliTaz cooking
  kernel (hd0,0)/boot/bzImage rw root=/dev/null vga=normal 
  initrd (hd0,0)/boot/rootfs.gz



title Windows XP SP2 Boot on HD 0
	rootnoverify (hd0,0)
	chainloader +1
	boot

So now I want to add a small Ubuntu. 

There has been rumor that somebody made a less than 
250MB version of ubuntu. not sure how it differ from 
xubuntu 

Nooby.

PS yes me have tested pclinuxos and kanotix and knoppix 
and many others. DSL didn't get my ethernet card going. 

I want a small ubuntu to compare with the linux versions 
I already have.

---

### Post by Bachstelze on 2008-07-29
Why not just install a base Ubuntu and then add the software you want. I didn't test it, but I believe you might be able to go under 250 MB thazt way.

---

### Post by eightmillion on 2008-07-29
You might install ubuntu server edition and a window manager like openbox, fluxbox, or icewm. Searching for ubuntu minimal install should point you in the right direction.

---

### Post by pedrogent on 2008-07-29
Not Ubuntu but I reckon Arch might be up your alley too. Give it a shot some time.

---

### Post by bumanie on 2008-07-29
Puppy linux or damn small linux may be what you're looking for - they are both > 100mb

---

### Post by snowpine on 2008-07-29
The smallest-ISO Ubuntu distros that I am aware of are Fluxbuntu (ISO ~300mb but it's not a Live CD) and Crunchbang Lite (ISO ~400 and it is a LiveCD). Your best bet may be to build what you want using the minimal install, then make your own Live CD using Remastersys or something similar. 

Honestly, Ubuntu is not designed to do the live cd/frugal install thing as well as DSL or similar. You will get the best performance with any distro of Ubuntu if you do a full hard drive install.

If you are just looking for a slightly faster Ubuntu that won't give you any headaches, I recommend Xubuntu.

---

### Post by LowSky on 2008-07-29
Ubuntu has alot of extras intalled right from the start. You could just go through and remove most of the extra packages you'll never use. You can also make a smaller footprint install with Debian and use a GUI like IceWM.

---

### Post by Anzan on 2008-07-29
CrunchBang Linux is Ubuntu with an Openbox configuration. There is also a lighter version.

---

### Post by nooby on 2008-07-29
Thanks for all answers. 

Was much harder than I thought to find a small "live" cd version of Ubuntu. 

Flux fooled me. I didn't realize that it was an install iso 
So it was more good luck that made me aware that it started 
to look for how resize my HD and start doing partition and 
I hit ctrl+alt+delete and restart computer to avoid it started 
to mess up my computer install. 

So disappointing. :) 

Well I found one small one IceUbuntu. And it allowed one to 
chose if one wanted a live or install. So I tool live and 
wow what a long time it took I though it had stalled or hanged 
but suddenly it asked for user name. 

Sadly it had no flash installed and I was not intelligent enough 
to get it mount my HD so I have not looked at how it deal with jpg or rm files. 


Youtube worked and it was good at recognizing my hardware. 
Ethernet and sound was right out of the box. 

Hard to understand compared to Puppy and Nimblex. These two 
are very good compared to full WUBI install of Ubuntu 8.04 
and IceUbuntu 2.3 which are the two ubuntus me have most experience of now. 

DSL failed to get my ethernet card. I never got out on internet ¨with it. 

Arch failed too. Kanotix and Knoppix and PCLinuxOS allof these 
failed too to get my Marvell Yulon Ethernet card, Computer are 
from 2004 or 2005. I bought it 2005 it has Intel Chipset 915.

---

