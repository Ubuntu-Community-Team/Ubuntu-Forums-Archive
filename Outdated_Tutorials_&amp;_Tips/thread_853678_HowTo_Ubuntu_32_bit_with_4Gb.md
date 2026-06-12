---
title: "HowTo Ubuntu 32 bit with 4Gb"
date: 2008-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by phico on 2008-07-08
Hi,

I have a macbook pro with 4Gb RAM. 

It was quite simple to make it a pure linux machine as this [http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)

But .. I really wanted to use those 4Gb because I plan to run some virtual machines ...

The solution was to use a 64 bit system .. but .. soon I noticed that 
I was 'downgrading' quite everything from 64 to 32 bit because of incompatibilty problems ...

So I looked a little bit more about 32 bit solutions with PAE 
(Physical Address Extension) 

In a linux kernel it is just a kernel config parameter : CONFIG_HIGHMEM64G 

In Ubuntu Desktop kernel it has not been set by default, in Ubuntu Server kernel it has 
been set .. but Ubuntu Server kernel is optimized for a Server not for a desktop environement 
(no preemption, timer interrupt of 100Hz against 250Hz for the desktop ... )  

So the solution was to recompile the kernel.   

The problem is my config (as many other) relies on some restricted-modules.  There are some information on 
the ubuntu wiki about how to recompile those restrited modules for a custom kernel but it is quite a hack of 
config files .. not so straightforward.  

To keep it simple, I just created a new kernel with same name (abi,flavour..) and so
recompile the restricted module with default config files .. and that's it !


Here it is :

create a work directory

```

sudo apt-get install linux-kernel-devel fakeroot build-essential

sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)

sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
apt-get source linux-ubuntu-modules-$(uname -r)

sudo apt-get build-dep linux-restricted-modules-common
apt-get source linux-restricted-modules-common


```

go to linux-xxxx 

and edit debian/config/i386/config.generic

(adapt the path to your platform and flavour)

change the folowing lines :

```

# CONFIG_HIGHMEM4G=y
CONFIG_HIGHMEM64G=y

```

Now compile kernel and modules

go to linux-xxx

```

CONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-debs flavours=generic

```

go to linux-ubuntu-modules-xxx/
```

CONCURRENCY_LEVEL=2 AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic

```

go to linux-restricted-modules-xxx
```

CONCURRENCY_LEVEL=2 AUTOBUILD=1 fakeroot debian/rules binary-indep binary-arch

```

Now install all packages :

go to the root of your working directory
```

sudo dpkg -i linux-image-xxx-generic_2.6.24-19.34_i386.deb
sudo dpkg -i linux-headers-xxx-generic_2.6.24-19.34_i386.deb
sudo dpkg -i linux-ubuntu-modules-xxx-generic_xxx_i386.deb
sudo dpkg -i linux-headers-lum-xxx-generic_xxx_i386.deb
   
sudo dpkg -i linux-restricted-modules-xxx-generic_2.6.24.13-19.44_i386.deb 
sudo dpkg -i nvidia-glx-new_169.12+xxx_i386.deb 

```
(this is for macbook pro 4.  Your platform might have other restricted package to be installed)

Reboot and DO NOT udate your kernel and modules with ubuntu repo's because you will go back to the beginning !

Hope this help you to use your 4 Gigs !

Screnshot in attachment ..

---

### Post by Sef on 2008-07-08
Moved to Tips and Tutorials.

---

### Post by phico on 2008-07-09
Thanks, it's better here indeed !

---

### Post by Klaue on 2008-07-10
Thank you phico. I was planning to buy two additional GBs and wondered if I could use them without a 64bit system :)
Is there a flag one could set to prevent automatic kernel updates without having to check all the updates every time?

And (this may sound dumb, because I have no expertise at all with 64bit systems) does all 32bit software still work on a 64Bit-system (while only using 4 GB of ram even if you have way more) or doesn't it? I mean, was your reason for it that you still used 32bit software or what do you mean with "downgrading"?

---

### Post by TheAL76 on 2008-07-10
I just use the server kernel. I can use all of my 4 GB of RAM.

---

### Post by phico on 2008-07-11
> **TheAL76 said:**
> I just use the server kernel. I can use all of my 4 GB of RAM.

This is simpler to setup but I would not advice this because ... 
there are other differences between Desktop and Server kernel.  
And of course Server kernel is not optimized for a Desktop.  

For example there is no preemption in server kernel.
The server timer frequency is set to a 100 HZ while the desktop is set to 250 HZ ..

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

So I prefer to recompile the Desktop kernel with the only PAE flag
to get a Desktop optimized kernel with 4Gb up to 64Gb support ..

---

### Post by phico on 2008-07-11
> **Klaue said:**
> 
Is there a flag one could set to prevent automatic kernel updates without having to check all the updates every time?


I try to find the same .. but no way until now.  I just uncheck 
module, kernel and header at each update with update manager 

> **Klaue said:**
> 
 does all 32bit software still work on a 64Bit-system (while only using 4 GB of ram even if you have way more) or doesn't it? I mean, was your reason for it that you still used 32bit software or what do you mean with "downgrading"?

