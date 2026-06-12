---
title: "HOWTO: build custom kernel [not for newbies]"
date: 2009-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by sandyd on 2009-12-10
Im going to post basic instructions on how to build a customized kernel for karmic without using git.
Note that this will take some research as you need to know your computer's hardware components.
It might also take a few tries for you to set all the modules and stuff right.
Part of this guide is based on the ubuntu wiki pages, but not all because karmic introduced a new type of (linux-source).
NOTE: this guide does NOT cover compiling from git, but instead covers how to build your own ubuntu kernel from linux-source.

so lets begin....

1. Getting dependencies for build.
```

sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile
sudo apt-get build-dep linux
sudo apt-get install linux-source
//next two steps might not work, ignore errors
sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
sudo apt-get source linux-ubuntu-modules-$(uname -r)
cd /usr/src
sudo bunzip2 -d kernel*.bz2
sudo tar xvf kernel*tar
cd kernel-source*

```2. Preparing and setting options and modules for build.
At this point, try as hard as you can to get all of the configuration optimized
I highly advise you to look through EACH and EVERY section to make sure that everything is correctly selected.
Components with a [M] in front will be loaded as a module
Components with a 
[*] in front will be in the kernel
You can switch between the status of the kernel components (built in, module, not included) by using the space bar.
its best to have all of your hardware support built into the kernel. The main point of using a custom kernel is to not have unnecessary modules loaded as this will slow down your system/boot time. Therefore, ensure that the hardware that you use is built into the kernel, and everything else is left as a module.
```

sudo make menuconfig

```3. Build And Install Kernel
```

sudo make //build the kernel[FONT=Verdana]
[/FONT][FONT=Verdana]sudo make modules //make sure modules are built[/FONT]
sudo make modules_install //install modules
[FONT=Verdana]sudo make install //install kernel
cd /boot
**sudo mkinitramfs -o ./initrd.img-2.6.xx.xx //replace with compiled kernel, HINT, look in /boot for a vmlinuz thats missing a initrd.img**
sudo update-grub
[/FONT]
```if you need to do this over, simply run
this....
```

cd /usr/src/linux-source*
sudo make clean
sudo make menuconfig

```If youve successfully built your kernel and its all working, run 
```

cd /usr/src/linux-source*
sudo make menuconfig
sudo make clean

```scroll down to the very bottom of menuconfig with the down key.
save the configuration and post it here along with your computer model ahd hardware.
It will help other struggling users.

Hint: dont build the Open Sound System (OSS) device support if you don't need to. It requires that you have the audio card firmware on hand.

---

### Post by jpeddicord on 2009-12-13
Clean & concise. Approved; thank you for your contribution to Tutorials & Tips!

---

### Post by sandyd on 2010-01-19
thanks to colin ([http://www.garytang.co.cc/2009/12/11/compiling-customized-kernel-ubuntu-9-10/#comment-16](http://www.garytang.co.cc/2009/12/11/compiling-customized-kernel-ubuntu-9-10/#comment-16)) for testing it out and pointing out a few typos and missing sudos. 

Fixed in post.

---

### Post by Sylslay on 2010-01-19
Thanks for that post,
1)I have traied: kernelcheck,
2) Debian way to compile kernel.
3) Some ohter Ways too, from books.
NO SUCESS. Alway something wrong. 
Have no sound , and lost about 50 houers of mine "machinig time".

And what for? kernel-generic is good as wall? Isn't it?
Is good as compiled one (meaby exept gentoo distro)

4) I wan't tray this time, unless ANYBODY give me reason for that tremendous WORK.
PS. I have been traying sine Debian 4 (Eteh). Am I DUMMY?
Even follow the HOW TO from 1997,

//I will bookmarked that post
// THX

---

### Post by dud3 on 2010-01-26
Thank you, 
compiling now (2.6.32.6 core2)

BTW: does anyone know if x86_64 generic is better or less optimized than core2 for a intel e6600? if i don't see any improvements i'll try the generic one...
Cheers

---

### Post by Bukran on 2010-01-26
Very interesting and concise tutorial. I have a question for experts, maybe ;)

Do you know if latest Ubuntu release (Karmic 9.10) can boot with kernel version 2.6.16? I need this precise version for development reasons but haven't been able to boot after compiling - kernel panic -. I need to know if there can be an incompatibility or I'm just missing some option from menuconfig.

Thanks in advance.

---

### Post by Barriehie on 2010-01-26
I'm up for this but have 1 question!!!  If, for whatever reason, we end up with a non-bootable ](*,) , machine how to undo?  What do we need to make .old copies of and where?  I'ld really like to give this a go, I've already compiled my FF and noticed a diff.  I can only imagine a compiled kernel will make a big diff too!

