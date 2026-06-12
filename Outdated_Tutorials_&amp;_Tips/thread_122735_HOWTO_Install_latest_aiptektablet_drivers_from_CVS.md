---
title: "HOWTO: Install latest aiptektablet drivers from CVS"
date: 2006-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by luopio on 2006-01-28
**[COLOR="Red"][SIZE="6"]Please see [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) for more up-to-date instructions[/SIZE][/COLOR]**



[SIZE="5"]Changelog[/SIZE]
Jan. 11 2009 - big red link to the official help page
Apr. 24 2007 - original howto replaced by bmcage's new version and luopio's fixes


[SIZE="5"]1. Obtain development system[/SIZE]
Enable universe, multiverse repositories in synaptic (in top menu: settings->repositories).
Open a terminal (applications->accessories->terminal) and enter the command:
```
sudo apt-get install build-essential linux-kernel-headers subversion linux-source
```


[SIZE="5"]2. Kernel Aiptek module[/SIZE]
We start by making the kernel driver.
```
mkdir aiptek
cd aiptek
svn co https://aiptektablet.svn.sourceforge.net/svnroot/aiptektablet/trunk/linux_kernel_drivers/2.6 aiptekkernel
cd aiptekkernel
make
```

Replace the current module with the new one we just compiled: 
```
cp /lib/modules/$(uname -r)/kernel/drivers/usb/input/aiptek.ko aiptek.ko.old
sudo cp aiptek.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input/
```

[SIZE="5"]3. Xserver module[/SIZE]
We start with adding the present defunct module, and then compile the new one, replacing the old with the result. In the aiptek directory:
```
cd ..
svn co https://aiptektablet.svn.sourceforge.net/svnroot/aiptektablet/trunk/xserver_input_driver aiptekxserver
cd aiptekxserver
sudo apt-get build-dep xserver-xorg-input-aiptek
apt-get source xserver-xorg-input-aiptek
```

The last command installed the source in the directory *xserver-xorg-input-aiptek-1.0.1*. We replace the files with the downloaded SVN files (I have used revision 190 which worked fine on Feisty):
```
cp xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.h xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.h.old
cp xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.c xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.c.old 
cp xf86Aiptek.c xf86Aiptek.h xserver-xorg-input-aiptek-1.0.1/src/
cd xserver-xorg-input-aiptek-1.0.1/
./configure --prefix=/usr
make
sudo make install
```


[SIZE="5"]4. Find the Tablet, and make a Udev rule[/SIZE]
Use gedit (or your favourite editor to create a new file)
```
sudo gedit /etc/udev/rules.d/66-aiptek.rules
```

Insert the following text there: 
```
# udev rule for aiptek tablets

KERNEL=="event[0-9]*", SYSFS{vendor_id}=="0x08ca", SYMLINK+="input/aiptektablet"
```

Save the file and restart Udev:
```
sudo /etc/init.d/udev restart
```

Plugin your tablet and check that you have a link in /dev/input/aiptektablet
```
ls /dev/input/aiptektablet
```


[SIZE="5"]5. Test the tablet[/SIZE]
You can query the device with the following command:
```
udevinfo -a -p $(udevinfo -q path -n /dev/input/aiptektablet)
```
This will show you how the different parameters of your tablet are set.


[SIZE="5"]6. Enable the pen in the Xserver[/SIZE]
Now we enable the pen in the xserver. For this we need to edit our xorg.conf file. First, backup the old one:
```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.no-pen
```

Now, edit the file xorg.conf with kate/gedit. The standard Ubuntu xorg comes with the wacom tablet enabled. You should delete the entries referring to the wacom tablet driver. Now, you add an InputDevice section:
```
Section "InputDevice"
 Identifier "pen"
 Driver "aiptek"
 Option "Device" "/dev/input/aiptektablet"
 Option "Type" "stylus"
 Option "Mode" "absolute"
 Option "Cursor" "stylus"
 Option "Mode" "absolute"
 Option "PressCurve" "0,5,95,100"
 Option "zMin" "0"
 Option "zMax" "512"
 Option "ZThreshold" "0"
 Option "USB" "on" 
 Option "KeepShape" "on"
 Option "debuglevel" "0"
EndSection
```

You can find info on these settings on [xfree86]("http://www.xfree86.org/4.4.0/aiptek.4.html") or by typing the command '*man aiptek*'. Now we need to make sure the mouse does not conflict with our hyperpen, so we change the mouse InputDevice Section:
```
 Option "Device" "/dev/input/mice"
```
should be changed to
```
 Option "Device" "/dev/input/mouse0"
```
Furthermore, make sure the following option is present:
```
Option "CorePointer"
```
In some cases, the mouse is not on mouse0. Test this first with the command:
```

udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse0)
udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse1)
...
```
and select the correct mouse node for use in xorg.conf. In my case mouse1 returns among others: ATTRS{name}=="Logitech USB-PS/2 Optical Mouse", so I need to set /dev/input/mouse1.

Note that hotplug of another mouse will not work after this, as this mouse will be connected to another input. So, you need to change your xorg.conf again in that case and restart X.

Now we change the ServerLayout section to reflect our changes. In my case:
```

Section "ServerLayout"
 Identifier "Default Layout" 
 Screen "Default Screen" 0 0
 InputDevice "Generic Keyboard" "CoreKeyboard"
** InputDevice "Configured Mouse" "CorePointer"**
 # the following are entries for the tablet
** InputDevice "pen" "AlwaysCore"**
 #InputDevice "cursor" "AlwaysCore"
 #InputDevice "eraser" "AlwaysCore"
EndSection
```
If you don't have a standard mouse, or you don't care about it, remove its entry and change the
```
InputDevice "cursor" "AlwaysCore"
```
line to
```
InputDevice "cursor" "CorePointer"
```


As a last step, we backup our changes:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pen 
```
Restart your X server and with a bit of luck, you can now use the tablet!

[SIZE="3"]Erasor and Cursor[/SIZE]
Is it usefull to add erasor and cursor to xorg? If so, what do they do and how do you activate them? Not clear to me.

[SIZE="5"]7. Configuration[/SIZE]
[SIZE="3"]7.1. General[/SIZE]
You can configure the tablet from the command line, or via a GUI called **gaiptek**.
[SIZE="4"]**[COLOR="Red"]Note that gaiptek is currently out of date and won't probably work with your tablet[/COLOR]**[/SIZE]

For the command line method, read [aiptek manual, section Programming the Tablet]("http://aiptektablet.sourceforge.net/kernel.html") 

To install gaiptek, go into your aiptek dir created above, and do the following:
```

svn co https://aiptektablet.svn.sourceforge.net/svnroot/aiptektablet/trunk/gaiptek gaiptek
cd gaiptek
sudo apt-get install libgtkmm-2.4-dev
./autogen.sh

```
This should already execute make, if not, run make separately. You can now run gaiptek via
```
cd src
./gaiptek
```
or install it system wide:
```

sudo make install
gaiptek

```

On my Feisty box, gaiptek gives an error that the driver is not found, and configuration is not possible. All help here is welcome. The xinput device pen is found, just no connection is made :( 

You find a short gaiptek manual [online]("http://aiptektablet.sourceforge.net/gaiptek.html").

[SIZE="3"]7.2. Configuring the Function buttons at the top[/SIZE]
Clicking the buttons at the top works, and they do F1->F12 in my case. Can this behaviour be changed?




[SIZE="5"]9. Usefull programs[/SIZE]
[SIZE="3"]9.1. GIMP[/SIZE]
If you want to use pressure-sensitivity in the Gimp image editor, start gimp, and select *File -> Preferences -> Input Devices -> Configure Extended Input Devices*. 
Select device "pen" and set the Mode to "screen" (Mode "window" does not center the pointer icon on the pointer position in my case). Save and close the configuration windows.

To test: open a new image, use the pen to draw with the brush tool. You can set the pressure effect with the "pressure sensitivity" options. Works great.

Question: What does the keys tab mean in this configuration? Doesn't really work

[SIZE="3"]9.2. Inkscape[/SIZE]
The pen is also usefull in Inkscape. Again, go to* File->Input Devices*, and as in GIMP you can enable the pen.

[SIZE="3"]9.3. Gsumi[/SIZE]
A nice black/white drawing program with pressure curve. Install it on feisty via:
```
sudo apt-get install gsumi
```
For info, see the [gsumi homepage]("http://www.gtk.org/~otaylor/gsumi/")

In my case the pressure is not really working: below 50 the pen draws, over 50 it doesn't?



[SIZE=5]Troubleshooting[/SIZE]

[SIZE=4]The tablet is not at /dev/input/aiptektablet[/SIZE]
If you are sure that you have saved the udev rule, restarted udev and plugged the tablet in with no success, then follow the instructions here to try to make it work. 
Run the command:
```
lsusb
```
In my case this returns:
```
Bus 002 Device 002: ID 03f0:0024 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 08ca:0010 Aiptek International, Inc. Tablet
Bus 001 Device 004: ID 046d:c01d Logitech, Inc.
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc.
Bus 001 Device 001: ID 0000:0000
```
From this one can see that in my case the Vendor of the Aiptek tablet is 08ca, and the product id is 0010. With this we will make a udev rule so that the tablet is found always in a fixed place:
```
cd /etc/udev/rules.d/
sudo touch aiptek-tablet.rules
sudo kate aiptek-tablet.rules
```
Use gedit in stead of kate on Ubuntu. Now in kate, paste the following, using the correct vendor and product id as determined with the method above, and save the file:
```
# links /dev/input/aiptektablet to the correct /dev/input/event*
# without it, X will not be able to locate the tablet
#
# Run "lsusb" to find your idVendor and idProduct values.
# All aiptek-compatible tablets might need different values.
#
# For me, lsusb outputs:
# Bus 001 Device 005: ID 08ca:0010 Aiptek International, Inc. Tablet
#
KERNEL=="event[0-9]*", SYSFS{idVendor}=="08ca", SYSFS{idProduct}=="0010", SYMLINK+="input/aiptektablet"
```

[SIZE=4]Xorg won't start anymore[/SIZE]
In case of an error, Xserver not starting, do the following: Press **CTRL+ALT+F4** to open another tty, login, and use your original configuration
```
sudo cp xorg.conf.no-pen xorg.conf
```
Now, you can restart the x server and all should be as in the beginning. 

You can investigate the error after restart by reading */var/log/Xorg.0.log.old*, looking for the place where the aiptek pen is loaded.

[SIZE="4"]Clicking with the pen[/SIZE]
Clicking the buttons on the pen does not work in my case. However, with one tap of the pen (tap on the tablet, like you tap on a touchpad) a click is done. Eg curves in inkscape can be made by doing a tap, and at the end of curve a double tap.



[SIZE="5"]Resources used for this howto:[/SIZE]
[LIST]
[*][aiptektablet-users]("http://sourceforge.net/mailarchive/forum.php?forum_name=aiptektablet-users") Go to 2006-12-02, thread: The world according to Rene, where he lists how to make it work on Fedora FC6
[*][This forum howto]("http://ubuntuforums.org/showthread.php?p=2517801")
[*][Aiptek Tablets on Debian Linux]("http://zeekat.nl/joost/trust-tablet/index.html")
[/LIST]

---

### Post by luopio on 2006-05-15
By creating a simple udev-rule you can make sure that the aiptektablet is always tied to /dev/input/aiptek. Here's my rule:
```
~$ cat /etc/udev/rules.d/aiptektablet.rules
 KERNEL=="event*", SYSFS{manufacturer}="AIPTEK International Inc.", 
 NAME="input/aiptektablet", MODE="0644"
```

---

### Post by also-rr on 2006-08-09
Has anyone installed this on 6.06? I can't get the kernel module to compile.

Installed headers, then the whole kernel source:

peu@elrsr-01:~/Downloads/Aiptek/aiptektablet/trunk/linux_kernel_drivers/2.6$ ls /usr/src/
linux-source-2.6.15  linux-source-2.6.15.tar.bz2
peu@elrsr-01:~/Downloads/Aiptek/aiptektablet/trunk/linux_kernel_drivers/2.6$ make KSRC=/usr/src/linux-source-2.6.15/
Cannot find kernel sources in /usr/src/linux-source-2.6.15/;
  give the path to kernel sources with KSRC=<path>                       argument to make
make: *** [prereq_check] Error 1

---

### Post by luopio on 2006-08-10
These directions were for Breezy, so they're a bit outdated. Also the current sources are in SVN, not in CVS. I changed the howto to reflect that, even though the rest won't work out-of-the-box. 

You only need the headers. Installing the source & headers is useless, because the source contains the headers also. 

I'm following the aiptektablet mailing list and I'll try out the latest drivers once they announce success (I'm hoping the new developers get the project to at least beta phase soon :-\" ). IF they work, I'll rewrite the howto.

---

### Post by also-rr on 2006-08-10
Just headers isn't enough (at least, wasn't when I tried that first before grabbing the source, which I needed for something else anyway).

I'm also watching the mailing list every now and again, good to see someone else is as well ;) Haven't seen any build instructions on there (yet) though.

For anyone interested, it seems that Nisis tablets are also Aiptek underneath ([link]("http://www.revis.co.uk/site/?q=node/58")) which is good as they seem to be offloading them at the moment in the UK... now just need to get the dang things to work right ;)

---

### Post by Josh_b on 2006-08-24
So, does that mean that we can't use Aiptek tablets **properly** until the new drivers come out? If so, then I'm not too happy. I haven't been able to use my tablet (A Medion from Aldi, which is really an aiptek) on my Windows drove because of a conflict with service pack 2, and wonderful Windows that won't let you uninstall SPs (and I thought I could choose to not install SP2 on my new computer, but noooo, XP with no SP only recognises 120GB of my 300GB SATA. grrr)

So how long until the new drivers come out?

---

### Post by luopio on 2006-08-24
John Barstow (one of the developers) has asked for a status update on which tablets are working. At the same time he said that he's been busy with other projects, but will get time "in the near future" for aiptek. 

I guess that if you really want to try to get your tablet working you can download the latest stuff from SVN and try to compile it yourself. I don't know if these really work, but they're your best bet. 

Or you can wait for John's release (which can take some time). Or you can start up a bounty for the release (I'll chip in a few &#8364;s too if you decide to start one :) )

---

### Post by casainho on 2006-09-26
> **also-rr said:**
> Has anyone installed this on 6.06? I can't get the kernel module to compile.

Installed headers, then the whole kernel source:

peu@elrsr-01:~/Downloads/Aiptek/aiptektablet/trunk/linux_kernel_drivers/2.6$ ls /usr/src/
linux-source-2.6.15  linux-source-2.6.15.tar.bz2
peu@elrsr-01:~/Downloads/Aiptek/aiptektablet/trunk/linux_kernel_drivers/2.6$ make KSRC=/usr/src/linux-source-2.6.15/
Cannot find kernel sources in /usr/src/linux-source-2.6.15/;
  give the path to kernel sources with KSRC=<path>                       argument to make
make: *** [prereq_check] Error 1

I was also having that error.. but I am now compiling the kernel.. and tried to compile again the aiptek kernel drivers and I am not geting that error :-)

---

### Post by pgatrick on 2006-12-24
Anyone messed with this at all lately? I've got one of these things that's just been laying around for years, I'd love to be able to actually use it. Tried compiling from SVN, but the xserver_input_driver part isn't working. Always get this:
```
Imakefile.c:39: error: Imake.tmpl: No such file or directory
imake: Exit code 1.
  Stop.

```

Also trieed installing from the repositories, no matter what I try it just doesn't seem to work.. It's recognized when it's plugged in and the appropriate kernel module loaded, but tit's still not actually working.. tail /var/log/Xorg.0.log:
```
Error reading Aiptek tablet: Success
Error reading Aiptek tablet: Resource temporarily unavailable
Error reading Aiptek tablet: Resource temporarily unavailable
Error reading Aiptek tablet: Success
Error reading Aiptek tablet: Interrupted system call
Error reading Aiptek tablet: Success
Error reading Aiptek tablet: Success
Error reading Aiptek tablet: Success
Error reading Aiptek tablet: Resource temporarily unavailable
Error reading Aiptek tablet: Resource temporarily unavailable

