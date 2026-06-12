---
title: "Logtiech Mediaplay Cordless Mouse and Fiesty Ultimate Guide"
date: 2007-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by nogg3r5 on 2007-08-04
**UPDATED 05/09/07**
These are notes for reference, I use them, they work for me. They might not for you!!
I got all* the buttons on my Logitech Mediaplay Cordless Mouse working. I also found a better way to generate the startup script. its mostly untested, mileage may vary!!!! Heres how...

*There is one exception, I haven't got the side buttons working in Nautilus, this doesn't really bother me though so I haven't tried.


You will need:
[These instructions]("http://ubuntuforums.org/showthread.php?p=560528#post560528")
[The Logitech MediaPlay Cordless Mouse USB Linux driver (lmpcm_usb)]("http://daemon.prozone.org/%7Edavid/projects/lmpcm_usb/")
Also familiarise yourself with [this guide to startup scripts]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")
Plus a few other things, but we can install those as we go.

They secret here is to follow the right instructions then finish with my custom startup script. Let us begin...


This first part is basically CompShrinks guide to installing the lmpcm_usb driver, re written slightly to make it more person friendly...

**[SIZE=4]Install Driver[/SIZE]**
You will need the build_essential package if you dont already have it:

```
sudo apt-get install build-essential
```Download the lmpcm_usb source tarball and uncompress it:

```
 tar zxf lmpcm_usb-0.5.2.tar.gz
```Now, change to the newly created directory, compile and install the driver: 

```
 cd lmpcm_usb-0.5.2
 sudo make
 sudo make install
```The installation script will have installed lmpcm_usb.ko (lmpcm_usb.o for kernel 2.4) into /lib/modules/your-kernel-version/misc/ and added an entry to modules.dep file, using depmod.

**[SIZE=4]Loading modules[/SIZE]**

Edit /lib/modules/your-kernel-version/misc/modules.dep and remove usbmouse and usbhid entries:

Change to the directory /lib/modules/
```

cd /lib/modules/ 

```You need to now use the directory specific to your kernel, you cna find this by entering:

```
ls
```The output should look something like:

```
nogg3r5-ubuntu:/lib/modules$ ls
2.6.20-15-generic  2.6.20-16-generic

```I used the highest numbered directory:

```

cd 2.6.20-16-generic/misc/

```Create a backup of modules.dep:

```

sudo cp modules.dep modules.dep.backup
```Now we need to remove the usbmouse and usbhid entries. Use gedit's find feature to find the lines you have to remove
```

gksudo /lib/modules/your-kernel-version/misc/modules.dep
```This is required because these modules "steal" any kind of mouse, so we have to load lmpcm_usb first. If usbmouse and/or hid are required for any other device, just load them after lmpcm_usb. But don't forget, lmpcm_usb SHOULD LOAD FIRST that any generic mouse driver.

I wasnt sure what these commands did, so I ran them all anyway...

Loading support:
(these 3 commands should be unneccessary unless you removed these modules for something else)
Kernel 2.6
```
 sudo modprobe usbcore
 sudo modprobe uhci-hcd
 sudo modprobe evdev
```
Ensure usbmouse and hid are not loaded:

Kernel 2.6
```
 sudo rmmod usbmouse
 sudo rmmod usbhid
 sudo modprobe lmpcm_usb
```At this time, your mouse should work.

Now, when you reboot your computer, the mouse will stop working. You need to run these three commands to get i working again...
```

 sudo rmmod usbhid
 sudo rmmod lmpcm_usb
 sudo modprobe lmpcm_usb
```This is where the magic happens...

```
gedit mouse.sh
```

Copy and paste this code into the new file:

```
#!/bin/bash
sudo rmmod usbhid
sudo rmmod lmpcm_usb
sudo modprobe lmpcm_usb
```I found the first line, after *#!/bin/bash* unneccesary and removed it.

Close and save the file then make it executable:

```
sudo chmod +x mouse.sh
```

**Updated **
Then install the startup script:
Go to System -> Preferences -> Sessions.

Add the script you just created....

Click new... Give it a name, I used Mouse. Then add the path to the script. something like /home/yourusername/mouse.sh

Now you need to edit your sudoers file to allow you to run the file without needing a password...

[code]sudo visudo[code]

Paste the following...

# User can run the script without the need for sudo password
yourusername ALL=NOPASSWD:/home/yourusername/mouse.sh

Now, when you reboot, your mouse should work, with all the media buttons, back, forward, skip and scroll wheel buttons!!!


If anyone has any feedback, please feel free to leave it, this is my first user guide and I probably made a few mistakes!!!

---

### Post by LeChacal on 2008-01-02
I was looking to get my Logitech MediaPlay Cordless Mouse working and found this. I see that it is a little old and was wondering if there is any updates and if it works smoothly with Gusty before I try it because it involves changing some system stuff.  *bytes nails*

---

