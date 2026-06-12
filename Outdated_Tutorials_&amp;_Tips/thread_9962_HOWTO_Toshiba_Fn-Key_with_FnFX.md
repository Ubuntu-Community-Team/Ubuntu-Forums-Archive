---
title: "HOWTO: Toshiba Fn-Key with FnFX"
date: 2005-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by amandla on 2005-01-03
**Purpose: Getting Fn-keys on toshiba laptops to work using [FnFX](http://fnfx.sourceforge.net/) **

FnFX is not in the repositories, so you will have to compile/install it manually.

1-  Download the tar file [here](http://fnfx.sourceforge.net/index.php?section=files), select Download source.

2-  
[list]
[*]cd <to dir where you downloaded the file>
[*]gunzip fnfx-<version number>.tar.gz
[*]tar -xfv fnfx-<version number>.tar
[*]cd fnfx-<version number> 
[*]./configure
[*]make
[*]sudo make install
[/list]

3-  sudo mkdir /etc/fnfx/

4- sudo cp /usr/local/etc/fnfx/* /etc/fnfx/ 

5- cp /etc/fnfx/fnfxrc_example /home/<your user name>/.fnfxrc

now to run the daemon
sudo fnfxd

for configuration options and more info please refer to fnfx doc [here](http://fnfx.sourceforge.net/index.php?section=doc) 

now there might be a few bugs in this HOWTO since it is my first one **EVER**   8-)  . Please keep in might the since fnfx is not in the repositories, i have no clue what it will do to warty ... USE AT YOUR OWN RISK. If it makes you feel better, it seems to work fine on my system  :mrgreen:

---

### Post by niels on 2005-03-15
[QUOTE=amandla]

now to run the daemon
sudo fnfxd

[/QUOTE]

I have just tryed to install fnfx with the above description. Everyting went well until I would run the deamon. I got the following error messge:

root@niels:/home/niels/Pakker/fnfx-0.3 # fnfxd
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).


I am pretty sure, that I have enabled Toshiba support, but how do I test or see this? The folder /proc/acpi/toshiba/ does not eksist!?!
If it is not enabled, how do I do it?

/Niels

---

### Post by barbarian on 2005-03-15
Does it work only for Toshiba?
On my Fujitsu-Siemens I have Fn key also..

---

### Post by Grant on 2005-04-12
[QUOTE=amandla]**Purpose: Getting Fn-keys on toshiba laptops to work using [FnFX](http://fnfx.sourceforge.net/) **

FnFX is not in the repositories, so you will have to compile/install it manually.

1-  Download the tar file [here](http://fnfx.sourceforge.net/index.php?section=files), select Download source.

2-  
[list]
[*]cd <to dir where you downloaded the file>
[*]gunzip fnfx-<version number>.tar.gz
[*]tar -xfv fnfx-<version number>.tar
[*]cd fnfx-<version number> 
[*]./configure
[*]make
[*]sudo make install
[/list]

3-  sudo mkdir /etc/fnfx/

4- sudo cp /usr/local/etc/fnfx/* /etc/fnfx/ 

5- cp /etc/fnfx/fnfxrc_example /home/<your user name>/.fnfxrc

now to run the daemon
sudo fnfxd

for configuration options and more info please refer to fnfx doc [here](http://fnfx.sourceforge.net/index.php?section=doc) 

now there might be a few bugs in this HOWTO since it is my first one **EVER**   8-)  . Please keep in might the since fnfx is not in the repositories, i have no clue what it will do to warty ... USE AT YOUR OWN RISK. If it makes you feel better, it seems to work fine on my system  :mrgreen:[/QUOTE]
 Note:  this will NOT work on some Toshiba laptops, specifically the ones that use a Phoenix BIOS.  Toshiba doesn't actually make those laptops, they just rebadge them.  So I'm stuck with a Satelite A70 that has almost no power management support.

---

### Post by caspian on 2005-04-27
I've installed FnFX, but I can't figure out how to use it. I do Fn+F3, which is suppoed to suspend to RAM... but it does nothing. I checked in /etc/fnfx/fnfxd.conf and noticed that the Fn+F3 command was commented out, so I uncommented it. Still nothing.

Is there something special I need to do to configure it?

I'm using a Toshiba Tecra M2.

---

### Post by Verplrke on 2007-04-09
> **niels said:**
> I have just tryed to install fnfx with the above description. Everyting went well until I would run the deamon. I got the following error messge:

root@niels:/home/niels/Pakker/fnfx-0.3 # fnfxd
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).
/Niels

I have the exact same problem, but how do you test or fix this issue?

---

### Post by madi on 2008-03-01
Guys i have this problem and i dont know what does it mean

[user@localhost ~]$ fnfx
FnFX Client v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not get id of semaphore with key 0x822155648.



Could somebody help. :guitar:

---

### Post by Skerious on 2008-05-29
> **Verplrke said:**
> I have the exact same problem, but how do you test or fix this issue?


I have the same problem....waiting for help....  :confused:

---

### Post by Skerious on 2008-05-29
[http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver)


found that but don't know how to install it or whatever.

---

### Post by vgrisham on 2009-02-27
The post regarding the Toshiba Tecra M3 at [this]("http://pentropy.twisty-industries.com/post/by_tag/65") site got my keys working.

---

### Post by binbash on 2009-02-27
> **vgrisham said:**
> The post regarding the Toshiba Tecra M3 at [this]("http://pentropy.twisty-industries.com/post/by_tag/65") site got my keys working.

Love you, i was playing with my old toshiba for 5 hours and i got it working after seeing your post : )

---

### Post by vgrisham on 2009-02-27
Binbash (and anyone else),

Does your monitor out port work? I can't get the hotkey enable the outgoing video signal. I need to connect this laptop to a projector and so far, no joy.

---

### Post by bacchusmarsh on 2009-03-13
This may seem obvious but i am new. I have a Te2100 and had the same Fn keys problem.
After hours of searching on forums i remebered something i had seen another linux user do. I went to synaptic package manager under System, administration>
Then did a search for fnfx
Highlighted both fnfx and fnfxd and installed.

Now my Fn f5 seems to work!!!

but the brightness doesn't seem to and the fan is running off tap....

---

### Post by bacchusmarsh on 2009-03-13
ok the Fn f5 keys was working, though external monitor did "not support video mode".
anyway i downloaded a whole bunch of updates that ubuntu had found for me and my Fn f5 key is not working again!!! HELP...

---

### Post by bacchusmarsh on 2009-03-13
i found this somewhere:

External monitor only starts in the case it is already plugged in during startup. It runs then in "both" mode. However, when login screen is displayed, display is switched to external-only mode.

Halilujah!!! that is all i need, stuff the fn keys.

---

### Post by vgrisham on 2009-03-14
What video card is installed in your Toshiba? I finally got my vga out port working by using the NVIDIA X Server Settings from the Administration menu. This allowed me to set my external screen in TwinView, essentially a second workspace that I can mouse over to. It works pretty well and I too have given up on getting all of the function keys to work.

---