```

Anyone had any luck with one of these things?

Thought I might add, I'm on edgy 64 bit with kernel 2.6.17 and Xorg 7.1.1

---

### Post by luopio on 2006-12-26
I tried the code in SVN a few months back and I had a similar problem: the kernel module compiles and runs fine, but the Xorg module won't work. And AFAIK Imake is the build system that was used previously on Xorg, but now it's using GNU autotools, so the SVN code has not been updated to that.

However, the mailing list seems to be a bit more alive these days and something about having "everything working" by xorg 7.3 was mentioned. 

As soon as any of the developers calls for testing I'll try and compile the drivers and update the HowTo.

---

### Post by VirgilioVasconcelos on 2007-01-25
Hey guys... 

Anyone has a clue of what can I do if the kernel recognizes the module, the Xorg recognizes it too, and I still can't use my tablet?

Looking into the logs (dmesg | grep aiptek, and the Xorg log) I can see the module has been loaded successfully.

The problem is: My Xorg doesn't seem to differentiate my USB mouse from my tablet.

On the xorg.conf, if I leave this on the mouse configuration:
[INDENT]Option "Device" "/dev/input/mice"[/INDENT] 
My Xorg thinks my pen is my mouse, so... no pressure sensitivity.

So, by using "cat" on the devices listed on my "/dev/input/" and moving the mouse and the pen around, I've figured that:
[INDENT]mouse = "/dev/input/mouse0"[/INDENT]
and
[INDENT]tablet = "/dev/input/event4"[/INDENT]

After updating my xorg.conf with these values, I get no poiter movement by moving the pen, just mouse.

BUT, the most strange thing: The shortcut buttons on top of the tablet ARE responsive! If I press the pen over F5, for example, I get a "refresh" on my browser.

Testing on Gimp, the "Device Status" dialog shows "cursor" and "pen", but I never get response for the latter.

Any clue on how to solve this?

Thanks a lot in advance. :D

---

### Post by luopio on 2007-01-25
IIRC the tablet can't use the event subsystem (input/event*-nodes), so you have to find the device for the tablet (on ubuntu edgy it should be /dev/input/aiptektablet since that is the udev rule that is written for the tablet).

But anyway... I haven't been able to get pressure sensitivity even with that. Good luck!

---

### Post by VirgilioVasconcelos on 2007-01-29
> **luopio said:**
> But anyway... I haven't been able to get pressure sensitivity even with that

Hi, luopio. Thanks a lot for your answer.

I've set up the udev rule, and now my Xorg recognizes it, but (same as you) no pressure at all...

It get the clicks, but when I try to draw something in the Gimp, nothing happens, even after changing all the setting on the "input devices" section. :( 

In the future, I'll save more money to buy better hardware. My last choices were pretty bad, actually: this Aiptek tablet and a laptop with a Sis video card.

Cheers.

---

### Post by VirgilioVasconcelos on 2007-04-08
Hey guys. I've got full functionality (yeah, pressure!!) with my Aiptek 8000U. I've tested some things until I get it working 100%. 

This is how I got it to work. Probably some steps are not necessary, but this is the way it worked for me on Ubuntu 6.10 (Edgy)

First of all, make sure you have the multiverse and universe (binary and source) repositories enabled on /etc/apt/sources.list:

```
deb http://br.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy universe
deb http://br.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

```

After that, I've installed the official ubuntu driver:

	```
sudo apt-get install xserver-xorg-input-aiptek
```

Then I've downloaded the proper packages to build the driver:

	```
sudo apt-get build-dep xserver-xorg-input-aiptek
```

And downloaded the official ubuntu source for the driver
	
	```
sudo apt-get source xserver-xorg-input-aiptek
```

Now comes the tricky part. Instead of just building it, you've got to download the latest files from the developers website and replace the ones that came with the Ubuntu version.
	Enter in the source directory:
	```
cd xserver-xorg-input-aiptek-1.0.1/src
```
	
	Remove the old source files:
	```
sudo rm xf86Aiptek.*
```
	
	Download the latest ones:
	```
sudo wget http://aiptektablet.svn.sourceforge.net/viewvc/*checkout*/aiptektablet/trunk/xserver_input_driver/xf86Aiptek.h
sudo wget http://aiptektablet.svn.sourceforge.net/viewvc/*checkout*/aiptektablet/trunk/xserver_input_driver/xf86Aiptek.c
```
	
	Go back one directory and build it:
	```
cd ..
./configure
sudo make
sudo make install
sudo cp /usr/local/lib/xorg/modules/input/aiptek_drv.* /usr/lib/xorg/modules/input/
```

The last line is because the default build puts the files in the wrong place, so you have to move them to the right directory.

After that I've put on my /etc/X11/xorg.conf:
	```
Section "InputDevice"
	Identifier	"pen"
	Driver		"aiptek"
	Option		"Device"		"/dev/input/aiptektablet"
	Option		"Type"			"stylus"
	Option		"Mode"			"absolute"
	Option		"Cursor"		"stylus"
	Option		"PressCurve"		"0,5,95,100"
	Option		"zMin"			"0"
	Option		"zMax"			"512"
	Option		"zThreshold"		"0"
	Option		"USB"			"on"
	Option		"KeepShape"		"on"
	Option		"AlwaysCore"		"on"
EndSection
```
	
Changed the "ServerLayout" section to: 

	```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse" "CorePointer"
	InputDevice 	"pen" "SendCoreEvents"
EndSection
```

And changed the mouse section to:
	```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0" #instead of "/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

This is because "/dev/input/mice" is a shortcut that gets everything that work like a mouse such as your mouse AND your tablet at the same time. So you have to be explicit on this path. The way I found the correct path was:
	```
sudo cat /dev/input/mouse0 
```
(and moved my mouse to see if it gets some weird letters on the terminal. If not, go test with mouse1 and so on. Ctrl C stops the "cat".)

After that, I have just restarted the X server and everything worked like a charm. =)

I hope this works for you all too. =D

Cheers

---

### Post by luopio on 2007-04-22
Hi Virgilio, 

thanks for the instructions. Unfortunately it did not work for me.

I'm running feisty with the standard kernel driver (1.5) and Aiptek 8000U. I compiled the new driver and installed it, but the tablet still calculates the screen size wrong and pressure does not seem to work.

Could be that my synaptics mouse on this laptop is screwing with the tablet, but I doubt it... I disabled other mouses when I tried the tablet.

---

### Post by bmcage on 2007-04-23
Hi virgilio, this works for me on Feisty, AMD64. After 5 years having this tablet, finally it works somewhat in linux for me. 

Great! Pressure sensivity is there, but some things are still strange (icon of pen is not where the cross is where is drawn). 

I'll make a howto for feisty with this information and other sources on the net, or would you do that luopio?

---

### Post by luopio on 2007-04-23
> **bmcage said:**
> I'll make a howto for feisty with this information and other sources on the net, or would you do that luopio?

Well.. like I said in the previous post, I did not work for me. What did you exactly do? Did you install both: the xserver driver and the kernel driver or just one? Do you have any other mice plugged in? Did you use the same config as Virgilio? Are you using it on a laptop or on a desktop system?

If I can get this thing to work I will gladly update this howto. Perhaps I'll even make debs so that others can have it easy.

---

### Post by bmcage on 2007-04-24
Ok, what did I do, and what do I think should be in the howto:

A. The name should change to:  HOWTO: Install aiptektablet drivers from SVN for feisty fawn
==> I would limit it to feisty as that should work. As I don't think the tablet works without this procedure, it could even be HOWTO: Install an aiptektablet on feisty fawn

B. The procedure I did is, very verbose, the following:

[SIZE="5"]0. The resources used for this howto:[/SIZE]
[LIST]
[*][aiptektablet-users]("http://sourceforge.net/mailarchive/forum.php?forum_name=aiptektablet-users") Go to 2006-12-02, thread: The world according to Rene, where he lists how to make it work on Fedora FC6
[*][This forum howto]("http://ubuntuforums.org/showthread.php?p=2517801")
[*][Aiptek Tablets on Debian Linux]("http://zeekat.nl/joost/trust-tablet/index.html")
[/LIST]

[SIZE="5"]1. Obtain development system[/SIZE]
Enable universe, multiverse repositories, type:
```

sudo apt-get install build-essential linux-kernel-headers subversion linux-source

```


[SIZE="5"]2. Kernel Aiptek module[/SIZE]
We start by making the kernel driver.
```

mkdir aiptek
cd aiptek
svn co https://aiptektablet.svn.sourceforge.net/svnroot/aiptektablet/trunk/linux_kernel_drivers/2.6 aiptekkernel
cd aiptekkernel
make

```
In the following you should replace the kernel version *2.6.20-15-generic* with the current kernel version of your installation. You can retrieve this with the the command "*$(uname -r) *"
```

cp /lib/modules/2.6.20-15-generic/kernel/drivers/usb/input/aiptek.ko aiptek.ko.old
sudo cp aiptek.ko /lib/modules/2.6.20-15-generic/kernel/drivers/usb/input/

```

[SIZE="5"]3. Xserver module[/SIZE]
We start with adding the present defunct module, and then compile the new one, replacing the old with the result. In the aiptek directory:
```

svn co https://aiptektablet.svn.sourceforge.net/svnroot/aiptektablet/trunk/xserver_input_driver aiptekxserver
cd aiptekxserver
sudo apt-get install xserver-xorg-dev xorg-dev 
sudo apt-get build-dep xserver-xorg-input-aiptek
sudo apt-get source xserver-xorg-input-aiptek

```
The last command installed the source in the directory *xserver-xorg-input-aiptek-1.0.1*. We replace the files with the downloaded SVN files (I have used revision 190 which worked fine on Feisty):
```

sudo cp xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.h xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.h.old
sudo cp xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.c xserver-xorg-input-aiptek-1.0.1/src/xf86Aiptek.c.old 
sudo cp xf86Aiptek.c xserver-xorg-input-aiptek-1.0.1/src/
sudo cp xf86Aiptek.h xserver-xorg-input-aiptek-1.0.1/src/
cd xserver-xorg-input-aiptek-1.0.1/
sudo ./configure
sudo make
sudo make install
sudo cp /usr/local/lib/xorg/modules/input/aiptek_drv.* /usr/lib/xorg/modules/input/

```
The last line is because the default build puts the files in the wrong place, so you have to move them to the right directory.

[SIZE="5"]4. Find the Tablet, and make a udev rule[/SIZE]
Run the command:
```
lsusb
```
In my case this returns:
```
Bus 002 Device 002: ID 03f0:0024 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 08ca:0010 Aiptek International, Inc. Tablet
Bus 001 Device 004: ID 046d:c01d Logitech, Inc.
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc.
Bus 001 Device 001: ID 0000:0000
```
From this one can see that in my case the Vendor of the Aiptek tablet is 08ca, and the product id is 0010. With this we will make a udev rule so that the tablet is found always in a fixed place:
```
cd /etc/udev/rules.d/
sudo touch aiptek-tablet.rules
sudo kate aiptek-tablet.rules
```
Use gedit in stead of kate on Ubuntu. Now in kate, paste the following, using the correct vendor and product id as determined with the method above, and save the file:
```
# links /dev/input/aiptektablet to the correct /dev/input/event*
# without it, X will not be able to locate the tablet
#
# Run "lsusb" to find your idVendor and idProduct values.
# All aiptek-compatible tablets might need different values.
#
# For me, lsusb outputs:
# Bus 001 Device 005: ID 08ca:0010 Aiptek International, Inc. Tablet
#
KERNEL=="event[0-9]*", SYSFS{idVendor}=="08ca", SYSFS{idProduct}=="0010", SYMLINK+="input/aiptektablet"
```


[SIZE="5"]5. Test the tablet[/SIZE]
Restart your pc/xserver. In */dev/input * you should see the entry *aiptektablet*, as made by the udev rule. You can see to which event it is bound by running
```
cd /dev/input
ls -all
```
You can query the device with the following command:
```
udevinfo -a -p $(udevinfo -q path -n /dev/input/aiptektablet)
```
This will show you how the different parameters of your tablet are set.

[SIZE="5"]6. Enable the pen in the Xserver[/SIZE]
Now we enable the pen in the xserver. For this we need to edit our xorg.conf file. First, backup the old one:
```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.no-pen
```
Now, edit the file xorg.conf with kate/gedit. The standard Ubuntu xorg comes with the wacom tablet enabled. You should delete the entries referring to the wacom tablet driver. Now, you add an InputDevice section:
```
Section "InputDevice"
 Identifier "pen"
 Driver "aiptek"
 Option "Device" "/dev/input/aiptektablet"
 Option "Type" "stylus"
 Option "Mode" "absolute"
 Option "Cursor" "stylus"
 Option "Mode" "absolute"
 Option "PressCurve" "0,5,95,100"
 Option "zMin" "0"
 Option "zMax" "512"
 Option "ZThreshold" "0"
 Option "USB" "on" 
 Option "KeepShape" "on"
 Option "debuglevel" "0"
EndSection
```

You can find info on these settings on [xfree86]("http://www.xfree86.org/4.4.0/aiptek.4.html") or by typing the command '*man aiptek*'. Now we need to make sure the mouse does not conflict with our hyperpen, so we change the mouse InputDevice Section:
```
 Option "Device" "/dev/input/mice"
```
should be changed to
```
 Option "Device" "/dev/input/mouse0"
```
Furthermore, make sure the following option is present:
```
Option "CorePointer"
```
In some cases, the mouse is not on mouse0. Test this first with the command:
```

udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse0)
udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse1)
...
```
and select the correct mouse node for use in xorg.conf. In my case mouse1 returns among others: ATTRS{name}=="Logitech USB-PS/2 Optical Mouse", so I need to set /dev/input/mouse1.

Note that hotplug of another mouse will not work after this, as this mouse will be connected to another input. So, you need to change your xorg.conf again in that case and restart X.

Now we change the ServerLayout section to reflect our changes. In my case:
```

Section "ServerLayout"
 Identifier "Default Layout" 
 Screen "Default Screen" 0 0
 InputDevice "Generic Keyboard" "CoreKeyboard"
** InputDevice "Configured Mouse" "CorePointer"**
 # the following are entries for the tablet
** InputDevice "pen" "AlwaysCore"**
 #InputDevice "cursor" "AlwaysCore"
 #InputDevice "eraser" "AlwaysCore"
EndSection
```
If you don't have a standard mouse, or you don't care about it, remove its entry and change the
```
InputDevice "cursor" "AlwaysCore"
```
line to
```
InputDevice "cursor" "CorePointer"
```


As a last step, we backup our changes:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pen 
```
Restart your X server and with a bit of luck, you can now use the tablet!

[SIZE="3"]Erasor and Cursor[/SIZE]
Is it usefull to add erasor and cursor to xorg? If so, what do they do and how do you activate them? Not clear to me.

[SIZE="5"]7. Configuration[/SIZE]
[SIZE="3"]7.1. General[/SIZE]
You can configure the tablet from the command line, or via a GUI called **gaiptek**.

For the command line method, read [aiptek manual, section Programming the Tablet]("http://aiptektablet.sourceforge.net/kernel.html") 

To install gaipte, go into your aiptek dir created above, and do the following:
```

svn co https://aiptektablet.svn.sourceforge.net/svnroot/aiptektablet/trunk/gaiptek gaiptek
cd gaiptek
sudo apt-get install libgtkmm-2.4-dev
./autogen.sh

```
This should already execute make, if not, run make separately. You can now run gaiptek via
```
cd src
./gaiptek
```
or install it system wide:
```

sudo make install
gaiptek

