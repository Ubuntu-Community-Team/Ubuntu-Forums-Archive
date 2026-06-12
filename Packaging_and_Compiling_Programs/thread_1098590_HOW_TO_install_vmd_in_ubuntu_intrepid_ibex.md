---
title: "HOW TO: install vmd in ubuntu intrepid ibex"
date: 2009-03-17
forum: Packaging and Compiling Programs
---

### Post by Claus7 on 2009-03-17
Hello,

in this how to I'll try to explain the steps I (we) took in order to install vmd-1.8.6 in ubuntu intrepid ibex. For the story the "machine" I installed it is a laptop Dell Latitude D630. The process I will describe here I'll try to be as general as possible. We goes for a collaborative work with a friend of mine. From now on I will use singular.

Even though I have written a How to before about this issue, the problems I've faced in installing vmd were really a lot and in the process I've learned a few things. So this is how it goes.

i)Dependencies
In a fresh installation of ubuntu intrepid I had a problem with synaptic package manager as these people:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

while typing a package name, only a few of them appearing in the results list. So in order to fix that this command should suffice:
```
sudo update-apt-xapian-index
```

Now that synaptic is ok you have to install via it the packages csh and libstdc++.so.5

It might be possible that you might have installed correctly vmd, yet not to see any error at all about the missing library libstdc++.so.5
In order to verify this I had to type:
```
vmd -dispdev text
```

Now solving the dependency issue we proceed with the installation.

ii)Installation
The following commands would suffice in a i386 architecture:
```
./configure LINUX
cd src
sudo make install
```

The installation paths and links are the same as my previous how to:
[http://ubuntuforums.org/showthread.php?t=598518](http://ubuntuforums.org/showthread.php?t=598518)

Now if you try to open vmd you might be disappointed. The message that sais:
> Unable to create OpenGL window
might arise.

If this happens 99% you have problems with your graphics card. And now the real story beggins.

1)is GLX extention in the list that arises if you type:
```
xdpyinfo | more
```
2)Propably it is not so you have to find out the type of the graphics card you have. In order to do so type:
```
lspci
```
For Intel graphic cards you will see something similar as:
> *01:00.0* VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
As a matter of fact this is the result in my desktop computer. In the laptop it was different. It was something like GM965/GL960. What is does matter is to recognise the vga string of words. 
3) Find the vendor and pci.id of your graphics card.
Ok you have found out that you have a graphics card installed somewhere. Now what? You have to see if this graphics card is supported by the linux kernel. To do so you have to type:
```
lspci -n
```
and something like this will arise:
> *01:00.0* 0300: [COLOR="SeaGreen"]10de[/COLOR]:[COLOR="Red"]0221[/COLOR] (rev a1)
Note in italics the number *01:00.0* which will enable to identify the vendor and pci.id of the graphics card and not any other pci device.
Now in the previous quote you have the numbers:
[COLOR="SeaGreen"]10de[/COLOR] -> vendor
[COLOR="Red"]0221[/COLOR] -> pci.id

4)Support from kernel
With the pci.id number you go there or to a similar web page:
[http://cateee.net/lkddb/](http://cateee.net/lkddb/)
and type the pci.id of the graphic card. It it's there then things are good.

5)install the driver yourself
If it is not installed you have to find the driver and install it yourself. For the 945 chipset I found out this:
[http://ubuntuforums.org/archive/index.php/t-465810.html](http://ubuntuforums.org/archive/index.php/t-465810.html)

iii)Configure xorg.conf file to solve opengl issue
Yet, the question remains. Why opengl refuses to open? Now that we know that the driver of the graphic card is there what should we do next?

Reading this:
[http://ubuntuforums.org/showthread.php?t=620843](http://ubuntuforums.org/showthread.php?t=620843)
I found out that the xorg.conf file wasn't properly configurated. I had to write manualy:
> Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

In other models of graphics cards the above will be different.

I logged out and logged in and things were working nicely.

If something goes wrong then the good old command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
will restore back your graphical environment.

Regards!

---

### Post by Claus7 on 2009-04-07
Hello,

the same installation procedure applies also to Jaunty Jackalope for vmd version 1.8.6. .

Regards!

---

### Post by Psychopump on 2009-04-08
I can't find where to enter the pci.id on [http://cateee.net/lkddb/](http://cateee.net/lkddb/) ?

---

### Post by Claus7 on 2009-04-09
Hello,

I have seen that they have changed the web site a little. Does this link help?
[http://pciids.sourceforge.net/v2.2/pci.ids](http://pciids.sourceforge.net/v2.2/pci.ids)

Regards!

---

