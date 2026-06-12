---
title: "How to install .tar.gz files"
date: 2007-06-26
forum: Programming Talk
---

### Post by Dark Aspect on 2007-06-26
I am not sure what category to post this under but I am trying to install a .tar.gz file on my Ubuntu computer to add joystick support in my kernel.[This is the file I am trying to install](http://atrey.karlin.mff.cuni.cz/~vojtech/joystick/).the read me file says I must modify the make file for my system and I must also modify my kernel but it gives me a incorrect file path to my kernel.It says my kernel is located in /usr/src/linux but I don't have a directory like that I have four folders in my src directory labeled:

linux-headers-2.6.20-15
linux-headers-2.6.20-15-generic
linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic

I am massive confused on what to do next and when I try to type "make" in the joy stick's driver directory I get a error.this is what the readme file says to do:

> 
To compile the utilities in the joystick package, and the driver itself,
as a standalone module, you first unpack the package, and then edit the
Makefile to meet your needs (namely whether are you using versioned
modules). You will also need an unpacked and configured

	make config

kernel in
	
	/usr/src/linux

Furthermore, if you're using versioned modules, you'll also need

	make dep

done on the kernel, to create some needed files.

After that, you compile the joystick driver

	make

  And after that you install it

	make install

  In case you have not used the driver before, you'll need to create the
joystick device files in /dev so that applications can use them:

	make devs

  For manual creation of the joystick devices, check the
Documentation/devices.txt file in the Linux source tree.

  Should you not want to mess with the kernel, and just use the driver
standalone, as modules, skip the next two sections, proceeding right to 2.4,
because all you need is already done.


Does Ubuntu have versioned modules?any help would be appreciated,I apologize if this is posted in the wrong category.

---

### Post by moma on 2007-06-26
Do you really must compile the joystick driver yourself? 

It seems to me that the code in question is quite old (kernel 2.4 and year 1999).

Ubuntu already comes with drivers for many Joystick controls.  

List the driver names: 
$ [COLOR="SeaGreen"]locate joystick | grep modules[/COLOR]
or 
$ [COLOR="SeaGreen"]ls -l /lib/modules/$(uname -r)/kernel/drivers/input/joystick[/COLOR]

Read these articles:
[http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html](http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html)

[http://swik.net/joystick-ubuntu](http://swik.net/joystick-ubuntu)

"joydev" seems to be the main module name.
--------------

If you want to study and re-compile the drivers, then first, D/L the complete linux-source [not only the headers (*.h files) as shown in your listing].

It's quite a big tar.bz2 ball
$ sudo apt-get install linux-source

Unpack it 
$ cd /usr/src 
$ sudo tar -xvjf linux-source-2.6.20.tar.bz2

$ cd /usr/src/linux-source-2.6.20/drivers/input/
$ ls -l 
$ ls -l joystick
----------

[COLOR="Red"]Importante:[/COLOR] read the documentation in the Linux-source's /Documentation directory
$  [COLOR="Green"]ls -l /usr/src/linux-source-2.6.20/Documentation/input[/COLOR]

---

### Post by Dark Aspect on 2007-06-26
> **moma said:**
> Do you really must compile the joystick driver yourself? 

It seems to me that the code in question is quite old (kernel 2.4 and year 1999).

Ubuntu already comes with drivers for many Joystick controls.  

List the driver names: 
$ [COLOR="SeaGreen"]locate joystick | grep modules[/COLOR]
or 
$ [COLOR="SeaGreen"]ls -l /lib/modules/$(uname -r)/kernel/drivers/input/joystick[/COLOR]

Read these articles:
[http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html](http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html)

[http://swik.net/joystick-ubuntu](http://swik.net/joystick-ubuntu)

"joydev" seems to be the main module name.
--------------

If you want to study and re-compile the drivers, then first, D/L the complete linux-source [not only the headers (*.h files) as shown in your listing].

It's quite a big tar.bz2 ball
$ sudo apt-get install linux-source

Unpack it 
$ cd /usr/src 
$ sudo tar -xvjf linux-source-2.6.20.tar.bz2

$ cd /usr/src/linux-source-2.6.20/drivers/input/
$ ls -l 
$ ls -l joystick
----------

[COLOR="Red"]Importante:[/COLOR] read the documentation in the Linux-source's /Documentation directory
$  [COLOR="Green"]ls -l /usr/src/linux-source-2.6.20/Documentation/input[/COLOR]

Well you have a good point its just my controller was a programmable one in windows were I could bind keyboard keys to gamepad buttons.I can only find for Ubuntu [this]("http://packages.ubuntu.com/edgy/x11/joy2key") and when I load the app nothing happens.If I load it though the terminal it gives a error and says I must have joystick driver in my kernel.Thus I got it in my head I must re compile my kernel thanks for the links I'll check then out thanks for the help.

---