```

On my Feisty box, gaiptek gives an error that the driver is not found, and configuration is not possible. All help here is welcome. The xinput device pen is found, just no connection is made :( 

You find a short gaiptek manual [online]("http://aiptektablet.sourceforge.net/gaiptek.html").

[SIZE="3"]7.2. Configuring the Function buttons at the top[/SIZE]
Clicking the buttons at the top works, and they do F1->F12 in my case. Can this behaviour be changed?

[SIZE="5"]8. Troubleshooting[/SIZE]
[SIZE="3"]8.1. General[/SIZE]
In case of an error, Xserver not starting, do the following: Press **CTRL+ALT+F4** to open another tty, login, and use your original configuration
```
sudo cp xorg.conf.no-pen xorg.conf
```
Now, you can restart the x server and all should be as in the beginning. 

You can investigate the error after restart by reading */var/log/Xorg.0.log.old*, looking for the place where the aiptek pen is loaded.

[SIZE="3"]8.2. Clicking with the pen[/SIZE]
Clicking the buttons on the pen does not work in my case. However, with one tap of the pen (tap on the tablet, like you tap on a touchpad) a click is done. Eg curves in inkscape can be made by doing a tap, and at the end of curve a double tap.

[[SIZE="5"]9. Usefull programs[/SIZE]
[SIZE="3"]9.1. GIMP[/SIZE]
If you want to use pressure-sensitivity in the Gimp image editor, start gimp, and select *File -> Preferences -> Input Devices -> Configure Extended Input Devices*. 
Select device "pen" and set the Mode to "screen" (Mode "window" does not center the pointer icon on the pointer position in my case). Save and close the configuration windows.

To test: open a new image, use the pen to draw with the brush tool. You can set the pressure effect with the "pressure sensitivity" options. Works great.

Question: What does the keys tab mean in this configuration? Doesn't really work

[SIZE="3"]9.2. Inkscape[/SIZE]
The pen is also usefull in Inkscape. Again, go to* File->Input Devices*, and as in GIMP you can enable the pen.

[SIZE="3"]9.3. Gsumi[/SIZE]
A nice black/white drawing program with pressure curve. Install it on feisty via:
```
sudo apt-get install gsumi
```
For info, see the [gsumi homepage]("http://www.gtk.org/~otaylor/gsumi/")

In my case the pressure is not really working: below 50 the pen draws, over 50 it doesn't?

---

### Post by bmcage on 2007-04-24
Luopio,

I you want I can send the source of above post to you, so you can easily edit for the howto. 

With the above, the pen works, but as you can see, still a lot of questions on how this use can be optimized. 
Also gaiptek not working annoys me, I tried some debugging, but the code is not clear to me yet.

---

### Post by luopio on 2007-04-24
bmcage, 

thanks for the howto! I fixed a couple of spots and removed quite a few unnecessary sudos. AFAIK gaiptek is very out of date. The current development focus seems to be on the drivers (first get stuff to work and in the official kernel tree and then work on the GUI's etc.)

I can't confirm that this works since it did not for me, but hopefully other users can :)

P.S. I also removed the downloading of the linux-sources since the headers are enough for compilation and also the xorg-dev files should not be needed (huge dependencies) as the build-deps for the drivers should suffice.

---

### Post by bmcage on 2007-04-24
I needed something from xorg-dev as otherwise there where errors in the make of the xorg driver. I couldn't be bothered with what was missing, just installed everything :) 

You're correct about the sudo's.

What exactly is not working for you? You can use the tablet put it positions wrongly on the screen?
I suppose if you query /dev/input/aiptektablet all is there? 

It would be great to have gaiptek working again, so some settings can be quickly changed to see if they help....

---

### Post by bmcage on 2007-04-27
Luopio, 

do you follow the aiptek mailing list? 

I've send a bug report and a patch to get gaiptek working.

The bug: /dev/input/aiptektablet gives errors because too long in xserver driver, so /dev/input/aiptek should be used, and hence also in the howto.

I send a one line patch to make the tablet in gaiptek recognized. Perhaps you could test? In gaiptek you can change your screensize as related to the tablet, so this might solve your screen problem. 

Anyway, even with that, the xorg driver is extremely unstable, and leads to crashes sometimes (on startup, shutdown, ....). Perhaps a warning about this on the howto would be usefull too :-)
I use xorg.conf.no-pen if no pen duties are needed and xorg.conf.pen otherwise.
 I works really great however in GIMP, wouldn't want to miss my tablet again.

Concerning the applications, perhaps you should mention also Tuxpaint, a life-saver when the kids have seen you play in GIMP and want to draw something with the pen too...

---

### Post by Puru on 2007-05-11
Works great here, with a "Trust 400 v2". The only issue is with my ps2 mouse, wich keeps changing event every boot: from /dev/input/mouse1 to /dev/input/mouse2.

I "solved" by adding another "Configured Mouse", pointing to the other event, as an input device ("Configured Mouse2") and added it as "AlwaysCore" in "Server Layout".

The dirtiest among solutions, but now I don't have to restart Xorg when my mouse needs a wind of change. Does anyone know a cleaner solution? I would have liked to create a udev rule for my mouse, but I can't manage to see it's IDs.

---

### Post by bmcage on 2007-05-14
Puru,

I don't find your solution dirty, xserver doesn't crash when no mouse is found.

For finding the id of the mouse, is it usb? Then lsusb should return the id to you (see my post #18).  Eg on my box I get: 

```
Bus 005 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
```

After setup, you can also query the found setting:

```
udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse1)
```

About using the tablet, xserver becomes somewhat unstable with this driver. A patch is submitted upstream but it will take a while before that appears in distro's. If you do not want to compile X server from source, it might be a good idea to have two xorg.conf files, and only use the one with the tablet, if you actually wil use the tablet.

Benny

---

### Post by Puru on 2007-05-14
Many thanks for your infos, bmcage, however my mouse is ps2, so lsusb won't be able to list it.

About compiling a patched module, I'm not afraid of building: there's nothing I wouldn't do for my linux-box! :D

What about this patch? Where can I find it?

---

### Post by bmcage on 2007-05-21
The patch is on [https://bugs.freedesktop.org/show_bug.cgi?id=10683](https://bugs.freedesktop.org/show_bug.cgi?id=10683) 

I'd wait till they include it and ship it. ;) 
Some people on aiptek user list did say it improved xserver enormously. If you apply the patch, do say on the bug list that it works, so as to speed up the inclusion of the patch in main xorg branch!

Benny

---

### Post by therezin on 2007-05-26
Hi all, I'm, desperate to get my Trust TB-4200 (rebranded aiptek 12000U) working under ubuntu studio. I've followed this tutorial as far as I can, but I get to the "make" command and get this error:

```
Cannot find kernel sources in /lib/modules/2.6.20-15-lowlatency/build;
  give the path to kernel sources with KSRC=<path>                       argument to make
make: *** [prereq_check] Error 1

```

I'm pretty new to linux in general, so I'm not entirely sure where to go from here. any pointers? the source definitely got downloaded, and there's plenty of directories under  /lib/modules/2.6.20-15-lowlatency, but there's no /build/. any clues?

---

### Post by bmcage on 2007-05-28
therezin.

You need to install with synaptic: 
build-essential
linux-headers-2.6.20-15-lowlatency  (In my case generic is installed, but in studio lowlatency is used)
(PS: this might be -16 by now, depends if you upgraded the kernel or not).
Next you need the package:
linux-source
I don't see a lowlatency version of that, so probably that is just a difference in modules and compile options, not in linux source

---

### Post by therezin on 2007-05-28
Thanks bmcage, it's all working now - pressure sensitivity, the pen maps properly to one of my monitors (exactly the way I was after), only one issue remains and it's a small one: when I try to load gaiptek (rarely since it all works fine anyway) it just instantly crashes X and I end up back at the login screen. Any clues?

---

### Post by Coffeebot on 2007-05-29
Awesome! I've been waiting years, and have spent countless hours trying to get this to work, and now it finally does! I'd given up, but randomly googled for answers today in a fit of boredom...and it worked, "out of the box"

Way to go, guys!

Question, though -- while it works beautifully, X crashes at boot if I don't have the tablet plugged in. Since I'm working on a laptop, having the tablet plugged in all the time isn't an option. I'm also using a usb mouse as my input, ignoring my synaptic. For whatever reason, if I have the tablet installed, my USB mouse is /dev/input/mouse4, the tablet is mouse2, and synaptic pad is mouse 3. Without the tablet, the usb mouse is mouse2, synaptic mouse3.

I'm sure there's a trick to get this to work, but I'm no X expert. Thoughts?

Thanks for all of your wonderful work!

---

### Post by bmcage on 2007-06-06
As I said in an earlier post, X server has a patch submitted, you'll have to wait for that to have it stable, or apply the patch yourself, and compile x server

Concerning Gaiptek, I and some other people submitted some patches needed for it to work 100%, no idea if they are in the SVN tree. It doesn't do much, but Gaiptek is a great way to see if your pen is recognized.

---

### Post by hva on 2007-06-20
has someone any clue about using the eraser? i couldn't understand much from driver's pages.
I also have problems with gimp and inkscape randomly crashing r whole system freezing when pressure sensitivity is enabled.

---

### Post by bmcage on 2007-06-21
hva, the crashing is an X server bug, see some earlier posts on where the patch is (if you can and want to recompile X). 
Not sure how eraser works, perhaps you set it in gaiptek in the tools by clicking on erasor. 
Anyway, on prefessional tablets you have more than one input device: a stylus, an erasor, ...

---

### Post by hva on 2007-07-02
i patched the xserver and the problem seems to have gone, thanks for the tip

---

### Post by xurizaemon on 2007-07-20
I got an Aiptek 12000U for the weekend. (I checked with the store that I can return it if it doesn't work with my required app.)

Some notes, because this thread is way piecemeal and probably deserves a reboot of its own, as the first few pages advise people to CVS compile a package which is now in core Ubuntu:

You can install evtest by installing dvb-utils. 
  ```
sudo apt-get install dvb-utils
```

Then you can use evtest to see the output of your tablet, which for me is accessed via /dev/input/aiptektablet
  ```
sudo evtest /dev/input/aiptektablet
```

I rebuilt the package from current SVN sources, although it didn't change my results much (except for being a bit more specific about the xorg.conf requirements - current version will reject entries containing more than one method of defining the ActiveZone in xorg.conf. Which, by the way, the developer tells us all about what the active zone settings do, but not what the active zone is ... unless you read xf86Aiptek.c :)

Here's how I rebuilt the Ubuntu package for Feisty based on Vergilio's instructions:
```

sudo apt-get build-dep xserver-xorg-input-aiptek
sudo apt-get source xserver-xorg-input-aiptek
cd xserver-xorg-aiptek-1.0.1/src
rm xf86Aiptek.?
sudo wget http://aiptektablet.svn.sourceforge.net/viewvc/*checkout*/aiptektablet/trunk/xserver_input_driver/xf86Aiptek.
sudo wget http://aiptektablet.svn.sourceforge.net/viewvc/*checkout*/aiptektablet/trunk/xserver_input_driver/xf86Aiptek.h
cd ../
sudo dpkg-buildpackage # i shoulda changed the version here
sudo dpkg -i ../xserver-xorg-input-aiptek_1.0.1-2ubuntu1_i386.deb

```

I used the calibrate script from wizardpen-driver, but had to use the output partially.

```

wget http://www.dallerweb.dk/ubuntu/wizardpen-driver-0.5.0.tar.gz
tar -xzvf wizardpen-driver-0.5.0.tar.gz
cd wizardpen-driver-0.5.0/calibrate
./wizardpen-calibrate /dev/input/aiptektablet

```

You'll get results like this. Don't copy mine! No copying!!

```

chris@vah:~/src/wizardpen-driver-0.5.0/calibrate$ sudo ./wizardpen-calibrate /dev/input/aiptektablet 

Press ANY corner of your desired working area: 237,210

Press the OPPOSITE corner of your desired working area: 5834,4346

Put the following lines into your /etc/X11/xorg.conf file:

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/input/aiptektablet"
        Option          "TopX"          "237"
        Option          "TopY"          "210"
        Option          "BottomX"       "5834"
        Option          "BottomY"       "4346"
        Option          "MaxX"          "5834"
        Option          "MaxY"          "4346"
EndSection

```

Extract either the TopX/BottomX TopY/BottomY  *OR*  the MaxX/MaxY (assumes Top=0) from these and paste into your xorg.conf in your Aiptek Pen InputDevice section. Current version will NOT accept both of these; the TopX/MaxX and XOffset/Xsize params are now mutually exclusive. Including more than one will prevent your XServer starting.

(This last fact is going to cause havoc on upgrade for people currently mixing voodoo values.)

Aiptek uses xTop/yTop and xBottom/yBottom values internally, but the other methods of setting may provide useful shorthands.

=====

I have a mostly working tablet but a few things still to fix:

1) I'm using nvidia TwinView. My righthand screen is #0 and left is #1. The initial click on the left side of the tablet is placed on the left side of screen #0, but if I horizontally wave the pen from side to side of the tablet, it moves further left each time until it gets to the middle of screen #1 at its leftmost reach.

2) Pressure appears (ranging from 0 to 512) when testing with evtest, but Gimp/Inkscape don't respond to it despite my following the instructions as listed in this thread (and elsewhere). The GNOME tablet control panel appears, but it also gives pressure as either on or off, no sensitivity.

3) Relative doesn't seem to be relative when using the mouse. And I don't know what all this talk about an eraser is ... my pen is just a pen. I've had Wacoms (ADB ones, jeebers!) which had erasers, but this Aiptek doesn't! :)

4) The tablet ignores the mouse until I click. The mouse is highly erratic, actually. I'm not too worried about mouse functionality myself :)

=====

Things we can do to make stuff better:

We should patch the wizardpen-calibrate tool for Aiptek and add it to the Aiptek package. It's a useful tool for the calibration, in the absence of anything else.

We could improve the documentation of the xorg.conf file and manpage for "man aiptek" to explain what the three (now mutually exclusive) settings mean.

=====

I hope this will improve, and would be stoked if I can get it working so I don't have to take it back. The hardware is super cheap and would be very nice to keep :)

---

### Post by droz928 on 2007-08-20
OK well i have now tried all three methods of installing this and still no luck. I am pretty new to linux just so you .

When i browse to /dev/input/aiptektablet there is nothing there. The directory doesn't even exists.

What am i doing wrong here?

---

### Post by bmcage on 2007-08-27
if you read all messages, you will see I wrote that there is an error in the aiptek driver of which the patch is at this moment still pending.

/dev/aiptektablet is too long. 

change it everywhere by 

/dev/aiptek

you might have done something else wrong of course (one small mistype somezhere is enough); but the above is a beginning. After that, check the syntax of your udev rule.

Benny

---

### Post by toshub on 2007-09-15
Hi,

I'm using Ubuntu Studio 7.04 with a lowlatency 2.6.20 kernel and an brand new Aiptek 14000U tablet which works in mouse mode without pression directly plugged on Feisty.

Believing it was an Aiptek tablet, i followed this post. Didn't work because this tablet reveals being a Waltop Media Tablet selled under european Aiptek distribution. I also changed the constructor and product ref. in the UDEV rules as lupio wrote (great work à propos). Didn't work then for me, till I found [this post]("http://ubuntuforums.org/showthread.php?t=477287").

In fact I replace in my xorg conf "aiptek" driver by wacom driver and /dev/input/wacom by /dev/input/aiptek. Here it is (I also use TwinView) :

```
 # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/aiptek"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/aiptek"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/aiptek"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Carte vidéo générique"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200 32M/64M"
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Carte vidéo générique"
	Monitor		"Écran générique"
	DefaultDepth	24
	Option         "TwinView" "1"
	Option         "TwinViewOrientation"  "crt-0 LeftOf crt-1"
    Option         "NoLogo" "1"
	Option         "Metamodes" "1280x800,1280x800; 1024x768,1024x768; 800x600,800x600;NULL,1280x800; NULL,1024x768; NULL,800X600; "
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```AND IT WORKS quite PERFECTLY : absolute mode, my dual display fits to the tablet, I've got pressure on Gimp without problem... Only exception : the two stylus button are reacting strangely depending on the application : middle button on XFCE, left button on Blender,... and I can't change Gimp and Inskape axes and buttons.

Hope this post would help some users. If someone could help me using my stylus button well. I'll be grateful. Thanks.

---

### Post by celticbhoy on 2007-10-20
Tried the original how-to and it all worked well.

But I have just done a clean install of Gutsy, and the how to no longer works, I have noticed that a few of the directories mentioned have moved, but some of the core steps dont work, has anyone got this going under Gutsy ?

Using a trust TB-2100 tablet.

lsusb gives :-

Bus 001 Device 004: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet

---

### Post by cemelmaci on 2007-10-27
hi today i installed ubuntu gutsy 7.10
and I tried aiptek drivers to install

```
sc@sc-laptop:~/aiptek/aiptekkernel$ sudo apt-get install build-essential linux-kernel-headers subversion linux-source
[sudo] password for sc:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
build-essential ist schon die neueste Version.
Achtung, wähle linux-libc-dev an Stelle von linux-kernel-headers
linux-libc-dev ist schon die neueste Version.
subversion ist schon die neueste Version.
linux-source ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

