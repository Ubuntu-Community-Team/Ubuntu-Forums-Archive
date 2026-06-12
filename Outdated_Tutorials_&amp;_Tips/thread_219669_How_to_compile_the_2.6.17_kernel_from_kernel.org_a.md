---
title: "How to compile the 2.6.17 kernel from kernel.org as FAKEROOT"
date: 2006-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxnewbie946 on 2006-07-20
[CENTER][SIZE="3"]*This guide is for compiling the stable 2.6.17 kernel from kernel.org as FAKEROOT.*[/SIZE]

[COLOR="Green"]If you find a mistake please notify me right away. To compile the kernel normally, go to this thread: [http://ubuntuforums.org/showthread.php?p=1266839]("http://ubuntuforums.org/showthread.php?p=1266839")[/COLOR][/CENTER]

[SIZE="2"]I have finished compiling the latest 2.6.17 kernel as fakeroot from kernel.org and as a result, my computer has been running much faster. This is a tutorial on how to compile the 2.6.17 kernel from kernel.org. You do not need to use the 2.6.17 kernel but it is the kernel that is explained in this guide. You can configure the kernel for maximum speed in xconfig. A tutorial to optimize the kernel you are compiling can be found [here]("http://ubuntuforums.org/showpost.php?p=1174954&postcount=507").
[/SIZE][B]
P.S. This howto is based on these threads here:[http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560),[http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4"). I give the credit for this thread to xXx 0wn3d xXx and mlind. Thanks![/B]



[SIZE="2"][LIST=1]
[*][COLOR="Blue"]Install the utilities needed to configure the kernel[/COLOR]
```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev fakeroot
```

[*][COLOR="Blue"]Force a relogin[/COLOR]
su $USER[/CODE]
[COLOR="Green"]Note: Replace $USER with your username.[/COLOR]


[*][COLOR="Blue"]Now we are going to move to /usr/src[/COLOR]
```
cd /usr/src
```

[*][COLOR="Blue"]Now we are going to download the kernel.[/COLOR]
```
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.6.tar.bz2
```

[*][COLOR="Blue"]Now unpack it.[/COLOR]
```
tar -xvjf linux-2.6.17.6.tar.bz2
```

[*][COLOR="Blue"]Now we are going to remove the link to the linux directory:[/COLOR]
```
rm -rf linux
```

[*][COLOR="Blue"]Make a new link to the new kernel:[/COLOR]
```
ln -sf /usr/src/linux-2.6.17 linux
```

[*][COLOR="Blue"]Move to the Linux directory:[/COLOR]
```
cd /usr/src/linux
```

[*][COLOR="Blue"]Now we are going to import your current kernel configuration:[/COLOR]
```
cp /boot/config-`uname -r` .config
```

[*][COLOR="Blue"]Configure the kernel:[/COLOR]
```
make oldconfig
make xconfig
```

_Here are some performance tips:_

> In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family Choose the model of your processor.

Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz

In Graphics Support
-_DISABLE NVIDIA RIVA IF YOU ARE USING 3RD PARTY NVIDIA DRIVERS. This has been known to cause problems_

In "Device drivers" go to "Block devices" and in "IO Schedulers" leave only the "CFQ I/O scheduler" activated, which provides the best performance.

In "Kernel hacking" uncheck "Kernel debugging".

Ctrl+S to save the kernel configuration and then close the window.
**NOTE: Not all the options will be the same in different kernels**


[*][COLOR="Blue"]Now time to build the kernel: [COLOR="Red"]Make sure that you are in **/usr/src/linux**.[/COLOR] This will build a debian file that you can install.[/COLOR]

Now in the terminal do this:

```
fakeroot make-kpkg clean
```

Then this:

```
fakeroot make-kpkg -initrd --revision=386 binary-arch modules_image
```
[COLOR="Green"]**Note:** You can replace "386" with anything you want. Like "k7" or "686."[/COLOR]
*[COLOR="DarkOrange"]The kernel will now compile for 1-3 hours, depending on the speed of your processor. If you have an extremely slow processor, you may have to wait 3-4 hours for the kernel to compile. In the meantime, I would go out to a movie or do something else while the kernel is compiling.[/COLOR]*



[*][COLOR="Blue"]Install the .deb files in /usr/src. There should be 2. One should be an image .deb file and the other a header .deb file. In terminal do:[/COLOR]
```
sudo dpkg -i <name of the file>
```
DO THIS FOR BOTH FILES.

IMPORTANT: IF YOU HAVE AN NVIDIA GRAPHICS CARD, YOU WILL HAVE TO REINSTALL THE DRIVERS FOR IT. REFER TO TROUBLESHOOTING BELOW.

[*][COLOR="Blue"]Now reboot and you will have a faster system![/COLOR][/SIZE]
[/LIST]


[COLOR="Green"][B]
Troubleshooting:[/B][/COLOR]
-------------------------------------------------------------------------------
Q: My Wifi Doesn't work !

A:To get wifi working, compile the new ndiswrapper from source. Follow the tutorial.
-------------------------------------------------------------------------------
Q: When I reboot I get Grub Error 22 ! WTH ???

A: You may have missed a step or messed something up. When it says Grub Loading..... press esc and you will be able to boot with another kernel. Then you should go into synaptic and uninstall the broken kernel and then reompile it.
--------------------------------------------------------------------------------
Q: How can I get fglrx and DRI working on my new kernel ?

A: Type this in terminal:

> sudo apt-get install fglrx-kernel-source

Reboot and if that does not work, make sure fglrx is in the Driver section.
---------------------------------------------------------------------------------
Q: I can't get X to load. Tried to use my xorg.conf backup and used apt-get to get the fglrx-kernel-source. What should I do?

A: You need to reinstall the drivers for your graphics card. Here is a site on how to do that ([http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")). It would be best to use method 1, but **[COLOR="Red"]skip the first 2 steps[/COLOR]** After you do that make sure to add nVidia to your /etc/modules file.

~Brain Juice
----------------------------------------------------------------------------------


[COLOR="Red"]**Want your bootup screen to look better? Do you hate the low resolution but don't want to have to compile another kernel to install bootsplash? You need **[/COLOR]**[Splashy]("http://www.ubuntuforums.org/showthread.php?t=216597&highlight=splashy")**[COLOR="Red"]![/COLOR]

---

### Post by linuxnewbie946 on 2006-07-20
Do not post your questions here, but on this thread: [http://ubuntuforums.org/showthread.php?p=1266839]("http://ubuntuforums.org/showthread.php?p=1266839")

---

### Post by citizenr on 2006-08-05
fakeroot make-kpkg -initrd --revision=386 binary-arch modules_image

compiles fine, cant write deb files (no permission)

make-kpkg --rootcmd fakeroot --initrd --revision=386 binary-arch

works fine

---

