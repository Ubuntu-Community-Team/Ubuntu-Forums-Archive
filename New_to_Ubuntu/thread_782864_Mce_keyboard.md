---
title: "Mce keyboard"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by kubuch on 2008-05-05
Hello guys ;)
I just start with Ubuntu. all work great but i have some problems with config of "Microsoft Remote Keyboard for WinXP MCE v1.0" 
I install lirc and lirc_mod_mce drives.. 
i try with "irw" and i see commands i set up is to VLC and work great but..
but only media keys.
I wonder how to make Mce keyboard to work in system,openoffice generaly in ubuntu. Now I type with my old usb key but i wanna get MCE keys to work.
its my   dmesg | grep -i lirc
```
[   35.846905] lirc_dev: IR Remote Control driver registered, major 61 
[   35.856824] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   35.860593] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[   35.860598] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   36.236794] lirc_dev: lirc_register_plugin: sample_rate: 0
[   36.240775] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb4:2
[   36.240806] usbcore: registered new interface driver lirc_mceusb2
[   36.284305] lirc_mod_mce: Input driver for Microsoft MCE 2005 keyboard v0.2.0
[   36.284309] lirc_mod_mce: Florian Demski
[   36.308099] usbcore: registered new interface driver lirc_mod_mce

``` 

pls help 
peace

---

### Post by kubuch on 2008-06-09
some1?

---

### Post by north_pole on 2009-04-29
This is exactly how it looks for me too! Keyboard and mouse pointer still doesn't work...

---

### Post by north_pole on 2009-04-29
YEEES! Finally I've made it all work. Here's an HOW-TO for Ubuntu Jaunty Jackalope 9.04:
 
1. Install some required modules with
 
```
$ sudo apt-get install lirc lirc-modules-source module-assistant 
```2. and then run the following command
 
```
$ sudo dpkg-reconfigure lirc-modules-source 
```3. Open the the hardware.conf file with this command
 
```
$ sudo vi /etc/lirc/hardware.conf 
```4. Change two of the lines so they look like this:
 
```
REMOTE_MODULES="lirc_mod_mce"
 
LOAD_MODULES="true" 
```Save and exit.
 
5. Run the following commands
 
```
$ sudo m-a update,prepare
 
$ sudo m-a clean lirc
 
$ sudo m-a a-i -f lirc    (if this one fails, choose "skip and continue with the next operation")
 
$ sudo depmod -a
```
 
6. Download one of the archives I've attached and extract/decompress the containing files "lircd.conf" and "lircrc". Put them in /etc/lirc. (some dists don't have any archive manager, resolved by executing "sudo apt-get install unzip")
 