```

and 

```
sc@sc-laptop:~/aiptek/aiptekkernel$ cp /lib/modules/$(uname -r)/kernel/drivers/usb/input/aiptek.ko aiptek.ko.old
cp: Aufruf von stat für „/lib/modules/2.6.22-14-generic/kernel/drivers/usb/input/aiptek.ko“ nicht möglich: No such file or directory
sc@sc-laptop:~/aiptek/aiptekkernel$ sudo cp aiptek.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input/
cp: angegebenes Ziel „/lib/modules/2.6.22-14-generic/kernel/drivers/usb/input/“ ist kein Verzeichnis: No such file or directory
sc@sc-laptop:~/aiptek/aiptekkernel$ 

```

Any suggestion?

---

### Post by Puru on 2007-10-28
Patterns have been changed in this release, now it is

```

kernel/drivers/input/tablet

```

instead then

```

/kernel/drivers/usb/input/

```

Still, it is not clear to me weather the out of the box Gibbon modules are SVN alerady or not... well, in doubt, let's compile! :)

---

### Post by cemelmaci on 2007-10-28
thanks :)

 and a suggestion for tablet  testing

[http://www.gnomefiles.org/app.php/Gnome_Tablet_Apps]("http://www.gnomefiles.org/app.php/Gnome_Tablet_Apps")

---

### Post by cemelmaci on 2007-10-28
i have now another problem with gimp. wenn i drawing in gimp, suddenly program closed itself.

```
sc@sc-laptop:~$ gimp
The application 'gimp' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

(script-fu:6127): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error

```

GNU Image Manipulation Program Version 2.4.0-rc3

---

### Post by Puru on 2007-10-28
Yes, using latest aiptek tablet driver with pressure on makes X applications randomly crash. I could solve this by patching the xserver like bmcage suggested.

Here is the patch

[https://bugs.freedesktop.org/show_bug.cgi?id=10683](https://bugs.freedesktop.org/show_bug.cgi?id=10683)

Applying a patch and recompiling may scary some people, but it's quite easy.

here's the text on Bugzilla

```

