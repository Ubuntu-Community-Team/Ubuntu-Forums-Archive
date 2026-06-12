---
title: "Kernel Compilation Help"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by jemate18 on 2008-05-25
Good day!

I'm using Xubuntu 8.04 Hardy Heron LTS

I have downloaded GNU/linux kernel 2.6.25.4 from [http://lkml.org](http://lkml.org).
I want to compile it and use it. (This is my first try of kernel compilation)
I have extracted the files to /usr/src

These are the steps I made:

$ls -l 
```

linux-2.6.25-4
linux-headers-2.6.24-16
linux-heders-2.6.24.16-generic

```

$cd ./linux-2.6.25-4
$make mrproper
$make menuconfig
$make dep
```
*** Warning: make dep is unnecessary now.
```
$make clean
$make bzImage
$make modules
$make modules_install
$cp -p arch/x86/kernel/boot/bzImage /boot/vmlinuz-2.6.25.4-stable

I have made the necessary changes in the menu.lst

I have succeded in booting in to my new kernel 2.6.25.4-stable
How ever my NIC wasn't detected at all using my new kernel no message found regarding ethernet (using dmesg) and there is no internet connection. In my window pane, there is the icon which says no network device found. Which make me think that my NIC wasn't working.

This is my NIC when I used dmesg using the xubuntu kernel 2.6.24-16-generic (Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)). It was working on my old kernel.

What do i have to do to make it work? Did i do something wrong in kernel compilation? what drivers do I have to load using modprobe..

Can somebody give me step by step procedure on enabling my NIC with my new kernel?

THANKS

---

### Post by sdennie on 2008-05-25
It's possible that the network card driver wasn't enabled in your kernel config.  

For future reference, there are actually much nicer ways to build and install a kernel on debian based systems.  I have used this guide in the past and it's worked very well for me: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by PmDematagoda on 2008-05-25
You could've used the config from the Ubuntu kernels which can be found in /boot and then load it.

Also, vor's link is really good, but if you want a condensed list of commands(really condensed), then they would be:-
```
sudo make modules
```
```
sudo make modules_install
```
```
sudo make bzImage
```
```
sudo make install
```
```
sudo update-initramfs -k name-of-modules-folder -c
```
and then after all that:-
```
sudo update-grub
```

Of course, you can switch to root before starting the compile to get rid of the sudos:).

---

### Post by jemate18 on 2008-05-25
Oh ok. Thanks for the link and guide.

But I'm trying to learn how to compile the kernel using the steps I have used above so that when I use different distro, it will be just like the same.

Can you point out where in the device driver section of the kernel can I enable the network card I have? I have looked at the device driver section and I am confused which module or driver will I enable (compiled or module).. Thanks again

---

### Post by PmDematagoda on 2008-05-25
> **jemate18 said:**
> Oh ok. Thanks for the link and guide.

But I'm trying to learn how to compile the kernel using the steps I have used above so that when I use different distro, it will be just like the same.

Can you point out where in the device driver section of the kernel can I enable the network card I have? I have looked at the device driver section and I am confused which module or driver will I enable (compiled or module).. Thanks again

Just enable all the devices in the Networking section, that shouldn't cause much harm except for a longer compile time and a larger kernel image/modules. Also, you could just load the Ubuntu config file for ease so that you may not overlook any other important settings.

---

### Post by jemate18 on 2008-05-25
> **PmDematagoda said:**
> Just enable all the devices in the Networking section, that shouldn't cause much harm except for a longer compile time and a larger kernel image/modules. Also, you could just load the Ubuntu config file for ease so that you may not overlook any other important settings.


Ok. I'll enable all the devices in networking section. By the way. here is the files in my /boot
```

root@myLinux:/boot# ls
abi-2.6.24-16-generic         
initrd.img-2.6.24-16-generic.bak  
vmlinuz-2.6.24-16-generic
config-2.6.24-16-generic      
lost+found                        
vmlinuz-2.6.25.4-stable
grub                          
memtest86+.bin
initrd.img-2.6.24-16-generic  
System.map-2.6.24-16-generic

```