TIA,
Barrie

---

### Post by sandyd on 2010-02-10
> **Barriehie said:**
> I'm up for this but have 1 question!!!  If, for whatever reason, we end up with a non-bootable ](*,) , machine how to undo?  What do we need to make .old copies of and where?  I'ld really like to give this a go, I've already compiled my FF and noticed a diff.  I can only imagine a compiled kernel will make a big diff too!

TIA,
Barrie

you know when you upgrade the kernel, you get an extra kernel in grub? same thing applies here. it it doesnt work, just select your origional kernel at bootup :D

---

### Post by sandyd on 2010-02-10
> **Bukran said:**
> Very interesting and concise tutorial. I have a question for experts, maybe ;)

Do you know if latest Ubuntu release (Karmic 9.10) can boot with kernel version 2.6.16? I need this precise version for development reasons but haven't been able to boot after compiling - kernel panic -. I need to know if there can be an incompatibility or I'm just missing some option from menuconfig.

Thanks in advance.

although this guide was never designed for that kernel version, it should work. you are likely missing something from menuconfig.

---

### Post by Bukran on 2010-02-10
> **carlee said:**
> although this guide was never designed for that kernel version, it should work. you are likely missing something from menuconfig.

Yeah, I'm near to find it. Do you know if there's something necessary to boot in a virtual drive? I'm testing everything under VMware Player 3.0.0 build-203739.

---

### Post by feistybill on 2010-02-10
Carlee,
when I tried compiling the kernel using the "debian way" and other methods, I always got a custom kernel along with a series of problems like no wifi, no audio, etc.

The "official" guide at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) says you have to rebuild the restricted modules using the guide at [https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules) to get intel wifi and other things to work.

So my question is, do I have to rebuild the restricted modules after following your guide?

---

### Post by sandyd on 2010-02-10
> **feistybill said:**
> Carlee,
when I tried compiling the kernel using the "debian way" and other methods, I always got a custom kernel along with a series of problems like no wifi, no audio, etc.

The "official" guide at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) says you have to rebuild the restricted modules using the guide at [https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules) to get intel wifi and other things to work.

So my question is, do I have to rebuild the restricted modules after following your guide?

hmm. for me, everything worked OOTB.
except for video drivers of course. But I expected that cause I always get a problem with them when upgrading kernels.
If you look carefuly in menuconfig, youll find ALL of the restricted modules in there. Including the sony memorystick pro support (experimental ) :D
All of the stuff in the restricted-modules are in the compiled kernel, except for the self-compiled ones such as if you installed the bcmwl from source.

---

### Post by feistybill on 2010-02-11
> **carlee said:**
> hmm. for me, everything worked OOTB.
except for video drivers of course. But I expected that cause I always get a problem with them when upgrading kernels.
If you look carefuly in menuconfig, youll find ALL of the restricted modules in there. Including the sony memorystick pro support (experimental ) :D
All of the stuff in the restricted-modules are in the compiled kernel, except for the self-compiled ones such as if you installed the bcmwl from source.

Ok, thanks for clarifying. And for your guide :)

---

### Post by zenon222 on 2010-05-24
I was happily compiling vanilla kernels with the realtime patches in Karmic using this guide until I upgraded to Lucid.  Now I can't seem to compile anything that boots.

This is the error that I think is killing me:
```
KERNEL PANIC - NOT SYNCING VFS: UNABLE TO MOUNT ROOT FS ON UNKNOWN-BLOCK (8,12)
```

A bit further into the boot sequence stuff like: "/lib/modules/2.6.29.6-rt24-2010.05.24/kernel/drivers/hid/xxx.ko" cannot be found, so I'm thinking it may be a grub thing...

The bootable stock lucid kernel has the following grub.cfg entry:
```
menuentry 'Ubuntu, with Linux 2.6.32-22-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bb1cd0ab-7955-48bc-bfac-4bf56970ec28
    linux    /boot/vmlinuz-2.6.32-22-preempt root=UUID=bb1cd0ab-7955-48bc-bfac-4bf56970ec28 ro pci=nomsi  crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-22-preempt
}
```

The entry for my most recent vanilla kernel is:
```
}
menuentry 'Ubuntu, with Linux 2.6.29.6-rt24-2010.05.24' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bb1cd0ab-7955-48bc-bfac-4bf56970ec28
    linux    /boot/vmlinuz-2.6.29.6-rt24-2010.05.24 root=UUID=bb1cd0ab-7955-48bc-bfac-4bf56970ec28 ro pci=nomsi  crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.29.6-rt24-2010.05.24
}
```

So I'm back to thinking there's something off with the way I'm compiling things, are these instructions working for anyone in Lucid??

TIA.

---