diff -ru xorg-server-X11R7.1-1.1.0/hw/xfree86/common/xf86Events.c
my_xorg-server-X11R7.1-1.1.0/hw/xfree86/common/xf86Events.c
--- xorg-server-X11R7.1-1.1.0/hw/xfree86/common/xf86Events.c    2006-03-25
13:52:03.000000000 -0600
+++ my_xorg-server-X11R7.1-1.1.0/hw/xfree86/common/xf86Events.c 2007-04-16
15:10:52.000000000 -0500
@@ -1230,12 +1230,14 @@
 xf86SigioReadInput(int fd,
                   void *closure)
 {
+    int err_save = errno;
     int sigstate = xf86BlockSIGIO();
     InputInfoPtr pInfo = (InputInfoPtr) closure;

     pInfo->read_input(pInfo);

     xf86UnblockSIGIO(sigstate);
+    errno = err_save;
 }

 /*

```

the "diff" part is the command typed by the submitter to show the difference by his version and the official one, the actual patch starts with "---", so the part you should grab and copy to a new text file is

```

--- xorg-server-X11R7.1-1.1.0/hw/xfree86/common/xf86Events.c    2006-03-25
13:52:03.000000000 -0600
+++ my_xorg-server-X11R7.1-1.1.0/hw/xfree86/common/xf86Events.c 2007-04-16
15:10:52.000000000 -0500
@@ -1230,12 +1230,14 @@
 xf86SigioReadInput(int fd,
                   void *closure)
 {
+    int err_save = errno;
     int sigstate = xf86BlockSIGIO();
     InputInfoPtr pInfo = (InputInfoPtr) closure;

     pInfo->read_input(pInfo);

     xf86UnblockSIGIO(sigstate);
+    errno = err_save;
 }

 /*

```

save the textfile and give it the name you like the most.

Now let's hack!

You should already have the build-essentials, as you've compiled aiptek.ko previously. We're going to create a .deb package, many people just use dpkg with some fancy option, I prefer using debuild

```
sudo apt-get install debuild
```

to patch the xserver you need the source code

```

apt-get source xserver-xorg-core

```

to compile it, dependencies are needed

```
sudo apt-get build-dep xserver-xorg-core
```

copy the patch file you saved before to the xorg source directory

```

cp *yourpatchfile* xorg-server-1.3.0.0.dfsg/

```

let's move to xorg source directory

```

cd xorg-server-1.3.0.0.dfsg

```

now patch it

```

patch -p1 < *yourpatchfile*

```

the "p1" option means that we are in the xorg tree already, be sure the patch successfully applies (the output should be something like "one hunk succeded")

Compile and build the new package, always from the xorg source directory

```

sudo debuild binary

```

Wait a while, the system is building. When the "Matrix" thing ends, you'll find the new xserver-xorg-core deb package in the top directory, toghether with other xorg stuff. Install it with sudo dpkg -i xserver-xorg-core_*somethingwrittenhere*.deb

Reboot.

Updater shouldn't replace this package, it doesn't on my system. That's all, I hope you can find this mini-howto useful.

Another issue with gimp+pressure is that gimp may never detect pressure 0, it stiil will paint even when you just move the cursor. I found out that this happens when trying to draw with opacity pressure just after gimp startup, but if another instrument (pen, for example, wich is "size pressure" by default) is used at startup, then everything goes fine. That's all.

P.S. Should the patch be a solution, remember to subscribe a Bugzilla account and post a comment on that bug page, in order to have the fix on the official xserver (no patching at any release! :) )

---

### Post by cemelmaci on 2007-10-28
Thank you again, it working for me:)

---

### Post by celticbhoy on 2007-10-28
could you re-post as a complete first to last step how-to having trouble following.

---

### Post by daw3b on 2007-12-14
thx to all my tablet works :) 
just one problem with the mouse; sometimes at boot /dev/input/mouse1 disappear, so I have to put in Xorg.conf mouse3 instead and the restart X and then put back mouse1 before shutdown.

Any ideas?

---

### Post by DuKe2112 on 2008-01-22
Id like a repost of the completed and corrected tutorial as way.

But first another issue:
Subversion refuses to download the driver source, because the server certificate expired. How can I bypass this check?

---

### Post by luopio on 2008-01-23
To those of you who haven't heard about the late developments, I suggest you check these threads on the Aiptektablet mailing list: [http://sourceforge.net/mailarchive/forum.php?thread_name=200801162121.03768.peterthevicar%40users.sourceforge.net&forum_name=aiptektablet-users](http://sourceforge.net/mailarchive/forum.php?thread_name=200801162121.03768.peterthevicar%40users.sourceforge.net&forum_name=aiptektablet-users)
[http://sourceforge.net/mailarchive/forum.php?thread_name=1200405699.3776.31.camel%40lrlscs29&forum_name=aiptektablet-users](http://sourceforge.net/mailarchive/forum.php?thread_name=1200405699.3776.31.camel%40lrlscs29&forum_name=aiptektablet-users)

It's the message I've been waiting for years. Finally the tablet should be working out of the box with Xorg 7.3 and a newish kernel.

---

### Post by DuKe2112 on 2008-01-23
With the speed Ubuntu usually updates its packages we could expect this to be included in 9.04.... /sarcasm off.
Sry I'm a bit tired of having to compile a lot my software myself, because Gutsy cointains still the same version Dapper did.

Anyway could someone please post at least a short (but complete) guide on how to make it work now in Gutsy?

Thanks.

---

### Post by celticbhoy on 2008-01-24
I agree it would be helpfull

---

### Post by DuKe2112 on 2008-02-03
Finally figured some things out.
Ok, thats how I got mine working somewhat in Gutsy:

1. Check your sources list and make sure that Ubuntu sourcecodes is activated.

2.Obtain development system.
 ```
sudo apt-get install build-essential linux-headers-generic subversion linux-source
```

3. Install kernel module.
```

mkdir aiptek
cd aiptek
svn co https://aiptektablet.svn.sourceforge.net/svnroot/aiptektablet/trunk/linux_kernel_drivers/2.6 aiptekkernel
cd aiptekkernel
make

cp /lib/modules/$(uname -r)/kernel/drivers/input/tablet/aiptek.ko aiptek.ko.old
sudo cp aiptek.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
```

4. Install XServer module.
```
sudo apt-get xserver-xorg-input-aiptek
```
(if you have one of the older tablets with serial input, you might have to use this:
```
sudo apt-get xserver-xorg-input-hyperpen
```

Note: This version is even newer then that of SVN, because it has some patch I think.

6. Make a Udev rule.
```
sudo gedit /etc/udev/rules.d/66-aiptek.rules
```

insert the following:
```
# udev rule for aiptek tablets

KERNEL=="event[0-9]*", SYSFS{vendor_id}=="0x08ca", SYMLINK+="input/aiptek"
```

Save the file and restart your system.
(A complete reboot might not be nessesary, but it assures that all modules get loaded.)

7. Testing the Tablet.
At this stage my pointer was already responding to the tablet although rather wonky.

You can get some info with this:
```
udevinfo -a -p $(udevinfo -q path -n /dev/input/aiptek)
```

or test it with evtest:
```
sudo apt-get install dvb-utils
sudo evtest /dev/input/aiptek
```

8. Configuration
This is the part I don't get right now.

I have an old 6000U with USB.

With my standart xorg.conf the tablet reacts strange (I have an absolut area on my tablet that moves around when I come too close to the edges).
But its usable and the left- and rightclick work fine.

When I change the config as mentioned my Pointer reacts just perfectly, but The clicks get stuck on the down operation never recieving an up.
Additionally both my Mouse and my Touchpad are disabled.

here is my xorg.conf:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mouse1"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"1"
EndSection

Section "InputDevice"
 Identifier "pen"
 Driver "aiptek"
 Option "Device" "/dev/input/aiptek"
 Option "Type" "stylus"
 Option "Mode" "absolute"
 Option "Cursor" "stylus"
 Option "Mode" "absolute"
 Option "PressCurve" "0,5,95,100"
 Option "zMin" "0"
 Option "zMax" "512"
 Option "ZThreshold" "0"
 Option "USB" "on" 
 Option "KeepShape" "on"
 Option "debuglevel" "0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection 	"Display"
	Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice 	"Configured Mouse" "CorePointer"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice 	"pen" "AlwaysCore"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

I hope someone can help me.

---

### Post by luopio on 2008-02-04
IIRC the post about the new *working* configurations are for Xorg7.3. Anyway you need to have both: the kernel driver and the xorg driver updated. Now you're running an old Xorg-driver.

If you have 7.10 then you're running Xorg7.2. You might try to compile the new driver (I think the patches can be found from a bug report for Xorg), but as it's intented for 7.3, I'd say the safest bet is to wait for 8.04.

---

### Post by DuKe2112 on 2008-02-04
Yeah 7.3 is supposed to support these tablets out of the box, but the only real issue with 7.2 is that some apps might crash, but Puru posted the patch for that.

At least I couldn't find a newer aiptek driver then 1.0.1-3 and others got their tablet working correctly with that.

So the only thing I'm missing is probably the correct configuration.

And since updates are known for not updating config files I would probably need these configurations anyway.

---

### Post by celticbhoy on 2008-02-05
Package linux-kernel-headers is a virtual package provided by:
  linux-libc-dev 2.6.22-14.51
You should explicitly select one to install.
E: Package linux-kernel-headers has no installation candidate

Getting the above on the first instruction from duke2112's sugestion - any ideas

---

### Post by DuKe2112 on 2008-02-06
Ah sry, misscopied that from the first post. The correct package should be linux-headers-generic or just linux-generic for the complete kernel.

---

### Post by Puru on 2008-02-21
Time to repatch your xserver-xorg-core package: a recent upgrade installed an unpatched version. If you still hold your previously patched .deb, you can reinstall it, it will still work; the updater will try to keep it up to date (it's just his job, he said) so be aware! :)

---

### Post by celticbhoy on 2008-02-23
Does anyone know if the new 7.3 will support these tablets, and if it will ship with 8.04 yet ??

---

### Post by hva on 2008-04-02
i've been trying aiptek hyperpen 12000U on hardy beta with no luck:
seems to send events but xorg doesn't react at all.
as it works quite nicely with feisty, this is going to stop me from upgrade...
that's a pity.

---

### Post by bmcage on 2008-04-07
The aiptek driver is now in latest linux tree, and in latest Xorg. 
My guess is Hardy does not use the bleeding edge though, it will be a LTS version of Ubuntu. So you will need to patch and compile stuff to get it to work. 

The guidelines to do that for Feisty at the start of this thread will no longer apply, so if you can't figure it out how to do it, I'm afraid you'll have to wait untill somebody has who has the required skills tries it on Hardy. 
I know a Gentoo user got the latest versions of the drivers: [http://gentoo-wiki.com/HOWTO_Aiptek_Tablet](http://gentoo-wiki.com/HOWTO_Aiptek_Tablet)

So, give it another 6 months, and the tablet will work out of the box on linux, requiring only an xorg.conf change to make them work with pressure sensitivity.

---

### Post by hva on 2008-04-15
i've progressed a bit with aiptek tablet on hardy, but still have problems:
hardy's kernel driver seem to work well, udev rules syntax should have changed a bit (old rule to create symlink didn't work anymore), i took my new one from here, as suggested in previous post: [http://gentoo-wiki.com/HOWTO_Aiptek_Tablet](http://gentoo-wiki.com/HOWTO_Aiptek_Tablet).
Then i had to fiddle with xorg.conf: it seems "AlwaysCore" option somehow prevents the tablet to send core events, while "SendCoreEvents" option seems to do the job.
When i start gdm, X starts well, and on gdm login screen i can move cursor with the pen tablet, and it correctly works in absolute mode, screen coords are correctly mapped.
Then it comes the problem: after i type login id and password the login process starts and suddenly Xorg segfaults and gdm is restarted.
I've tried to compile aiptek xorg-input driver from git repo, but the behavior is exactly the same.
Segfault of xorg happens only when pen is enabled in xorg.conf, but strangely only after the gdm login has been made. I've haven't tried to trace it back yet, but i'm not sure that the bug is related to aiptek driver, i suspect it's something else just triggered by the presence of the pen, because on login screen it works perfectly.
Will try to investigate a bit further, but i'm probably not skilled enough to debug it.
[B]
UPDATE:[/B]

Ok, i got it working somehow... i can officially state that aiptek tablets work under Hardy
not exactly out of the box on my system, but anyway...
When i login through gdm it still keeps on segfaulting Xorg... i couldn't investigate the cause, but i suppose is something in the way gdm manages the gnome session.
to get a gnome desktop working with the aiptek tablet i have to do the following:
-shut gdm down
-start X from console
-start an xterm on X
-from the xterm i call gnome-session
Then i have my gnome desktop perfectly loaded, with pen working in absolute mode, and perfect pressure sensitivity in inkscape and gimp.
I don't really know what the problem in gdm can be, and i'm not sure how to fix it... maybe it's something related specifically to my system (i'm testing on an old geforge NVIDIA card)
Hope someone with an aiptek tablet can do some testing on a Ubuntu Hardy and see if my problem can be reproduced...
At least i can hope to get everything working soon.

---

### Post by pierric on 2008-05-03
Hi!

I can confirm I have (almost) the same symptoms as you.

- Aiptek HyperPen 12000U tablet
- Up-to-date Hardy Heron, no patch whatsoever applied for the tablet

When I uncomment my Aiptek line in the server layout part of xorg.conf, if there's AlwaysCore then X runs fine but the tablet doesnt work. Without AlwaysCore, the tablet works in gdm, but when I log in, X crashes instantly and I get back to gdm.

However when I try your trick (I go to a text console, do a killall gdm, put an "xterm" in my .xinitrc and run startx or xinit), I get the terminal open in X, and then enter gnome-session, but then... instead of getting my system working, it just crashes to a blank screen with blinking cursor and no text, and my PC is frozen. I can't change consoles or whatever, it seems to be like a panic! just without the panic! text... I can only press the reset button (ctrl-alt-suppr wont work either).

So I'm stuck... and I need my tablet bad... I was sure the worst thing that could happen when upgrading would be to need to redo the same procedure as last time (was the case when I moved from 7.04 to 7.10). I hope someone will find a solution :-(

UPDATE:
By the way when I have my xterm running on nothing before trying to launch gnome-session, the tablet works. So to me it looks like a gnome problem, or a problem linked to whatever is launched at the same time.

The errors in the X log are strange, they seem to correspond to keyboard mapping stuff. Here's my backtrace from the Xorg.0.log.old file:

------------------
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f96420]
2: /usr/bin/X(XkbApplyMappingChange+0x1b9) [0x8190cd9]
3: /usr/bin/X(SendDeviceMappingNotify+0xe3) [0x81744d3]
4: /usr/bin/X(ProcChangeKeyboardMapping+0x218) [0x8085428]
5: /usr/bin/X [0x815075e]
6: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
7: /usr/bin/X(main+0x48b) [0x807471b]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d28450]
9: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting
-------------------

UPDATE 2:
I've tested with Fluxbox started from an xterm, and it works. So I'm pretty convinced now that it's not GDM but Gnome...

Cheers,
Pierric.

---

### Post by bmcage on 2008-05-05
Is hardy on xorg 7.3? See [http://gentoo-wiki.com/HOWTO_Advanced_Mouse#Upgrading_to_XOrg_7.3_or_higher](http://gentoo-wiki.com/HOWTO_Advanced_Mouse#Upgrading_to_XOrg_7.3_or_higher)

So indeed, alwayscore is deprecated. You need a CorePointer device in the ServerLayout, and then the aiptedkpen as SendCoreEvents.

I'll upgrade to Hardy in a month or so and hopefully have some success.

---

### Post by TameLion on 2008-05-27
> **Coffeebot said:**
> 
Question, though -- while it works beautifully, X crashes at boot if I don't have the tablet plugged in. Since I'm working on a laptop, having the tablet plugged in all the time isn't an option. I'm also using a usb mouse as my input, ignoring my synaptic. For whatever reason, if I have the tablet installed, my USB mouse is /dev/input/mouse4, the tablet is mouse2, and synaptic pad is mouse 3. Without the tablet, the usb mouse is mouse2, synaptic mouse3.

I'm sure there's a trick to get this to work, but I'm no X expert. Thoughts?



As it notes at the bottom of the Ubuntu page [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) and as pointed out in Coffeebot's earlier post (above), Xorg will not run when the tablet is unplugged.

I was thinking.. would it be possible to create a UDEV rule (again using the vendor ID) for your standard mouse as well, i.e. to link it to /dev/input/stdmouse or some such and then add this in place of the /dev/input/mouseX which is likely to change when the tablet is not plugged in?

I know it's not an elegant fix and I can't try it until the weekend, but can anyone see why this wouldn't work?

---

### Post by pierric on 2008-06-19
Hi,

What I've done is link against the "by-id" file in my xorg.conf. It looks like this:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/by-id/usb-Microsoft_Microsoft_Wireless_Laser_Mouse_8000_00125A5A013F-mouse"
etc.

It's not pretty but it's a one-off, it will work until you change your mouse :-)

Did anyone get Gnome+Hardy+Aiptek to work together? :-(

---

### Post by hva on 2008-06-20
ok, i was forced to switch my main workstation to hardy (due to a disk failure), and i had the nice surprise to find out that my tablet is perfectly working with gnome as well.
Seems previous problem has been fixed (though i'm on a different machine, haven't tried yet to update the one i had previously tested on).
I identified the mouse using the 'by-path' trick (dirty but works).
Good new is that behaviour seems much more stable than i had experienced in feisty, no more random crashes in applications or xserver, and i've started to use my tablet even in time-critical works. pressure is working and fine.
i think we're at it.
i include my xorg.conf and the udev rules i use for my tablet.
(remember to install xerver-xorg-input-aiptek package anyway)

---

### Post by Stratagem on 2008-06-20
Hi, I'm new and crazy confused about installing my Aiptek tablet on Hardy. Seven pages in a thread is kinda hard to follow, and everything went great when I followed the instructions until I had to edit xorg.conf which I couldn't for some reason. It gave me something like "You don't have permission to edit this file."

So, uh, if anyone could, please, please, PUH-LEASE help, thank you, thank, thank you in advance!!

Actually, I'm stuck here:

```
GNU Make 3.81 found
you need autoconfig (2.58+ recommended) to generate the Makefile
```

---

### Post by hva on 2008-06-21
> **Stratagem said:**
> Hi, I'm new and crazy confused about installing my Aiptek tablet on Hardy. Seven pages in a thread is kinda hard to follow, and everything went great when I followed the instructions until I had to edit xorg.conf which I couldn't for some reason. It gave me something like "You don't have permission to edit this file."

So, uh, if anyone could, please, please, PUH-LEASE help, thank you, thank, thank you in advance!!

Actually, I'm stuck here:

```
GNU Make 3.81 found
you need autoconfig (2.58+ recommended) to generate the Makefile
```


In hardy you're not supposed to compile anything in order to have your aiptek tablet working: kernel module comes with hardy and it's ok,
just do

sudo apt-get install xserver-xorg-input-aiptek

and then you have to tweak xorg.conf in order to make configured default mouse to point just to your mouse and not to tablet
(that's the "by-id" or "by-path" trick, or similar), and of course you must add tablet entry (that's the "pen" part").
next step is to write a udev rule in order to have udev write a proper symlink to the event identifier of your tablet.
Then it's supposed to work. you can take as a reference the two files i attached to my previous post, seem to be working perfectly for me.

how are you trying to edit xorg.conf?
you must have administrator privileges to have write permission on system files, try (from a terminal)

[SIZE="3"]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig[/SIZE] (this makes a backup copy of original file, just in case something goes wrong)
[SIZE="3"]sudo gedit /etc/X11/xorg.conf[/SIZE]
then you should be able to save modified version from gedit

but be careful, old tutorials are not accurate anymore due to hardy use of xorg 7.3, there are some differences.
Maybe when i have time i'll write myself a new little tutorial for aiptek tablets on hardy.

---

### Post by sulligogs on 2008-06-23
Hi everybody,

I feel a bit out of place because I'm a Debian Lenny user.  I've had a dusty Trust TB-3100 graphics tablet connected to my desktop for the past several months when all of a sudden I decided to get back to drawing.  As this thread seems to be more active than any other I've come across I would really appreciate any help you could give.

Firstly, I'm using the 2.6.24-1-686 kernel with X.Org version 1.4.0.90 (does that relate to X11R7.3 at all?) and doing an "lsusb" at a root terminal reported :-

```

Bus 001 Device 002: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet

```So I guess it is a rebranded Aiptek model.

Initially, without any system modification, I found that the graphics tablet would work perfectly well in my Gnome Desktop.  Cursor was fully functional and the buttons would act like mouse buttons.  However, I couldn't configure it under The Gimp or Inkscape.

So, I hunted around the web and found that I should have a udev rule, along with the xorg-xserver-input-aiptek module installed. I implemented this and put the following into /etc/udev/rules.d/61-aiptek.rules

```

BUS=="usb", DRIVER=="aiptek", KERNEL=="event[0-9]*", SYMLINK+="input/aiptektablet"
KERNEL=="event[0-9]*", SYSFS{vendor_id}=="0x08ca", SYMLINK+="input/aiptektablet"

```Then I restarted udev with

```

/etc/init.d/udev restart

```only to find that no such device file named "aiptektablet" had even been created and after a reboot GDM refused to start.

So, I had a look at the other devices in /dev/input and found that there were device files for "mouse0" and "mouse1".  I unplugged the graphics tablet and sure enough mouse1 vanished.  So, I worked out that mouse1 may have been the device file being used for the graphics tablet.

Changing the SYMLINKs in the above to "mouse1" made the X server start, but wtihout any input from the graphics tablet, even after a reboot.

So!  I then came across this thread.  I've copied 85-aiptek.rules into /etc/udev/rules.d and made the changes to my xorg.conf as provided by hva.  Yet, I still can't get the device files I need and X Server still bombs to a terminal screen.

What would I be doing wrong?  It's driving me mad!

Any thanks would be greatly appreciated.

Sulligogs

---

### Post by pierric on 2008-06-28
> **hva said:**
> ok, i was forced to switch my main workstation to hardy (due to a disk failure), and i had the nice surprise to find out that my tablet is perfectly working with gnome as well.
Seems previous problem has been fixed (though i'm on a different machine, haven't tried yet to update the one i had previously tested on).
I identified the mouse using the 'by-path' trick (dirty but works).
Good new is that behaviour seems much more stable than i had experienced in feisty, no more random crashes in applications or xserver, and i've started to use my tablet even in time-critical works. pressure is working and fine.
i think we're at it.
i include my xorg.conf and the udev rules i use for my tablet.
(remember to install xerver-xorg-input-aiptek package anyway)

Congratulations on getting your tablet working! On my side, I still have the issue :-(
I checked your files and they're similar to mine, except for the fact that in udev I had some user=root and mode=666 or something. I removed that but the system still freezes on a black screen with blinking cursor when I run "gnome-session". With Fluxbox, no problem...
Now that you have your problem fixed, it probably means I'm alone in this situation and my hopes for a resolution vanished! Well, I'll do a complete new install when the next Ubuntu is released, maybe that will help...

---

### Post by happymellon on 2008-07-04
> **pierric said:**
> Congratulations on getting your tablet working! On my side, I still have the issue :-(
I checked your files and they're similar to mine, except for the fact that in udev I had some user=root and mode=666 or something. I removed that but the system still freezes on a black screen with blinking cursor when I run "gnome-session". With Fluxbox, no problem...
Now that you have your problem fixed, it probably means I'm alone in this situation and my hopes for a resolution vanished! Well, I'll do a complete new install when the next Ubuntu is released, maybe that will help...

So on Hardy, you installed the xserver-xorg-input-aiptek, and updated your xorg.conf, and this crashes your gnome session?

That's odd, and not quite the issue I'm having ;)
after doing those two steps, x doesn't give me any issues... BUT the tablet does not move the cursor around. My x log shows that the aiptek driver loads successfully, and I can cat my /dev/input/aiptek and get loads of garbage by moving the stylus around. But in X, it doesn't move unless I'm pressing on one of the mouse buttons on the side. I'm assuming that means I have a setting wrong. But I can't figure out what.

---

### Post by hva on 2008-07-05
> **happymellon said:**
> So on Hardy, you installed the xserver-xorg-input-aiptek, and updated your xorg.conf, and this crashes your gnome session?

That's odd, and not quite the issue I'm having ;)
after doing those two steps, x doesn't give me any issues... BUT the tablet does not move the cursor around. My x log shows that the aiptek driver loads successfully, and I can cat my /dev/input/aiptek and get loads of garbage by moving the stylus around. But in X, it doesn't move unless I'm pressing on one of the mouse buttons on the side. I'm assuming that means I have a setting wrong. But I can't figure out what.

can you post you xorg.conf?

---

### Post by happymellon on 2008-07-05
> **hva said:**
> can you post you xorg.conf?

Sure, here it is. Any ideas?

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse1"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"aiptek"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/aiptek"
	Option "Type" "stylus"
	Option "Mode" "absolute"
	Option "Cursor" "stylus"
	Option "Mode" "absolute"
	Option "PressCurve" "0,5,95,100"
	Option "zMin" "0"
	Option "zMax" "512"
	Option "ZThreshold" "0"
	Option "USB" "on" 
	Option "KeepShape" "on"
	Option "debuglevel" "0"
	Option "SendCoreEvents" "on"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by hva on 2008-07-05
i'd try to replace the identifier for the tablet from "stylus" to "pen" both in inputdevice and layout sections, don't know it it helps, but is the first thing i can think about.

---

### Post by happymellon on 2008-07-05
> **hva said:**
> i'd try to replace the identifier for the tablet from "stylus" to "pen" both in inputdevice and layout sections, don't know it it helps, but is the first thing i can think about.

Yup, tried that. Nothing different. Do you know how I can remap buttons? I am starting to suspect that since it only works when I press the button on the side, it is mapping the nib to button one. Double mapping the button to two functions as it also highlights at the same time.

---

### Post by hva on 2008-07-07
> **pierric said:**
> Congratulations on getting your tablet working! On my side, I still have the issue :-(
I checked your files and they're similar to mine, except for the fact that in udev I had some user=root and mode=666 or something. I removed that but the system still freezes on a black screen with blinking cursor when I run "gnome-session". With Fluxbox, no problem...
Now that you have your problem fixed, it probably means I'm alone in this situation and my hopes for a resolution vanished! Well, I'll do a complete new install when the next Ubuntu is released, maybe that will help...

i think i have good news: i've installed k3b today (the kde cd-dvd burning suite) and all in a sudden my xorg segfault with the tablet reappeared.
Removing k3b and its dependencies fixed it and gave me my working desktop again.
So now we can find the guilty boy. it must be something in k3b dependencies, one of the packets. i can't say which one, but it's only a matter of trying them one by one i suppose. maybe it can fix your issue as well.
it's one on this list:

k3b
kdebase-bin
kdebase-bin-kde3
kdelibs-data
kdelibs4c2a
libarts1c2a
libartsc0
libavahi-qt3-1
libdbus-qt-1-1c2
libflac++6
libk3b2

---

### Post by bmcage on 2008-07-14
My guess would be the dbus qt package, as the rest should not touch the aptek things

---

### Post by pierric on 2008-08-03
Hi!

Thanks to all for your help. I've tried uninstalling libdbus-qt, but it changes nothing. And k3b is not installed.

By the way my crashing issue is not just an Xorg segfault, the PC is completely frozen on a black screen and I have to hit the reset button. :-(

The backtrace is this (I posted it previously, it seems to not have changed a bit):
Backtrace:
0: X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f44420]
2: X(XkbApplyMappingChange+0x1b9) [0x8190d49]
3: X(SendDeviceMappingNotify+0xe3) [0x8174543]
4: X(ProcChangeKeyboardMapping+0x218) [0x8085428]
5: X [0x815076e]
6: X(Dispatch+0x2cf) [0x808d8df]
7: X(main+0x48b) [0x807471b]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cd5450]
9: X(FontFileCompleteXLFD+0x201) [0x8073a91]

It makes me wonder if Gnome could be trying to do a keyboard mapping on my tablet, failing and for some reason crashing the entire OS in the process. But I don't know what to do with that idea...

Open to any further suggestion ...


EDIT: HUGE PROGRESS !!
I googled around on that keyboard mapping lead... and I found this: [http://lists.freedesktop.org/archives/xorg/2007-November/030287.html](http://lists.freedesktop.org/archives/xorg/2007-November/030287.html)
That's a post by someone working on Wacom tablet support, getting exactly the same backtrace as me when trying some xmodmap commands... apparently some bug in X. So I tried looking for anything potentially changing the mapping of the keyboard in my gnome setup... and finally found an old .Xmodmap file in my user directory... which explains why it works when I run gnome as root. Copying the .Xmodmap file to the root directory, Gnome asked me if I wanted to use it on the next load, and when I said yes the PC crashed. So I removed the .Xmodmap file from my user directory.
NOW: it works when I run gnome-session from an empty console when launching xinit without Gdm. However, with gdm, I get the same issue as you had before, hva: X segfaults and gdm shows up again. It's strange that the problem got solved on its own for you and not for me... since my Hardy is up to date... any idea ?

Thanks,
Pierric.

---

### Post by pierric on 2008-08-04
It works !!!!

Stubbornness finally paid. Based on the link I found in my previous post, I downloaded the source code for the wacom tablet support. I found the keysyms data used with that InitKeyClassDeviceStruct function. Indeed in the most recent version of their code, they define 255 key symbols, most of them with a value of NoSymbol.

I downloaded again the source code of the aiptek driver:
```
sudo apt-get source xserver-xorg-input-aiptek
```

I went in there again and compared with the wacom project. For aiptek they only define 32 symbols. So I changed in xf86Aiptek.c:
```
  aiptek_map,   8,          0x27,   1
```  
into
```
  aiptek_map,   8,          0xFF,   1
```

And above in the file, I changed the last line of the aiptek_map data:
```
    XK_F25, XK_F26, XK_F27, XK_F28, XK_F29, XK_F30, XK_F31, XK_F32
```
into:
 ```
   XK_F25, XK_F26, XK_F27, XK_F28, XK_F29, XK_F30, XK_F31, XK_F32,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,
    NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol,NoSymbol

```
To have 255 symbols.

The wacom project have a "size" of 2 in their keysyms data, whereas aiptek have 1. I've left it at 1.

Then I recompiled, reinstalled:
```
sudo ./configure --prefix=/usr/
sudo make
sudo make install
```

(of course I previously got a safety download of the original package:
```
sudo aptitude download xserver-xorg-input-aiptek
```
)

And that was it. It works fine now, I can log directly from gdm and enjoy an apparently stable tablet !!!

Now I just need to rebuild the package properly to avoid having ubuntu telling me to update all the time (I played with checkinstall, which might have broken that). But it's a detail...

---

### Post by hva on 2008-08-07
good job!

---

### Post by bmcage on 2008-08-11
Pierrec, 

I think you should do a bug submission with patch to xorg so as to resolve this upstream. Do this at [https://bugs.freedesktop.org](https://bugs.freedesktop.org) 

Thanks in advance ;-D

---

### Post by sandos on 2008-10-25
Perfect, the patch makes it work! My X started crashing as soon as I managed to configure everything correctly, but this helped.

I just guessed this was the problem, my backtrace seemed to not be in any logs and it scrolled of my screen.

---

### Post by waldeck on 2008-10-29
Hi all,

I just got a Trust Wireless Scroll Tablet TB-4200 in the mail and I spent the day installing and configuring in on Hardy. I found this thread to be most helpful in getting it to mostly work. However, a few things are still bothering me:

1. It seems that my absolute area will slide everytime I get close to the borders. The driver reports the size of the drawing area to be 6000x4500 (aspect ratio 1.333) while my screen is 1280x800 (aspect ratio 1.6). The xorg driver knows about the different aspect ratios, but apparently is not making any sense of it. I tried setting the xMax/xMin, xOffset, etc, as suggested on this thread to no avail.

2. The pen is a bit jittery and it is a bit hard to draw straight lines or to make fluid movements. I know this is not anything like the wacom tablet I used before, but I was expecting it to be more stable. If II keep the pen steady, I can see the pointer shivers. Perhaps adding  a signal filter to the driver could help, althoug it would introduce a slight delay in the movements. I could do this if I knew how to compile/install the driver (I'm a mathematician and I know a bit about signal processing :-), but unfortunately I know very little about linux device drivers :-( ).

3. Loss of registration. This is perhaps related to (1). If I mark two points on a piece of paper and use the stylus to mark those two points on the graphic canvas, then after moving the stylus around for a little while, then the points on the paper and those on the canvas do not match anymore.

I tested the tablet on XP with the bundled drivers and it works fine, without any of the above issues.

My udev rules and xorg config are as described in this thread. All in all, the tablet seems quite usable, but I would very much like to see these issues solved.

Is anybody else experiencing these problems?

Regards,
Waldeck

PS: tried this on intrepid and xorg will crash after login on gdm just as reported on this thread.

---

### Post by 080812jk on 2008-10-30
Nihilum, [**wow gold**](http://www.oofay.com/)famed Horde guild on Magtheridon EU, will be running a second live, cheap [**wow gold**](http://www.oofay.com/)streaming raid on the Sunwell Plateau this month. Partnering with Xfire, Nihilum is set to provide the entire raid in real-time, cheap [**wow gold**](http://www.oofay.com/)through your browser with the Dyyno plug-in. Choose your favorite class and watch the raid through the eyes and screens of a Warrior, Druid, cheap [**wow gold**](http://www.oofay.com/)or Warlock from the guild. [**world of warcraft gold**](http://www.oofay.com/)(Choose wisely because you can't switch later.)

---

### Post by waldeck on 2008-10-30
Just to complement my previous post, I ran some experiments on data I captured from my tablet and the following pictures show the results of raw versus filtered data. The filter is adaptive of variable order and its implementation is rather straightforward.

[IMG]http://www.dm.ufscar.br/profs/waldeck/adaptive-filtering-of-tablet-data.png[/IMG]

[IMG]http://www.dm.ufscar.br/profs/waldeck/adaptive-filtering-of-tablet-data-1.png[/IMG]

Would anyone care to implement it in the driver? Perhaps it could also be implemented as a pipe from /dev/input/aiptektablet to the xorg driver, this would allow one to use the filter or not simply by inserting or removing the pipe in the filesystem. Would it be possible?

Seems like wacom performance on a budget! :-)

Cheers,
Waldeck

---

### Post by bmcage on 2008-11-03
Waldeck, you should write to the aiptek driver project on sourceforge for this. This is just the Ubuntu forum about getting it to work in ubuntu. The device driver devels are not reading this.

---

### Post by waldeck on 2008-11-03
> **bmcage said:**
> Waldeck, you should write to the aiptek driver project on sourceforge for this. This is just the Ubuntu forum about getting it to work in ubuntu. The device driver devels are not reading this.

Thank you, bmcage.

I'll be doing that shortly. Meanwhile I dug into the sources and I found how to compile the driver. I made a patch and the tests look promissing. I hope that the driver devel team will find it interesting.

Waldeck

Edit: that project seems to be stalled. The aiptek-devel mailing list has no new message since 2006. I was suspecting it since the reported driver version 2.3 dates back to 2007. Is this correct?

---

### Post by link141 on 2008-11-03
> 
1. It seems that my absolute area will slide everytime I get close to the borders. The driver reports the size of the drawing area to be 6000x4500...

6000x4500 seems way too high, if the driver is telling the device to do this resolution, or if the driver is mishandling the data, it will give you sloppy data.

Supposedly, all of the third party tablets that are based off aipteks are really Hyperpen 12000Us.  I have a Hyperpen 12000U and the max drawing area in pixels for these tablets is 1280x1024.

Maybe the driver is scaling a very small area on the tablet up to a significantly larger area on the screen.  If so, then the output would be very jagged and aliased (as would be the case if you zoomed in on a low res image).

Also, there should be no scrolling if the tablet is really in absolute mode...  I ( and many other people ) were having problems with this tablet being set as a mouse.  I noticed that the tracking on my tablet was messed up when this happened, so this is another possible reason for the jagged tracking of the pen.

I would think that the driver programmers shouldn't have to compensate for bad hardware tracking...  It's best to get accurate, reliable data straight from the device, and process it minimally.  If the hardware had that bad of tracking, it wouldn't be good enough to draw with...
>  
 2. The pen is a bit jittery and it is a bit hard to draw straight lines or to make fluid movements...

See above...

> 
 3. Loss of registration. This is perhaps related to (1)...
I would think that this would only happen if the tablet was in 'relative mode'...

In my experience, these tablets are just as good as the over-priced Wacoms.  My sister compared our 12000U to a Wacom at school and said that the tracking was equivalent, if not better.  For the same price as one of the post-card size wacoms, you can get a full-sized tablet.

I didn't expect someone to talk about (much less implement) a signal filter into the aiptek driver.  This forum attracts many extremely intelligent people ;).

---

### Post by waldeck on 2008-11-03
Hi link141,

Thank you for the response. I'm new on the tablet business and I used only a Wacom Graphire4 tablet before, but I'm quite confident that my new Trust tablet will work well enough for me if those issues can be solved.

Looking in the driver code, I can see that it sets the resolution to 500LPI no matter what tabled is plugged in. Since my tablet is 12x9 inches, this explains why I'm getting the 6000x4500 size right off from the hardware.

It is interesting that my is the second one on the list hard-coded in the driver:```

static const struct usb_device_id aiptek_ids[] = {
        {USB_DEVICE(USB_VENDOR_ID_AIPTEK, 0x01)},
        {USB_DEVICE(USB_VENDOR_ID_AIPTEK, 0x10)}, <-----------------  
        {USB_DEVICE(USB_VENDOR_ID_AIPTEK, 0x20)},
        {USB_DEVICE(USB_VENDOR_ID_AIPTEK, 0x21)},
        {USB_DEVICE(USB_VENDOR_ID_AIPTEK, 0x22)},
        {USB_DEVICE(USB_VENDOR_ID_AIPTEK, 0x23)},
        {USB_DEVICE(USB_VENDOR_ID_AIPTEK, 0x24)},
        {}
};
```


So perhaps this particular tablet is not suitable for a 500LPI resolution and should be set to, say, to about 100LPI instead. This would be close to 1280x1024, actually a little bit less, and perhaps would solve part of the jaggedness. Unfortunately, the documentation in the driver does not tell how to change the resolution. I would assume it is possible since there is a command for doing it.

[COLOR="Silver"]I'm probably setting the pen as a mouse on my system. How can I avoid it? And in that case what has to be done in the programs so they'll recognize the tablet?
[/COLOR]
As to the filtering, I do not see why would it hurt if we did some modest filtering in the software. This could otherwise help improve even further the tracking performance and help out those who have a poorer hardware. I develop hardware (microcontrollers) and often leave to the firmware most of the task that was traditionally done in the hardware. It is not only cheaper but also allows for smaller hardware sizes that are easier to maintain. So, why not?

Thanks again,
Waldeck

*Edit*: I tried setting the resolution to 100LPI in the driver by changing the following lines:```
        /* Execute Resolution500LPI */
        if ((ret = aiptek_command(aiptek, 0x18, 0x00)) < 0) /* changed the 0x04 into 0x00 to get 100LPI */
                return ret;