7. Now download the lirc_mod_mce v.0.1.5 file from [http://sourceforge.net/project/showf...kage_id=203215]("http://sourceforge.net/project/showfiles.php?group_id=171688&package_id=203215"), but be sure to download version 0.1.5 and NOT the v0.2.0 or v0.2.1. The later ones has the famous "keypress repeats forever"-bug and should be avoided. Extract/decompress the archive in a new directory on e.g. your desktop.
 
8. Delete the downloaded "lirc_dev.h" file and replace it with the one located in "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev"
 
9. In the file named "lirc_mod_mce.c", you have to change one of the lines:
 
```
input_dev->cdev.dev = &dev->dev;
 
to
 
input_dev->dev.parent = &dev->dev; 
```Save and exit.
 
10. Now execute, in your desktop directory containing the lirc_mod_mce files:
 
```
$ sudo make 
```
 
11. Create a new directory in "/lib/modules/%YOUR_CURRENT_KERNEL%" and name it "misc".
 
12. Some extra files have been created in the desktop "lirc_mod_mce" directory.
One of them is "lirc_mod_mce.ko". Copy it to the new directory you just created in step 11.
 
13. Run
 
```
sudo depmod -a
 
modprobe lirc_mod_mce 
```14. At last we have to blacklist the "lirc_mceusb2" module. Otherwise it will
interfere with the "lirc_mod_mce" one and make all of our work useless. Execute:
 
```
$ sudo vi /etc/modprobe.d/blacklist.conf 
```and add the line
 
```
blacklist lirc_mceusb2
```
on an own row e.g. in the bottom of the file. Save and close.
 
15. Reboot
 
16. And VOILA! Your MCE Keyboard should be working!

---

### Post by MikeV8 on 2009-08-21
Hey North_pole...  Very excellent instructions, up to point 6, then we linux numpties are left in the lurch with steps 6, 7, & 8 (and it would also help to repeat the 'Gedit' instruction for 9).
At step 6,  the stated files are not attached, unless they are within the .tar file mentioned at the very last step, but what the hell do you do with a .tar file ?
Oh, and at step-3, Gedit aint part of a base mythbuntu install, so a mention that you might need to download/install Gedit would be helpful at that point.

It all fell apart at Step 6 for me ! and I cain't get no further.

If you are still around (or someone else lurking), could you please explain steps 6 thru 9 a little ?

Regards, Mike

---

### Post by north_pole on 2009-08-21
Changed the recommended editor to "vi" instead of "gedit", and attached another archive with the .zip format. I'm forced to keep the files packed because otherwise the forum refuses to upload them.

---

### Post by MikeV8 on 2009-08-22
Thanks again, North-P
Still stumbled as there was no unzip or other applet associated with .zip
Hit the forum search again,  found that Mythbuntu doesn't include unzip, so had to install that first.  For other newbies,  the command is  ***sudo apt-get install unzip***
Now carrying on with the rest of the steps.

---

### Post by MikeV8 on 2009-08-22
Got through everything except the 'modprobe' under step-13.  This gives the following :-  

/lib/modules/2.6.28-15-generic/misc$ modprobe lirc_mod_mce
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module lirc_mod_mce not found.

Does this need to be executed from within a particular folder ?

---

### Post by north_pole on 2009-08-22
> Does this need to be executed from within a particular folder ?
No, but the "sudo make" command at step 10 has to, in the directory where you unpacked your downloaded lirc_mod_mce files (step 7).

Is the lirc_mod_mce.ko file really copied to "/lib/modules/2.6.28-15-generic/misc"?

Is 2.6.28-15 really your actual kernel?

Sure you've run "sudo depmod -a"?

---

### Post by MikeV8 on 2009-08-23
*Is the lirc_mod_mce.ko file really copied to "/lib/modules/2.6.28-15-generic/misc"?*

That was the problem. Must have been a permissions thing and it didnt copy (was using Thunar file manager, worked better from command line with Sudo).

Ran thru steps again from 11,  and Voila - Working beautifully.

Thanks so much for your help, North-Pole !

---

### Post by ryanolf on 2009-09-13
Thanks for the How-To. 

Using lirc_mod_mce version 0.1.5 does not work for me. My IR receiver (which came with my new MCE remote) does not seem to be recognized by the module. However, using 0.2.1 my keyboard and remote both work (I do not change the cdev line, but I do copy over the newer lirc_dev.h file). Unfortunately, the infinite keypress issue means the keyboard is basically useless. Any ideas how to get the older version working?

My lsusb lists the IR receiver as Bus 004 Device 004: ID 1784:0008 TopSeed Technology Corp. It has a red light on the front that turns on when it sees a keypress (either keyboard or remote). This light stays lit once a key/button is pressed using the old version 0.1.5, and the press is not seen (either as keyboard or irw) by the system. With 0.2.1 the light is on only when keys/buttons are pressed, but not once they are unpressed.

Thanks for the help!

---

### Post by jon47 on 2010-07-23
I'm pretty sure that the package I built for lirc/lirc_mod_mce has code to recognise the TopSpeed hardware, but I don't have the hardware so can't test it.  Try this:

 [http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326](http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326)

and let me know how you get on.

Cheers
Jon

---

