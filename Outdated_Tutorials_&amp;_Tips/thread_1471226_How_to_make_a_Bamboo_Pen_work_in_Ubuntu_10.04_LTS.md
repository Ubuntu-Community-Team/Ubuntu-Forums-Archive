---
title: "How to make a Bamboo Pen work in Ubuntu 10.04 LTS"
date: 2010-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by sakisds on 2010-05-03
In the latest Ubuntu release, Wacom Bamboo Pen tablet's won't work out of box. So with a bit of searching around i found out how to make one work. The steps are easy, so i think everyone can follow this tutorial(and also can help new users get familiar with the terminal).

First of all, we need to download some packages by using the following command:
```
sudo apt-get install build-essential libx11-dev libxi-dev  x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
```

All these are required for the next steps.
Now we are downloading the latest version of the wacom drivers like this:
```
wget  http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2
```
*Note: If the link does not work, go to the sourceforge page of the linuxwacom project and download the latest package. Then replace the new filename(for example *"
"linuxwacom-0.8.7.tar.bz2"*)* *with the old one(*"linuxwacom-0.8.6-1.tar.bz2"[I]) in the following commands.


[/I]Now that we have everything we need, lets extract the package and configure it to do out job. 
```
tar -xf linuxwacom-0.8.6-1.tar.bz2
cd linuxwacom-0.8.6-1
 ./configure --enable-wacom
```

Not hard, right? Now lets get started with building out driver from the source code. Don't freak out, its easier that it sounds.

```
cd src/2.6.30/
 make
 sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
```

A lot of output, if you don't get any errors, we can move on and enable our new driver.

```
sudo rmmod wacom #This is just to be sure that the driver isn't running yet.
sudo modprobe wacom
```

Now try using your pen, it works! But if you restart your computer, the driver will be disabled. Not a big problem through, it can be easily fixed by adding one line to /etc/modules. Lets open it with a text editor: 

```
sudo gedit /etc/modules
```
[I]Note: gedit is used by default at the desktop ubuntu installation. If you are using Kubuntu, replace gedit with kate.

[/I]And the final step, add this line at the bottom:
```
wacom
```

You are finished! Now you can go to gimp and draw something ;)
Please tell me if you find anything wrong in the tutorial or if you encounter any problems.
Also sorry if my English are bad.

---

### Post by chris rowan on 2010-07-27
[I][I]"Now that we have everything we need, lets extract the package and configure it to do out job. 
```
tar -xf linuxwacom-0.8.6-1.tar.bz2
cd linuxwacom-0.8.6-1
 ./configure --enable-wacom
```

Not hard, right? Now lets get started with building out driver from the source code. Don't freak out, its easier that it sounds."[/I][/I]


oh dear .... my terminal says this, and I haven't a clue what to do with it:

Your wacom.ko is available under 
    /home/chris/linuxwacom/linuxwacom-0.8.8-7/src/2.6.30


NOTE: this package only supports Xorg server older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.

chris@chris-laptop:~/linuxwacom/linuxwacom-0.8.8-7$

---

### Post by Favux on 2010-07-27
Hi chris rowan,

As you can see it's a little dated and 0.8.6-1 isn't available anymore.  You can try the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

