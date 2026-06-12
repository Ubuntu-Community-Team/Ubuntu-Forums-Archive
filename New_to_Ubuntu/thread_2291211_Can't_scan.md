---
title: "Can't scan"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by sab7 on 2015-08-18
My Brother DCP350C prints but not scans. Brother officially supports this device but, although that, the printer doesn't scan. It isn't event recognized by the system. On Windows it works, but not on Linux.
I also tried to use VueScan (that have built in drivers for my device) with CrossOver (a software similar to Wine) but it doesn't work.
How can I solve that? Thank You.

---

### Post by VMC on 2015-08-18
Did you read this:
[http://www.hamrick.com/vuescan/brother_dcp_350c.html](http://www.hamrick.com/vuescan/brother_dcp_350c.html)

Also on that page is this:
[http://www.freecolormanagement.com/sane/libusb.html](http://www.freecolormanagement.com/sane/libusb.html)

---

### Post by Bucky Ball on 2015-08-18
Install HPLip from the Software Centre then go to [this]("http://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=dcp350c_all") page and download the Linux (.deb) at the bottom of the page.

Double click the .deb file and it should start installing with Software Centre. You will then need to delete the printer you have installed and 'Add' the printer again in 'Printers', choosing the correct driver when you get to that part, which you hopefully now have. Good luck.

---

### Post by sab7 on 2015-08-18
Why install HPlip if my printer's brand is Brother? :-/

---

### Post by Bucky Ball on 2015-08-18
Oops, sorry. Just disregard that. Did you try installing the driver I linked to then adding the printer? Please confirm and let us know what happened.

Uninstall HPLip if you did install. Makes no difference either way but if you don't need, remove.

---

### Post by HermanAB on 2015-08-19
See if the device is listed:
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

If not, then you are outta luck...

---

### Post by sab7 on 2015-08-19
Thank You for your support.
Yes, I installed the official drivers from Brother but the scanner doesn't work. And no, the sane project doesn't support my device :|
It's strange because I'm able to print with it but not to scan...

---

### Post by VMC on 2015-08-19
You might try this guys solution.
[http://forums.linuxmint.com/viewtopic.php?f=51&t=185094](http://forums.linuxmint.com/viewtopic.php?f=51&t=185094)

---

### Post by mollie4168 on 2015-08-20
I have a Brother DCP7065DN, and it stopped scanning after my most recent upgrade.  I tried your solution using my printer model.  When I get to the software center, it says this version of brscan is bad quality and I shouldn't install it.  What do you think?

---

### Post by thane1 on 2015-08-21
hi sab7;     I spent quite a bit of time initially getting my brother dcp-7030 to print and scan.  I did however get it to do both.  On the USA Brother site there are 2 driver downloads (32 and 64 bit) on the following page [HTML]http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp350c_all&os=128[/HTML] .  Installing the scanner driver is similar to installing the printer drivers.  However there may be a couple of things you need to address first.  Back when I first got it to work I made a howto for myself, which might help you along.  It's from an older version of mint, but you may find the same /usr/lib problem which needs a bit of work for your system.  See if you can pick anything out of this to help:

```
Brother 64 bit scanner driver instl'n:

I had a problem at first with this, to the point that I made posts on Linux Mint forums.  Following are my question post followed by the post of how I fixed the problem. 

New Mint instl'n and cannot get scanner to work on a Brother DCP7030.  It worked fine on my old ubuntu 10.10 instl'n.  What I've tried so far:
Brand new Mint 12 amd64 instl'n ==>     Linux Mint 12 (Lisa) 3.0.0-12-generic gnome 3.2.1
All available updates installed as of today
Followed procedure from the Brother website,   http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html which I used  in ubuntu before to the letter :&#8211; 
install sane-utils
download the brscan3 file =>         brscan3-0.2.11-4.amd64.deb
turn on printer/scanner then insert usb cable
install the driver with sudo dpkg -i &#8211;force-all brscan3-0.2.11-4.amd64.deb  (n.b. The same caveat about copying and pasting this line in terminal as for the printer drivers.)
check if driver is installed =>         dpkg -l | grep Brother     its there
modified the "/lib/udev/rules.d/40-libsane.rules" file, adding  
# Brother scanners 
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"  to the end of the device list before the line # The following rule will disable ...
restarted the system

Used same Simple Scan program from the menus, that I'd used with ubuntu.  Will not recognize scanner in Mint.
Installed the gnome users/groups program to get access to the groups settings.
Added my user name to the saned and scanners groups.
Restarted and tried Simple scan again &#8211; no luck.
Installed Skanlite and tried that program &#8211; no luck.
After searching around I check /etc/sane.d/dll.conf file for the Brother entry, which is apparently supposed to appear at the bottom of the file.  There is a  brother3 addition at the bottom of the listings.
Don't know, where to go from here.  Thanks

And here is the final answer post:

Re: Got it!
by kingsthane on Tue Jan 24, 2012 8:06 pm 
Got it! Re-read the Brother site pages with a fine toothed comb and found this page 

http://welcome.solutions.brother.com/bs ... tml#f00101

Below the line "FAQ (SCANNER)" the second line gave me the solution. I just needed to copy all of the files from /usr/lib64/ into /usr/lib/ then restart computer and now the scanner works. Thank you Brother website!

Note for the above posts:  Not sure if I needed to install the gnome users and groups program or not for this to work.  But it was available apt-get install and it works fine in mint.  
         sudo apt-get install gnome-system-tools

Also after installing Linux Mint 14.1 the files in /usr/lib64 were also in /usr/lib already after installing the driver.  A reboot and the scanner worked fine.  I still needed to modify the /lib/udev/rules.d/40-libsane.rules file though as described above.  I installed the brscan driver and got scanner working without needing to unplug printer usb, turn printer on and then replug the usb in.  So the scanner can be set up independantly of the printer drivers.
```

Please note that for some reason in the line ```
install the driver with sudo dpkg -i &#8211;force-all brscan3-0.2.11-4.amd64.deb  (n.b. The same caveat about copying and pasting this line in terminal as for the printer drivers.)
``` listed above, the long dash displayed before the "force" command is actually two short dashes with no space between.    Hope this helps.

---

### Post by thane1 on 2015-08-21
Found the following page on the Brother site, which may help as well:

[HTML]http://support.brother.com/g/s/id/linux/en/instruction_scn1a.html?c=us&lang=en&prod=dcp350c_all&redirect=on[/HTML]  cheers sab7

---

### Post by sab7 on 2015-09-05
Thank you Everyone for Your replies.
I tried the solution posted by the user VMC and althouth that solution is recommended by Brother itself, it does not work.
May the last solution be: Buying another cheap used scanner supported by Sane? :confused::frown:

---