Some (most of actually) 32 bit applications can work on 64 bit os
if you install some additional libs.  Now it is not straightforward
and you have most of the time some additional hack to do .. 

For example getting java and flash plugin working on firefox 64 bit 
is a nightmare (no Sun Java plugin, Flash working not all the time...)
Then you can try to install firefox 32 with some hack to get it
working on 64 bit os ... and so and so ....  I also get java 
libraries not working on java 64 bits (even some sun sdk ...)

In the result it was more a battle to get 32 bit applications working
on 64 bit !  So I decided to go back to 32 bit + PAE because I get
4Gb support + all compatibilty.  But the day java 64 is more used
and all firefox plugin are available in 64 bit .. I definitely go
for 64 bit

---

### Post by kkfok1 on 2008-08-14
Just an alert to those having T61 or similar hardware. After following the instruction, the kernel can discover upto 4GB RAM but the volume, wireless, webcam (nvcvideo) all become not working. 

I think Ubuntu team should enhance the current version or provide a non-compile way to discover upto 4GB.

Anyway, thanks for the post as I do learn the way to compile a new kernel.

---

### Post by kud0gfx on 2008-08-14
thanks very much for this!

---

### Post by amp711 on 2008-08-16
Thanks for that info kkfok1.  I almost pulled the trigger on a recompile this morning of my R61i and have decided against it.

I wish that it was just enabled by default.  Don't really want to go through the hassle of switching to 64 bit...

---

### Post by airspirit on 2008-08-22
I did this this morning on a current update Hardy 32 install and it destroyed my linux install.  I was never again able to properly login to GDM because the restricted driver system was shot wouldn't accept nvidia drivers either from Envy or from the internal repository installation via the restricted driver menu.  The artifacts I got through the generic nv driver in recovery mode made it look like my graphics card was on fire.  Even after purging the system completely of everything nvidia and retrying installation it would not work.  Further, doing this destroyed alsa and network manager (though I managed to get those two back after reinstalling the -21 kernel and associated packages through synaptic).

I compulsively back everything up in case of issues such as this but somehow this broke things so thoroughly that no restoration could be done.  In the end I upgraded to Hardy 64 and I'm happy with it (rough edges notwithstanding).

I wish I could tell if it was something in particular I did wrong, though this is not my first go at kernel compilation (I'm an old gentoo user) and I followed the directions to the letter.  If you plan on doing this I would highly recommend backing up your entire disk before pulling the trigger.

---

### Post by dmsuperman on 2008-10-07
This is an absolutely lifesaving guide. I just bought 4GB of ram and was sad to find I could only see 2.75GB of it. Not only did I get to use 3.25 like I expected, but I get to use 4GB and the steps weren't very complicated. I'm using this guide to build 3 more machines with 4GB of ram in them, thanks =D

---

### Post by anandi on 2009-02-18
Hi,

I am using intrepid, and have 4GB ram on MBP4.1. Ubuntu shows 3020M, is this ok ? Shouldn't i see the complete 4GB ?

---

### Post by anandi on 2009-02-23
bump

Anyone ?

---

### Post by riqmat on 2009-02-23
Hi, 

I've got the same situation too.
Till now, the best solution I've read (but no yet tested) seems to upgrade from the "desktop" version of Ubuntu to the "server" version.
See this link :
[http://www.softwarevoices.com/archives/53-Only-seeing-3GB-of-RAM-on-Ubuntu-7.04-Feisty-when-4GB-are-installed-SOLUTION.html]("http://www.softwarevoices.com/archives/53-Only-seeing-3GB-of-RAM-on-Ubuntu-7.04-Feisty-when-4GB-are-installed-SOLUTION.html")

If you test it - please tell us if it's ok within Intrepid ;)

---

### Post by riqmat on 2009-02-23
well, I just tested this... and it works great ! Now I can use my 4GB.

One point I had to fix : verify that grub's menu has been adapted to launch your "server" image instead of your "generic" image. (both remain available)

It should look like this:
[COLOR="SeaGreen"]  kernel /boot/vmlinuz-2.6.27-11-server root=UUID=1adedd1f-619e-471a-b858-f78a30c77f67 ro quiet splash 
  initrd /boot/initrd.img-2.6.27-11-server
[/COLOR]
instead of:
[COLOR="Red"]  kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=1adedd1f-619e-471a-b858-f78a30c77f67 ro quiet splash
  initrd /boot/initrd.img-2.6.27-11-generic
[/COLOR]
=; Caution: do not copy/paste above: I'm not sure the UUID is always the same...

---

### Post by anandi on 2009-02-26
I prefer not to compile / use the server kernel. The server kernel isn't optimized for desktops (can't recall where i read it but it was in these forums itself)

---

### Post by zvacet on 2009-04-28
When I run first command 

> sudo apt-get install linux-kernel-devel fakeroot build-essential

I get error 

> E: Couldn't find package linux-kernel-devel


What am I doing wrong?

---

