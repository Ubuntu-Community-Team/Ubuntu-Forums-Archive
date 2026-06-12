---
title: "How to compile the UNSTABLE 2.6.18-rc2 kernel from kernel.org"
date: 2006-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxnewbie946 on 2006-07-19
***[COLOR="Red"]ATTENTION! THIS IS A GUIDE TO COMPILE THE _UNSTABLE_ 2.6.18-RC2 KERNEL FROM KERNEL.ORG. THIS KERNEL IS IN TESTING AND IS NOT STABLE. BY COMPILING THIS KERNEL YOU RISK SCREWING UP YOUR COMPUTER. DO NOT COMPILE THIS KERNEL IF YOU HAVE VALUBLE DATA STORED ON YOU HARD DRIVE.[/COLOR]***

[SIZE="2"]Please do not install this kernel unless you are willing to take the risk of messing up your computer. A tutorial to optimize the kernel you are compiling can be found [here]("http://ubuntuforums.org/showpost.php?p=1174954&postcount=507").
[/SIZE][B][U]
P.S. This howto is based on this thread here: [http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560). I give the credit for this thread to xXx 0wn3d xXx. Thanks![/U][/B]

**Before you begin, download the [latest kernel]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.tar.bz2") and the _unstable_ [performance patch]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.18-rc2.bz2")**.



[SIZE="2"][LIST=1]
[*][COLOR="Blue"]Install the utilities needed to configure the kernel[/COLOR]
```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev
```

[*][COLOR="Blue"]Now we are going to move the kernel and unpack it.[/COLOR]
```
sudo cp linux-2.6.17.tar.bz2 /usr/src
```

[*][COLOR="Blue"]Now we are going to move to /usr/src[/COLOR]
```
cd /usr/src
```

[*][COLOR="Blue"]Now unpack it.[/COLOR]
```
sudo tar -xvjf linux-2.6.17.tar.bz2
```

[*][COLOR="Blue"]Now we are going to remove the link to the linux directory:[/COLOR]
```
sudo rm -rf linux
```

[*][COLOR="Blue"]Make a new link to the new kernel:[/COLOR]
```
sudo ln -s /usr/src/linux-2.6.17 linux
```

[*][COLOR="Blue"]Move to the Linux directory:[/COLOR]
```
cd /usr/src/linux
```

[*][COLOR="Blue"]Make yourself root:[/COLOR]
```
sudo -s -H
```

[*][COLOR="Blue"]Apply the performance patch:[/COLOR]  **Don't use if you are not patching the 2.6.17 kernel !**
```
bzcat /home/$USER/patch-2.6.18-rc2.bz2| patch -p1
```

[*][COLOR="Blue"]Now we are going to import your current kernel configuration:[/COLOR]
```
sudo cp /boot/config-`uname -r` .config
```

[*][COLOR="Blue"]Configure the kernel:[/COLOR]
```
sudo make xconfig
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


[*][COLOR="Blue"]Make yourself root again:[/COLOR]
```
sudo -s -H
```

[*][COLOR="Blue"]Now time to build the kernel: [COLOR="Red"]Make sure that you are in **/usr/src/linux** with full root access.[/COLOR] This will build a debian file that you can install.[/COLOR]

Now in the terminal do this:

```
make-kpkg clean
```

Then this:

```
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
```
[COLOR="Green"]**Note:** You can replace "386" with anything you want. Like "k7" or "686."[/COLOR]
*[COLOR="DarkOrange"]The kernel will now compile for 1-3 hours, depending on the speed of your processor. If you have an extremely slow processor, you may have to wait 3-4 hours for the kernel to compile. In the meantime, I would go out to a movie or do something else while the kernel is compiling.[/COLOR]*



[*][COLOR="Blue"]Install the .deb files in /usr/src. There should be 2. If there are 3, then go ahead and install the third one (it should have module image in it. I say there should be two because I only got 2 and nothing screwed up. If you don't have 3 don't worry about it.) One should be an image deb file and the other a header deb file. In terminal do:[/COLOR]
```
dpkg -i <name of the file>
```
DO THIS FOR BOTH (or all 3) FILES.
IMPORTANT: IF YOU HAVE AN NVIDIA GRAPHICS CARD, YOU WILL HAVE TO REINSTALL THE DRIVERS FOR IT. REFER TO TROUBLESHOOTING BELOW.

[*][COLOR="Blue"]Now reboot and you will have a faster system![/COLOR][/SIZE]
[/LIST]


[COLOR="Green"][B]
Troubleshooting:[/B][/COLOR]
-------------------------------------------------------------------------------
Q: My Wifi Doesn't work !

A:To get wifi working, compile the new ndiswrapper from source. Follow the tutorial.
-------------------------------------------------------------------------------
Q: When I reboot I get Grub Error 22 ! WTF ???

A: You may have missed a step or messed something up. When it says Grub Loading..... press esc and you will be able to boot with another kernel. Then you should go into synaptic and uninstall the broken kernel and then reompile it.
--------------------------------------------------------------------------------
Q: How can I get fglrx and DRI working on my new kernel ?

A: Type this in terminal:

> sudo apt-get install fglrx-kernel-source

Reboot and if that does not work, make sure fglrx is in the Driver section.
---------------------------------------------------------------------------------
Q: I can't get X to load. Tried to use my xorg.conf backup and used apt-get to get the fglrx-kernel-source. What should I do?

A: You need to reinstall the drivers for your graphics card. Here is a site on how to do that ([http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")). It would be best to use method 1, but **[COLOR="Red"]skip the first 2 steps[/COLOR]** After you do that make sure to add nVidia to your /etc/modules file.

**_[COLOR="Red"]I will not be providing support for this thread as I am for my other thread ([http://www.ubuntuforums.org/showthread.php?t=217657]("http://www.ubuntuforums.org/showthread.php?t=217657"))[/COLOR]_**

----------------------------------------------------------------------------------


[COLOR="Red"]**Want your bootup screen to look better? Do you hate the low resolution but don't want to have to compile another kernel to install bootsplash? You need **[/COLOR][COLOR="Red"]**[Splashy]("http://www.ubuntuforums.org/showthread.php?t=216597&highlight=splashy")**[/COLOR]!

---