```

The strange thing is that now the tablet reports its size to be 1200x900 but as evtest shows the coordinates are still coming out in the broader range of 6000x4500 instead.

*Edit #2*: I made several tests with fake resolutions by tweaking the driver. Even when I set the resolution to match my screen (1280x800), there was no difference in the sliding of the working area. As the output of evtest suggests, the driver is reporting its tracking consistently. This lead me to suspect that the problem is somewhere inside the xorg driver.

*Edit #3*: Choosing the mouse as the CorePointer and enabling the pen in applications seems to work quite well, without sliding or registration problems. As to the jaggedness, this particular tablet does not seem to do a great job, and the filter I implemented really makes a big difference. The lines become noticeably smoother with it. Too bad it cannot work well as a mouse too. Is there any workaround?

---

### Post by waldeck on 2008-11-04
Hi link141,

I have the tablet working well with Gimp and InkScape, but it bothers me that there's no visual confirmation to the pen position, since there's no other pointer on the screen. Do I have to set this visibility somewhere else?

Thanks,
Waldeck

---

### Post by link141 on 2008-11-08
> As to the filtering, I do not see why would it hurt if we did some modest filtering in the software. This could otherwise help improve even further the tracking performance and help out those who have a poorer hardware. I develop hardware (microcontrollers) and often leave to the firmware most of the task that was traditionally done in the hardware. It is not only cheaper but also allows for smaller hardware sizes that are easier to maintain. So, why not?

Interesting, I didn't realize they did this...

Sorry for not responding too fast, I've been kind of busy.

The pointer is supposed to follow the tracking of the pen.  It disappears if you don't hold the pen close enough to the tablet (or if the tablet doesn't pick up the pen).  I remember there being a setting for how close the pen has to be to the tablet to pick it up, something like 5mm or 10mm (although it's hard-coded into the driver).  Either that, or you've found a bug in the driver, (or you're modifications made the pointer disappear somehow...)

I haven't messed around with the tablet for a while, but I will when I get some free time.

Other than that, you say you have the tablet working well with some common apps.  I presume that you're using Hardy.  The last time I seriously went after getting this tablet working (on Gutsy), I mainly had problems with X (even though I recompiled it with the patch) and it not getting the right pressure sensitivity.  Mainly, the pen thought that it was held down against the tablet when it was above it...  I also might have had a small degree of "jagedness", although if I did it wasn't too bad compared to the tablet on Windows.  How is the tablet working for you on Linux compared to Windows?  You might have made better progress than me...

The other day, I tried getting the tablet working on an Intrepid live CD, but I couldn't get it to compile.  The instructions in this thread may need to be updated for intrepid...

Anyway, it seems like you've made a lot of progress.  You're filtering modification seems like it can improve the tracking a lot, and you're also helping a lot of other Linux users, so thanks:D!

---

### Post by steve-ss on 2008-11-08
I'm coming from opensuse to ubuntu because of this thread. I have a 12000U I need to get working. I have the kubuntu 8.10 cd. Absolutely hours of trying different combinations. All google articles seem to be for xorg 7.2 or earlier apart from the gentoo wiki article which is now lost due to a databse fault. Ahggh! I tried the wacom fdi file with references to wacom replaced by references to aiptek instead. restarting hal had no effect on the tablet (which works perfectly as a mouse btw). I'm a bit puzzled as to why you would want to compile the driver as it's already in the kernel. Sorry that this isn't adding much help. I'll offer to test anything though. Does anyone think that it will work with 8.10?

I found that /etc/X11/xorg.conf has no effect on either the mouse nor tablet behavior. I removed all sections which started with Input Device and removed Input device references from the ServerLayout section. 

I created this file in /etc/hal/fdi/policy/10-aiptek.fdi

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<match key="info.product" contains="Aiptek International, Inc. Tablet">
<merge key="input.x11_driver" type="string">aiptek </merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
<merge key="input.x11_options.Type" type="string">stylus </merge>
<merge key="input.x11_options.Mode" type="string">absolute </merge>
</match>
</device>
</deviceinfo>

restarted hal and X

result: both the mouse and pen work just like a mouse. At least it proves that playing around with xorg.conf settings is now pointless.

HTH a little. Cheers. Steve.

---

### Post by link141 on 2008-11-08
The packaged Kernel driver is likely to be out-dated, (it is in Gutsy).  A driver developer came by after months of inactivity, and made some crucial fixes...

The X driver in Intrepid, however, is probably up to date.

Correct me if I'm wrong, but I've noticed that you tend to get better results with certain hardware if you custom compile the drivers on your particular system/hardware...

I think with enough messing around, we will be able to get this tablet working.  Many people had trouble with this tablet when upgrading from Edgy to Feisty and Feisty to Gutsy, but workarounds for these problems were found.

I'm just curious: why did you bypass X and make that file.  Also, what exactly does this file do?  Since the tablet driver has two parts, maybe the X driver only looks at the settings in Xorg, or is only activated if it is referenced in Xorg.conf.

Hope this helps

---

### Post by steve-ss on 2008-11-09
Hi. I don't think xorg.conf has any effect on input devices unless you disable hotplug: [https://wiki.edubuntu.org/X/Config/Input](https://wiki.edubuntu.org/X/Config/Input)

It seems that fdi files control the input these days. I can confirm that by having removed references to input devices from xorg.conf. My file still doesn't work though. It seems that the tablet is still being controlled by evdev mouse driver. Here are the hal input devices I have:

hal-device | grep "input.x11_driver"
  input.x11_driver = 'evdev'  (string)
  input.x11_driver = 'evdev'  (string)
  input.x11_driver = 'aiptek '  (string)

My question is, how can I make the tablet use the aiptek driver rather than evdev? And why do I have two evdev references when I have only a mouse and a tablet connected? **

Cheers, Steve

**Just realised I have a keyboard too. Duh

---

### Post by link141 on 2008-11-09
I think you have to explicitly state which mouse you want to use in xorg.conf instead of /dev/input/mice.  I, and many other people were having problems as it being detected as a mouse...  I'm not sure if this will help, but it's worth a try.

---

### Post by steve-ss on 2008-11-09
I tried using /dev/input/mouse0 when I was still using udev to link /dev/input/aiptek to the correct device. Thanks for the suggestion but no go I'm afraid. The tablet still worked as a mouse. As I said earlier I need a hal guru who can tell me how to stop evdev grabbing the aiptek pen. I'm totally new to ubuntu. I'm wondering if maybe I should ask this question on another forum. Any ideas? TIA.

---

### Post by waldeck on 2008-11-09
Hi link141,

Thank you for your reply to my previous post. I have been seriously digging and changing the aiptek xorg driver for a couple days and I managed to fix the sliding active area problem.

The way I managed this was by making some changes in the code and turning on the xorg.conf option SendCoreEvents instead of AlwaysCore, so the tablet is working as a mouse. The mapping of the tablet to the screen seems perfect to me, but now a rather strange thing is happening: single clicks are always interpreted as doubleclicks!

I am pretty sure that a single xinput event is being generated, judging by the debug messages, so it is really something to do with xorg internals. Unfortunately, the wacom driver source wasn't much helpful, for it is completely different. Aside from this, I see no serious problem at all. Of course it can always work as an extended device, in which case the particular application does its own coordinate mapping and pointer drawing. Gimp sure does it, but it seems that InkScape doesn't.

As to the filtering, the wacom driver does it! so once again, it might be a good idea in aiptek's, at least as an option. But I'll have to move my filter code from the kernel to the xorg driver. Wacom's filter is a simple averaging filter and it is used to smoothen out the noise. However, it seems that a Savitzky-Golay filter would do a much better job there.

For the moment, I have absolutely no clue on this doubleclick issue. Perhaps one of the developers out there could shed some light, but I don't know where they are.

As soon as I can get this tablet nice and working, I'll be posting my patches somewhere for those who are interested.

Cheers,
Waldeck

Edit: I fixed it by making the synaptics touch pad on my notebook the CorePointer. I don't know the reason, but now everything is fine. So now tablet and touchpad are working like mice. And yes, I'm running 8.04 here.

---

### Post by link141 on 2008-11-11
Interesting, I didn't know that Gimp could grab the device directly...

Anyway, it might be better, for the time being, to have the tablet working (in most programs) as a mouse, (although it would be nice to have pressure sensitivity working correctly).  Good job on getting this far, I can't wait for your improvements to make it to the driver;)!

I've found that you're right about the filtering...  I remember having the tablet set up close to our old CRT, and having problems with the tracking...  The tablet also picked up other noise under certain conditions.  Perhaps the Windows driver has a noise filter too. (if it doesn't, the Linux driver will be superior, in true open source fashion :D)

Seeing that Vista is having problems with the tablet, (driver is buggy on Vista) I have more incentive to get it working on Linux.

Anyway, thanks for all of your hard work!

---

### Post by bmcage on 2008-11-12
Waldeck, sorry for not replying earlier. 
Messages are on the user list Aiptektablet-users but I see your message there you noticed that.

About the driver, the kernel driver is in linux since beginning of the year, so patches should now go against the linux branch on the linux devel list somewhere I suppose. 
The X11 driver is in xorg, so also there I believe patches should go to freedesktop.org. I'm not sure Renee merged all the patches from the sourceforge project too X though... 
Kernel and X are not the fastest projects to get patches in, but you can host a git branch I am told ;-)

---

### Post by bmcage on 2008-11-12
About using the tablet as mouse, that worked from the beginning. Point is to be able to use the pressure data in your applications....

I guess I'll have to try to find some time to hook up the tablet too, so I can contribute a bit

---

### Post by hva on 2008-11-19
here we go again! after fighting for a month last year in order to get my aiptek 12000 working in hardy (and it works perfectly, with pressure sensitivity too), today i tried Intrepid live dvd in order to test my workstation for a possible upgrade to new release. Everything worked fine, EXCEPT the tablet.
i tried to use the same  procedures that made it usable in hardy, but no way. It seems it works (badly) as a mouse, using only central part of the tablet, and freezing from time to time, but i coldn't get it working as tablet, nor map coordinates correctly.
THAT'S A DAMN NIGHTMARE!!! every ubuntu release is a new struggle with my tablet. Of course this issue is going to stop me from upgrading: i work everyday with my tablet!
When will it be possible to have this damn tablet working out of the box on linux!!! i'm really tired of this.
Besides, new approach of xorg, with xorg.conf ignored and autoconfiguration stuff and so on, doesn't help at all when you try to configure something. WHERE THE HELL SHOULD I PUT MY HANDS IF I WANT TO CONFIGURE THE F... TABLET???
very bad work ubuntu guys!

---

### Post by steve-ss on 2008-11-21
I do not know why this thread will not accept change. I have had to return to suse for this and other issues I have had with ubuntu.

fwiw you have to use hal with 8.10.

<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Tablet">
     <match key="input.vendor" string="Aiptek International, Inc.">
         <merge key="input.x11_driver" type="string">aiptek</merge>
         <merge key="input.x11_options.USB" type="string">On</merge>
         <merge key="input.x11_options.Type" type="string">stylus</merge>
         <merge key="input.x11_options.Mode" type="string">absolute</merge>
      </match>
    </match>
  </device>
</deviceinfo>

cheers and have a lot of fun. steve.

---

### Post by waldeck on 2008-11-22
Hi folks,

Actually, on ubuntu intrepid, it is best if you created the following file, named 10-aiptek.fdi, in /etc/hal/fdi/policy:

```