Can you give me commands/steps on how to load the config file to my new kernel compilation? 

By the way the steps in which I did in my number 1 post differs in the steps of commands you have given, Do you think that caused some problems? I mean I started make bzImage before make modules and make modules_install (I just followed a tutorial section in an oreilly book) 

Thanks again

---

### Post by PmDematagoda on 2008-05-25
Just configure the kernel with:-
```
sudo make xconfig
```
That aught to give you a nice and friendly interface.

Also, the file you're looking for is:-
config-2.6.24-16-generic

---

### Post by PmDematagoda on 2008-05-25
> **jemate18 said:**
> 
By the way the steps in which I did in my number 1 post differs in the steps of commands you have given, Do you think that caused some problems? I mean I started make bzImage before make modules and make modules_install (I just followed a tutorial section in an oreilly book) 

Thanks again

About that, I don't think it really matters the order in which you carry out the commands, except that update-initramfs, update-grub and install must come in the order given, although I think it may be safe to switch the update-grub and update-initramfs about.

---

### Post by jemate18 on 2008-05-25
just another question, how am I going to load the config-2.6.24-16-generic? what commands will I use it to be loaded in my new kernel.. Thanks for your support and patience.

---

### Post by PmDematagoda on 2008-05-25
> **jemate18 said:**
> just another question, how am I going to load the config-2.6.24-16-generic? what commands will I use it to be loaded in my new kernel.. Thanks for your support and patience.

No commands, that's why I told you to try xconfig, there is an Open icon that you can use to load the config, that's why I said that xconfig has a friendly interface:).

---

### Post by jemate18 on 2008-05-25
Ok thanks ill try xconfig. (I have previously used make menuconfig).

---

### Post by sdennie on 2008-05-25
You can also do it with something like:

```

cp /boot/config-`uname -r` .config

```

(Assuming you are running the Hardy kernel)

Doing that from the top directory of the kernel source will use that config as the default.

---

### Post by jemate18 on 2008-05-25
> **vor said:**
> You can also do it with something like:

```

cp /boot/config-`uname -r` .config

```

(Assuming you are running the Hardy kernel)

Doing that from the top directory of the kernel source will use that config as the default.

ok so copying it and then running the make menuconfig will load that config? Then I'll issue the commands make bzImage and then and so forth.....

Thanks

---

### Post by sdennie on 2008-05-25
Yes.  Before you start menuconfig or xconfig you can also do:

```

make oldconfig

```

Which will prompt you on the command line for the new options in the kernel version you are about to build.  I think it probably selects all the defaults if you just immediately go to menuconfig or xconfig and you can skip that step but, I always find it interesting to see what new options are available.

---

### Post by jemate18 on 2008-05-25
Hello again

can you please visit this link?
this is another kernel compilation error in my xubuntu distro.. 

[http://ubuntuforums.org/showthread.php?t=804706](http://ubuntuforums.org/showthread.php?t=804706)

Thanks. I appreciate your help

---

### Post by sdennie on 2008-05-25
I'm not really sure what would cause your build problem in the other thread.  It's a makefile problem but, having not built a kernel using the method you are using for a very long time, I'm not sure what steps you'd take to fix it.

---

### Post by jemate18 on 2008-05-25
> **vor said:**
> I'm not really sure what would cause your build problem in the other thread.  It's a makefile problem but, having not built a kernel using the method you are using for a very long time, I'm not sure what steps you'd take to fix it.

I will also try the guide and link you have given me on your previous response.

---

### Post by stinger30au on 2008-05-25
i hate to sound stupid, but, if the kernel released now is stable and is better then the one we are currently using from the ubuntu repos, wont someone from the ubuntu team put the updated kernel in to the repos so everyone can get their hands on it???

having said  that i have found some info that may help you on your quest to update the kernel

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

[http://kcheck.sourceforge.net/screenlet.html](http://kcheck.sourceforge.net/screenlet.html)

---

