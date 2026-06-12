---
title: "Ubuntu server - failed to copy files from cd-rom (live USB)"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by *^kyfds( on 2013-05-17
I'm trying to install Ubuntu server on a dell optiplex 170L.

Every single time i try to install it via a live USB, it throws the 'failed to copy files from CD-rom' error after about 10 seconds of copying a number of files, and i end up having to abort this installation.

I've tried all of the below fixes, with no success:

- Tried creating USB with unetbootin, universal live usb creator and Lili USB creator. 
- The tutorial shown on [this blog post]("http://cassaprodigy.wordpress.com/2012/09/28/how-to-make-ubuntu-server-installer-from-unetbootin/") (identical to the instructions on [this thread]("http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r")), by creating a folder 'default' and changing the format of a file to 'udeb'.
- Using the 13.04 server build instead of 12.04
- using a USB larger than 2Gb.

All of the above still result in the same 'failed to copy files' error message.


I'm getting to the end of my tether, as i've been working for a week to solve this, and I can't


any help getting this to install would be appreciated, 

~ thehumorouscheese.

---

### Post by ITfromScratch on 2013-08-09
This guy had the same problem: [http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r](http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r)

I'll quote his solution here:

> [COLOR=#333333][FONT=UbuntuRegular]It seems there are some naming errors with the files under [/FONT][/COLOR]\pool\main\l\linux[COLOR=#333333][FONT=UbuntuRegular] (I found false extensions [/FONT][/COLOR]*.ude[COLOR=#333333][FONT=UbuntuRegular] instead of [/FONT][/COLOR]*.udeb[COLOR=#333333][FONT=UbuntuRegular] there) and a MD5-Checksum error with[/FONT][/COLOR]./install/netboot/ubuntu-installer/i386/pxelinux.cfg/default[COLOR=#333333][FONT=UbuntuRegular]). After fixing these errors I'm able to install the 32-bit Server Edition.[/FONT][/COLOR]

So you might have some naming errors or checksum errors in your installation media.

---

### Post by l3dx on 2013-08-09
Have you been using unetbootin for all tries? If so it's worth a shot to use

> 
dd if=/path/to/ubuntu.iso of=/dev/sdX


(Replace sdX with your usb device)

---