<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
    </match>
  </device>
</deviceinfo>

```

Then restart hal and xorg to get it working.

However, I've found that the stock xorg driver is likely to crash upon login if the tablet is plugged in. I'm working on a patch to fix this and other minor things, but I'm not ready to release it yet. You can follow this discussion on the aiptektablet-users mailing list on sourceforge.net.

If clicks and pressure are not working as expected, add the following lines
```

<merge key="input.x11_options.zMin" type="string">0</merge>
<merge key="input.x11_options.zMax" type="string">511</merge>

```
just above the </match> line in the above file, then restart hal and xorg so they'll take effect.

If your tablet has 1024 levels of pressure sensitivity, change that the to 1023, although 511 should work just fine.

Best,
Waldeck

---

### Post by steve-ss on 2008-11-23
Hi
No! I've not been clear I don't think. You only need to write a fdi if the defaults given by the driver to hal aren't acceptable to you. I thought the thread was trying to translate the old xorg 7.2 way to new releases which use hal. As I now understand it, this thread is for users who do not wish to upgrade to the latest version.

Sorry. Steve.

---

### Post by waldeck on 2008-11-23
Hi Steve,

My tablet is a Trust TB-4200 (AFAIK the Aiptek 12000U rebranded) and on ubuntu intrepid I do need to write that fdi file, including the two lines regarding the z limits. Otherwise clicks and pressure do not work and the tablet is misidentified as a keyboard by xorg!

Regards,
Waldeck

---

### Post by bmcage on 2008-11-24
Waldeck, can you edit the ubuntu help? A forum post with manual is really not that great. As people indicate, only the original poster can edit the main post.

So I suggest we edit: [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

I'll start and add your information on HAL

---

### Post by waldeck on 2008-11-24
Hi bmcage,

Thank you for the invitation. I'll be glad to help. :)

Waldeck


> **bmcage said:**
> Waldeck, can you edit the ubuntu help? A forum post with manual is really not that great. As people indicate, only the original poster can edit the main post.

So I suggest we edit: [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

I'll start and add your information on HAL

---

### Post by Smitje on 2008-12-05
Hello tablet users,

I've been checking google on and off for aiptek since Dapper but never been able to get my TRUST  1200-v2 (rebranded aiptek) to work with ubuntu.

However your recent activity has given me hope, so I installed 8.10 intrepid and followed the above instructions. (created the .fdi file) But now nothing happens. I used to get some movement when I pluged in but now the pen does nothing (it is reccognized by the tablet the green light stops blinking)

allso the following leads me to believe that the tablet is being reccognized.

```

qwe@rty-desktop:~$ dmesg |grep aiptek
[   23.975432] aiptek: input: Aiptek using 400 ms programming speed
[   24.020127] usbcore: registered new interface driver aiptek
[   24.020150] aiptek: v2.3 (May 2, 2007): Bryan W. Headley/Chris Atenasio/Cedric Brun/Rene van Paassen
[   24.020153] aiptek: Aiptek HyperPen USB Tablet Driver (Linux 2.6.x)
qwe@rty-desktop:~$ 

```

any ideas what I can try.

cheers,
Smitje

running Ubuntu intrapid 8.10 on amd64 dual core system

---

### Post by simtaalo on 2008-12-15
i've been having trouble getting my trust work tablet 400 to run, a rebranded Aiptek 8000U.

i made this thread [http://ubuntuforums.org/showthread.php?t=1011582](http://ubuntuforums.org/showthread.php?t=1011582)
can anyone help?

---

### Post by Puru on 2008-12-26
works!

created waldeck's .fdi, installed package xserver-input-aiptek, restarted hal and xorg, plugged the tablet (trust 400 v2), got pressure! :)

@simtaalo, Smitje: may sound silly, check wether you have xserver-input-aiptek installed, I took it for sure but it's not shipped by default.

edit: yeah, crashing on login when tablet's plugged! :(
I'll wait for this patch release, and plug it on the fly until then.

---

### Post by simtaalo on 2008-12-26
> **Puru said:**
> 
@simtaalo, Smitje: may sound silly, check wether you have xserver-input-aiptek installed, I took it for sure but it's not shipped by default.


nope that wasn't the problem. made sure it was installed and then reset n the plugged in tablet to see if it made any difference. still couldn't find it in list of devices in gimp.

---

### Post by Coffeebot on 2008-12-31
First off...thanks to everyone who's been working hard to keep the aiptek tablets alive and well :)

I'm having a similar problem to others above, where the tablet maps to the screen beautifully, but it doesn't do left or right clicks. I can see it in GIMP, too, but cannot reassign any of the buttons.

I've "installed" waldeck's fdi file, and rebooted for good measure, but that hasn't changed anything.

```
nphillips@armitage:/etc/hal/fdi/policy$ hal-device |grep aiptek
  info.linux.driver = 'aiptek'  (string)
nphillips@armitage:/etc/hal/fdi/policy$ hal-device |grep "input.x11"
  input.x11_driver = 'evdev'  (string)
  input.x11_driver = 'evdev'  (string)
  input.x11_driver = 'evdev'  (string)
  input.x11_driver = 'evdev'  (string)

nphillips@armitage:/etc/hal/fdi/policy$ sudo tail /var/log/Xorg.0.log
(II) Aiptek: Configuring as mouse
(II) Aiptek: Configuring as keyboard
(**) Option "xkb_rules" "evdev"
(**) Aiptek: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Aiptek: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Aiptek: xkb_layout: "us"
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```

How can I get it to stop registering as a keyboard?

---

### Post by luopio on 2009-01-11
> **bmcage said:**
> Waldeck, can you edit the ubuntu help? A forum post with manual is really not that great. As people indicate, only the original poster can edit the main post.

sorry for the delay. i've posted a big red link to that page. i guess there's no reason in updating the original post since we have a wiki page available.

---

### Post by celticbhoy on 2009-01-12
thanx for wiki post

---

### Post by jackmcslay on 2009-03-04
I had a hard time trying to properly install my tablet on previous versions of Ubuntu (in fact, the fact 8.10 presented a new way to configure tablets was THE reason for me to update)

But I'm not at 100% already. The pen doesn't act like a mouse anymore but pressure sensitivity is dead. Any ideas? Here's my 10-aiptek.fdi:
```

<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
      <merge key="input.x11_options.zMax" type="string">511</merge>
    </match>
  </device>
</deviceinfo>

```

also, is there any way to configure the drawing area? My screen's ratio (8:5) doesn't match my tablet's (4:3)

edit: doh, Pressure sensitivity wasn't set up in gimp' It works now :D
also fixed the screen ratio problem, so all of wide-screeners or cocktailers might want to add this line too
```

      <merge key="input.x11_options.KeepShape" type="string">On</merge>

```

---

### Post by bmcage on 2009-03-09
Thanks for updating the wiki jack! ( [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) )

---

### Post by DuKe2112 on 2009-04-04
Hey thanks for the update too, that looks realy easy.
Unfortunately it doesn't work right for my 6000U.

I think I have unusual behavior here:
Without the Hal policy it already worked as a mouse, but without the buttons.
With the Hal policy it works as a pointer, but the tip doesn't trigger a click although gimp recognizes pressure sensitivity as an available axis.
Per default it uses it as the y-axis and recognises a total of 5 axes though.

Also when you boot with the tablet plugged in, it doesn't crash, but it doesn't work either and crashes when you pull it out.

I'd like to use the other buttons on the pen and the function keys on the tablet as well, how do I configure them?

---

### Post by Tropcon on 2009-04-24
Hi everyone! I have what I hope to be a rather simple question.

I just installed the "drivers," and they work beautifully on my Medion MD 41217 (an off-brand Aiptek tablet.)
I was just wondering if there was a way to increase the threshold... sensitivity... ? I don't really know what to call it. It's how close the stylus has to be before the tablet starts tracking it. As it is now, my stylus has to be practically *on* the tablet before it is detected (makes it kinda' hard to draw when you don't know where your going to start drawing when you put the pen down.) I know that the tablet is capable of detecting the stylus from at least a half inch away.
Any suggestions?

Thanks.

---

### Post by Sewje on 2009-04-26
Just wanted to clear some thing regarding the Aiptek/Genius/Trust brand graphics tablets.

I myself have 2 A4 tablets from the re-brand, one is Trust brand and the other is Nisis. I currently use the Trust TB-7300 which is basically the Aiptek 14000U or the Genius M712.

I just want to clear up that the ORIGINAL tablet maker is Waltop, and to be honest the Aiptek driver should in fact be called Waltop driver.

Now I do a lot of researching before I start posting problems and this is an issue I failed to find a solution for, a small thing but big enough to really make the tablet crap to use on Linux.

I am talking about Ubuntu 9.04, The tablet works fine with pressure sensitivity, but the problem is the middle stylus buttons don't work properly. When testing the middle button presses with xinput it triggers the pressure and button[1] values altogether with it, button[2].

How can I map the buttons so this does not happen?

---

### Post by Favux on 2009-04-26
Hi Sewje,

If you do not have a calibration tool like "wacomcpl" for Wacom tablets you could do it through the .fdi file.  The 10-wacom.fdi contains a Waltop entry.  I'm assuming that's the .fdi file your tablet is using.  It is located at /usr/share/hal/fdi/policy/20thirdparty/.  The Waltop section looks like:
```
      <match key="info.product" contains="WALTOP">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
```
You could add a line like:
```
       <merge key="input.x11_options.Button2" type="string">3</merge>
```
Which would map the first stylus button to a right mouse click.  So the concept is similar to modifying a xorg.conf.

I'm just keying off your explanation that these are actually Waltop tablets.

Hope this is helpful.

---

### Post by bmcage on 2009-04-27
Tropcon,

you should play with the options 
PressCurve, example value: 0,5,95,100
zMin, example value: 0
zMax, example value: 512
zThreshold, example value: 0

You set them in the fdi file eg: 
<merge key="input.x11_options.zMin" type="string">0</merge>
See [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) and the man file [http://aiptektablet.svn.sourceforge.net/viewvc/aiptektablet/trunk/xserver_input_driver/aiptek.man?view=markup](http://aiptektablet.svn.sourceforge.net/viewvc/aiptektablet/trunk/xserver_input_driver/aiptek.man?view=markup) 

It might be that raising your zMin means you have to press harder, but you first see the pointer appearing on the screen before drawing. Please, make sure your batteries are not old before you do anything.

If you identify which setting helps for your problem, please add it to that wiki page.

---

### Post by Tropcon on 2009-04-27
Thanks bmcage. I was hoping to get back here before someone took the time to reply to my post, but I guess I was too late. Wow! I feel somewhat like an idiot! lol

The battery in my stylus *was* dead! It's been weeks of searching forums trying to get this *AWESOME* OS working smoothly with all of my hardware (webcam, sound-card etc.) I guess by the time I got back to working on the graphics tablet again the stylus was almost dead! I changed the battery and it works *beautifully* now.

Thank-you *SO* much to everyone who worked (or is working) on getting these tablets working!

Sorry for taking your time on something that I should have figured out myself. :)

---

### Post by Sewje on 2009-05-01
Favux,

Thanks for the help in mapping the buttons, that was something I was looking for also but thats not what my original problem is. At default the button is mapped to the middle mouse which is perfectly fine since that will allow me to auto-scroll.

Let me try to explain it better with an example.
When I press my stylus button it also triggers the pressure to max, so basically if I hold down my stylus button while moving on the screen it will select/draw even tho I am not pressing down the nib.
There is also 2 buttons on the stylus, both do the same thing, while I don't mind if only one is available it is a bit of a pain if it is unusable.

Regarding the wacomcpl, I did install it but it just comes up blank with nothing listed when I run it.

This is what happens in xinput query-state:

_Just hovering stylus_
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
ValuatorClass Mode=Absolute Proximity=In
	valuator[0]=2409  (x-axis)
	valuator[1]=5432  (y-axis)
	valuator[2]=0     (pressure)
	valuator[3]=0
	valuator[4]=0
	valuator[5]=0

_Pressing down on stylus_
ButtonClass
	button[1]=down   (stylus nib)
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
ValuatorClass Mode=Absolute Proximity=In
	valuator[0]=5545  (x-axis)
	valuator[1]=6115  (y-axis)
	valuator[2]=452   (pressure)
	valuator[3]=0
	valuator[4]=0
	valuator[5]=0

_Stylus button only hovering_
ButtonClass
	button[1]=down   (stylus nib)
	button[2]=down   (stylus button)
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
ValuatorClass Mode=Absolute Proximity=In
	valuator[0]=5557   (x-axis)
	valuator[1]=6228   (y-axis)
	valuator[2]=1023   (pressure)
	valuator[3]=0
	valuator[4]=0
	valuator[5]=0

See how only pressing the stylus button also triggers the pressure and button one. Obviously the pressure will be linked with button one, but the problem is that the stylus button is also link the button 1 and the pressure.
[U]
What Stylus button only hovering should be[/U]
ButtonClass
	button[1]=up
	button[2]=down   (stylus button)
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
ValuatorClass Mode=Absolute Proximity=In
	valuator[0]=5557   (x-axis)
	valuator[1]=6228   (y-axis)
	valuator[2]=0
	valuator[3]=0
	valuator[4]=0
	valuator[5]=0

So how would I fix it so it works how it should be.

---

### Post by Favux on 2009-05-01
Hi Sewje,

OK, now I see what you want.  You could try continuing to modify the .fdi as I showed.  The .xinitrc that wacomcpl generates is a hidden file in your /home/username.  What you seem to need would be the .fdi equivalents of:
```
xsetwacom set stylus Button1 "Button 1"
xsetwacom set stylus Button2 "Button 2"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 10 90 100"

