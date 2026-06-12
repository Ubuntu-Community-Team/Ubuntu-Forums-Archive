---
title: "Easycap video capture"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by squakie on 2013-11-24
It appears a driver has been developed for my Easycap video capture device that uses the UTV007 single chip.  This driver must be quite new as I didn't find it several months ago when looking.  [This]("http://www.linuxtv.org/wiki/index.php/Easycap") linux tv wiki page covers a lot of the Easycaps, and includes a section on the Easycap using the UTV007 single chip:

> 
[h=3]USBTV007 EasyCAP[/h] This EasyCAP is based on a single UTV007 labeled chip. 
This device is sold as "USB video capture QS702" from SHENZHEN FUSHICAI ELECTRONIC CO.,LTD 
**lsusb** reports 
 
[LIST]
[*] Manufacturer: Fushicai
[*] Product: usbtv007
[/LIST]
 [h=4]Components Used[/h] 
[LIST]
[*] Single chip: UTV007 A614231.1 1136L1BK
[*] Inscriptions on the board: FSC VIDEO DVR
[/LIST]
 [h=4]Indentification[/h] # lsusb
Bus XXX Device XXX: ID 1b71:3002 
[Full lsusb -v]("http://ubuntuforums.org/showthread.php?t=1949993") 
 [h=4]Making it work[/h] Linux kernel driver, enable CONFIG_VIDEO_USBTV: [https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/media/usb/usbtv](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/media/usb/usbtv) 

 
[LIST]
[*] From 3.11 ("Linux for Workgroups") on: Supports NTSC, Composite input
[*] Queued for 3.12: S-Video input
[*] In works: Controls (brightness, ...)
[/LIST]
 Also, a very experimental (for testing purposes only) userspace driver is available on github: [http://github.com/memeruiz/usbtv007]("https://github.com/memeruiz/usbtv007") 
 
[LIST]
[*] Currently doesn't do anything beyond what kernel driver does
[*] Written using Python libusb1 and v4l bindings
[*] Requires v4l loopback
[*] Could be useful for easy protocol testing, prototyping
[/LIST]
.....tail of post removed by me

It includes the link:
[https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/media/usb/usbtv](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/media/usb/usbtv)

But I have no real idea what to do with what's in that.  I know to compile the C source for the driver - what I don't know is what the things mean in the other 2 files.  In particular, I would have thought there would be a make file, perhaps a config file, and a list of dependencies.  

If someone could walk me through enough of that it would be GREATLY appreciated!  I no longer have a XP installation dual booting with Ubuntu - I just went all Ubuntu after what I thought was the conclusion of a project scanning in my old VHS tapes.  Turns out there is a problem with the output and I need to re-scan them, but trying to avoid reinstalling a small XP installation.  

I would also imagine that after that driver is built and loaded, I'm still going to need something to actually scan the moives in with Ubuntu.  I guess 1 bridge at a time.

Thank you.

[HR][/HR]

---

### Post by squakie on 2013-11-25
Don't know about all the Easycap's, but I did find out my Dazzle DC100 will work in Linux Mint 15 - going to try it there and get back the movies I need.

---

### Post by squakie on 2013-11-27
No replies for Ubuntu, so giving up trying to find something that will work in it.  Going to try Mint as the linked thread shows - don't know how well that will go.

For me, at least, this is closed.  But I'm not allowed to mark it "Solved" because I don't have a solution.  Therefore the thread remains open and will someday be removed as a dead thread.

---