```
Where the stylus tip is mapped to a left mouse click (default) and your first stylus button (Button2) to a middled mouse click (scroll) and the second button to a right mouse click.

You seem to be saying that you are able to use wacomcpl (except not in Jaunty) and that should actually do everything you need.  Just calibrate your tablet with it.  It allows you to configure your buttons also.  See Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

The reason wacomcpl is showing up empty is a bug in Wacom for Jaunty.  Timo Aaltonen specially patched the linuxwacom 0.8.2-2 in Jaunty to work with Xserver 1.6 and HAL.  Unfortunately the callout in the .fdi file is returning HAL/D-BUS names that linuxwacom doesn't understand.  So xsetwacom commands and hence wacomcpl don't work.  We have found a few work arounds.  See Jaunty Users near the top of the link above.

Now I suppose you could also be looking at either a problem with how the .fdi is constructed for Waltop or with a problem as to how the linuxwacom drivers handle a Waltop tablet.  But I would look into the above first.

---

### Post by Sewje on 2009-05-01
Uhggg! Your wall of text in the link crits me for 99999...

Thats a lot of information for what I wanted to fix.

Anyway I managed to find out why it connects the other unwanted buttons along with the stylus button, apparently the TPCButton string needs to be set to ON by adding:

```
<merge key="input.x11_options.TPCButton" type="string">on</merge>

```
The query-status with the stylus button now looks like:
ButtonClass
	button[1]=up
	button[2]=down
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
ValuatorClass Mode=Absolute Proximity=In
	valuator[0]=5955
	valuator[1]=15337
	valuator[2]=1023
	valuator[3]=0
	valuator[4]=0
	valuator[5]=0

The stylus works perfectly fine now, both stylus buttons trigger button[2] but I can live with that.

Thanks for the help! I'm sure this fix will be needed for all Aiptek 14000U/Genius M712/Trust TB-7300 users in Jaunty

---

### Post by Favux on 2009-05-02
Hi Sewje,

LOL.  What's even funnier is I originally had TPCButton "on" in my example above.  But I thought no, that can't be it because it is the default for tablet pc's.  TPC=tablet pc.

Since you want to go the .fdi route; to fix your stylus buttons try adding:
```
       <merge key="input.x11_options.Button2" type="string">2</merge>
       <merge key="input.x11_options.Button3" type="string">3</merge>
```

---

### Post by Sewje on 2009-05-02
Hi Favux,

The setting doesn't make sense to me either, Ubuntu always seems to do that, things just don't make sense with Ubuntu sometimes lol.
The method using fdi settings to configure button 3 won't work, I think its because the button isn't even set at lower level.

Anyway solve one problem and another one pops up, for some reason now the fdi setting reset to default on reboot and the only way to get it back is to hot-plug the usb everytime.

It happened when I changed the refresh detection in Compiz setting to fix the stuttering. How on earth could that have affected my tablet fdi settings?, whyyyy!!!!

During a brief moment in the boot process just before the tablet resets, if I'm fast enuff and try the tablet it does work properly for a brief moment, so basically somewhere during login time the tablet initially loads the proper fdi setting then resets to the wrong settings!
Why does it do that? lol

---

### Post by Favux on 2009-05-02
Hi Sewje,

As usual too many variables.  We know it can't be xorg.conf.

Are you modifying the original 10-wacom.fdi?  Or did you create a custom .fdi?  If so or if you saved and moved a copy of the original .fdi did you rename it?  Change .fdi to say .bak?  I'm saying make sure only one .fdi is available.

You did say you tried to use wacomcpl.  Make sure it didn't create a .xinitrc.  This is a hidden file in your /home/username directory.  It would apply after the .fdi.

I know that until recently when ATI video users tried to rotate their tablet pc's screen with Compiz on all kinds of weird things could happen.  Their keyboards would stop working, etc.  Apparently if something inadvertently modifies what Xinput sees things can get strange.

It's possible the linuxwacom driver is stuttering and then some other module is taking control of your tablet.  Your tablet is a usb tablet correct?  I've seen usb tablets work fine with the wacom.ko that comes with Jaunty.  But for example, our tablet pc's require us to compile linuxwacom 0.8.3-2 only to get it's wacom.ko and substitute it for the one in Jaunty.  The wacom.ko is the usb kernel driver.  Otherwise we get an error 113 or other problems.

---

### Post by Sewje on 2009-05-02
I've re-install Jaunty clean two times, just to make sure.

Seems the settings just resets on reboot, nothing to do with anything else. It doesn't reset the file or anything tho just the tablet which I find strange which means there must be another file for configuration?, I tried deleting fdi cache also, lol didn't work.
I copy the 10-wacom.fdi to desktop for editing then sudo copy it back into the original /usr/share/hal/fdi/policy/20thirdparty directory with terminal.
I only have one 10-wacom.fdi file.
There is a 11-x11-synaptics.fdi and 20-libgpod-sysinfo-extended.fdi file in the same directory, but that shouldn't affect anything right?

i never used wacomcpl since it doesn't show anything. So i don't have the .xinitrc file.

Yes it's a USB tablet.

Done some read ups on linux hotplug and coldplug and there are mentions of some ubuntu scripts that break the coldplug process prehaps its something to look into.

Don't want to mess with this problem too much since I have my compiz working perfectly, and damn its nice! :D

---

### Post by Favux on 2009-05-02
Hi Sewje,

Okay we won't mess with Compiz.

The other .fdi files shouldn't matter.  What HAL is doing is defining a nested hierarchy of devices I guess.  So the .fdi files are crawling out far enough on the branches that they are dealing with only a single branch (device).  If you look at the first line or two of each section you see they are specifying a uid or info.product=serial or whatever.  But what I wanted to avoid is two .fdi files dealing with the same device.

Did you look for .xinitrc?  A hidden file so you have to check show hidden files in View.

You are right that linuxwacom has had troubles with hot plug.  I think there have been patches for it on versions newer than the 0.8.2-2 in Jaunty.  That's the last production version.  The development branch is up to 0.8.3-3.  But it doesn't have the special Jaunty patches.

So one thing you could try is what gali98 does in his HOW TO on page 11 post #104.  He replaces the 0.8.2-2 wacom.ko (the usb kernel driver) with the 0.8.3-2 wacom.ko.  That fixed the usb problem with his tablet pc.  The cp command shows you the directory of the current 0.8.2-2 wacom.ko.  You could move it and save it somewhere else.  Then replace it the 0.8.3-2 wacom.ko that you compile.  You don't install 0.8.3-2, you keep using the patched 0.8.2-2 but you do replace the kernel driver.  Maybe that would fix your problem?  If not just move the 0.8.2-2 wacom.ko back.

---

### Post by Sewje on 2009-05-02
OMFG! Yeah... I read it properly now >.> lol its because there is too much dummy devices so the real one is not getting detected...
Man someone needs to fix that properly OFFICIALLY! damn!

So basically for my Tablet I just remove the entrys for the "Cursor", "Eraser" and "Pad" and voila! Bobs not my uncle!

Problem sorted, I've tested it on reboot and damn it feel soooo right LOL :D

Many Thanks for the help, looks like Linux is going to be my main OS :D

All thats needed for my tablet was:
```
      <match key="info.product" contains="WALTOP">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<merge key="input.x11_options.TPCButton" type="string">on</merge>
      </match>
```

---

### Post by Favux on 2009-05-02
Outstanding!

---

### Post by sheffield on 2009-06-21
Hi All 
sorry to be a pain i have managed to get the tablet drivers and the tablet working in inkscape with no problem.

My problem is gimp, all I can do in it is draw a limited horizontal straight line, can anyone help

MTIA

Alex

---

### Post by hva on 2010-05-02
I'm back again with the same old problem: I upgraded from hardy to lucid, and I have lost my tablet again (Aiptek HyperPen 12000U).
It used to work perfectly on hardy, and now I get no buttons working, and it seems to act as a mouse.
besides it works with proximity only until first pen-tip touch, then it moves the cursor only if the pen-tip is on the tablet.
see this:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-aiptek/+bug/361693](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-aiptek/+bug/361693)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-aiptek/+bug/573519](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-aiptek/+bug/573519)

I've set the hal fdi policy file as it is in the wiki guide, but no luck at all.
It seems Lucid has dropped Hal for a udev only based system, could that be relevant? any tip?
I'm really sick of having to get mad with my tablet each time a new ubuntu release is out. This prevented me to upgrade from hardy before, but such regressions between two LTS releases are really really bad, after 2 years I was rather confident my tablet would have been working out of the box, but it seems the aiptek driver is more or less unmaintained.

---

### Post by hva on 2010-05-02
I have had a look at how wacom tablets are supported in Lucid:
seems fdi files have to be translated to udev rules, see this:
[https://wiki.kubuntu.org/X/InputConfiguration](https://wiki.kubuntu.org/X/InputConfiguration)
and then we are back to a sort of xorg.conf configuration system, through local snippets added in /usr/lib/X11/xorg.conf.d

I will try to see if I can work things out.
I was thinking about adding udev rules like this:

```
ACTION!="add|change", GOTO="xorg_aiptek_end"
KERNEL!="event[0-9]*", GOTO="xorg_aiptek_end"

ATTRS{idVendor}=="08ca", ENV{x11_driver}="aiptek", SYMLINK+="input/aiptektablet"

LABEL="xorg_aiptek_end
```"

and a '10-aiptek.conf' xorg.conf.d snippets more or less like this:

```
Section "InputClass"
	Identifier "pen"
	MatchProduct "Aiptek|AIPTEK|aiptek"
	MatchDevicePath "/dev/input/event*"
	Driver "aiptek"
	Option "SendCoreEvents" "true"
	Option "USB" "on"
	Option "Type" "stylus"
	Option "Mode" "absolute"
	Option "zMin" "0"
	Option "zMax" "511"
EndSection
```

Has anyone already tried this kind of approach?

---

### Post by Favux on 2010-05-02
Hi hva,

That looks reasonable.  We've been doing similar things with Wacom and N-trig tablets.  We've found, for instance with N-trig, that using xorg.conf seems to work better than xorg.conf.d.  But maybe that's because we haven't figured it out completely.  For example coordinates don't seem to work in xorg.conf.d.

The key is whether the Aiptek X driver has been updated to Xserver 1.7 and whether the kernel supports Aiptek good enough to send the appropriate raw data to the Aiptek X driver (it's a usb tablet, correct).

---

### Post by hva on 2010-05-02
Hi Favux, thanks for your kind answer

> **Favux said:**
> Hi hva,

That looks reasonable.  We've been doing similar things with Wacom and N-trig tablets.  We've found, for instance with N-trig, that using xorg.conf seems to work better than xorg.conf.d.  But maybe that's because we haven't figured it out completely.  For example coordinates don't seem to work in xorg.conf.d.

The key is whether the Aiptek X driver has been updated to Xserver 1.7 and whether the kernel supports Aiptek good enough to send the appropriate raw data to the Aiptek X driver (it's a usb tablet, correct).

yes, it's USB tablet.
last changelog of the driver package says

```
xserver-xorg-input-aiptek (1:1.3.0-1) experimental; urgency=low

  [ Timo Aaltonen ]
  * New upstream release.
  * Bump Standards-Version to 3.8.3.
  * Build against Xserver 1.7.

  [ Cyril Brulebois ]
  * Upload to experimental.

 -- Cyril Brulebois <kibi@debian.org>  Sat, 05 Dec 2009 23:33:34 +0100

```

so I suppose it should work with xserver 1.7.
The kernel driver has always worked, and I hope it still does, but certainly is a bit annoying to have to completely chenge the configuration policy with each new release, above all when the xserver-xorg-input-aiptek package doesn't provide any kind of config file, and not even a template.
I will try to see if i can work it out and I'll let you know.

---

### Post by Favux on 2010-05-02
Hi hva,

> a bit annoying to have to completely chenge the configuration policy with each new release, above all when the xserver-xorg-input-aiptek package doesn't provide any kind of config file, and not even a template.
Totally agree.  The packager should supply the .conf file.  But give where other folks are in practice you are lucky Cyril Brulebois/Timo Aaltonen built it to work with 1.7.  Basically your template will be the old xorg.conf's and the options used in the .fdi.

Good luck!

---

### Post by hva on 2010-05-03
IT WORKS!

I have made a udev rules file and the xorg.conf.d thing and now i have my tablet back.

A problem I haven't solved yet is with buttons mapping:
at start I have only the stylus tip working and acting as button 1, the
xinput get-button-map Aiptek
gives "1 2 3 4 5"
If I remap with
xinput set-button-map Aiptek 1 3 2 4 5
I have lower stylus button acting as right-click and pen tip working as left-click, that is good enough for me, but I was not able to have the upper stylus button to work as middle-click as it was supposed to do.
I tried to set ButtonMapping option in xorg.conf.d snippet, but it doesn't work, so I guess I should find a way of remapping buttons at session startup, but I have my tablet back, with pressure working in Gimp!

---

### Post by hva on 2010-05-03
another quick note: according to the discussion in this bug report
[https://bugs.freedesktop.org/show_bug.cgi?id=26584](https://bugs.freedesktop.org/show_bug.cgi?id=26584)
aiptek driver has not been ported completely for use with 1.7 server yet, this may explain the quirks with button management.
It certainly explains why the Fn buttons on top of the tablet don't have any effect, though they generate events.

> As I've added in the commit message for the second patch, this only fixes the
issue for X servers 1.6 and earlier. X server 1.7 has a different
initialization method that - afaict - is currently not employed at all by the
aiptek driver. So under 1.7, the driver has no key symbols at all.

Just letting you know about this so you're not surprised when you update :)

The good new is that it seems there's someone committed to work on aiptek driver to make it work better with 1.7 xserver.

---

### Post by Favux on 2010-05-03
Hi hva,

It turns out that button mapping in Xinput is not as straitforward as it seems.  Linuxwacom only got it fixed in the last month or two because a Xorg expert, Peter Hutterer, is helping to port the X driver part of linuxwacom to xf86-input-wacom for running on Xserver 1.7.  So it wouldn't surprise me if the code is wrong, because of a misunderstanding of button mapping in the newer Xservers.

The function buttons on the tablet need code in the drivers which hasn't been done AFAIK.

---

### Post by rvlander on 2010-05-10
Hello,

I am trying to use a 8000u with lucid and it is a failure :
[URL="http://ubuntuforums.org/showthread.php?t=1478769"]
http://ubuntuforums.org/showthread.php?t=1478769[/URL] 

Can anybody help me ?

Thanks,
rvlander

---

### Post by arttie_br on 2010-05-19
Hi,

I have an 8000u too.
Following this kind and detailed tutorial I have mine working almost perfectly.
The only missing thing is the pressure control.

Does anyone have any advice on this?

Thanks in advance for the attention.
Regards,

Arthur

---

