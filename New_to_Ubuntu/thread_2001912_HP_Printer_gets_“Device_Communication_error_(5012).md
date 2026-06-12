---
title: "HP Printer gets “Device Communication error (5012)”"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Ralph L on 2012-06-11
I have spent considerable time getting my HP Photosmart C6180 all-in-one (printer, fax, scanner, copier) working on Lucid.  I have seen posts indicating that other people were having similar problems so I thought I would post the solution.

I discovered that the hp-setup (no parameters) GUI and hp-toolbox both set the printer URI to &#8220;hp:/net/Photosmart_C6100_series?zc=HP547597&#8221; rather than to &#8220;hp:/net/Photosmart_C6100_series?ip=192.168.0.31&#8221; as it should be. On Lucid you can go to Mainmenu>System>Administration>Printing (system-config-printing if you need to install it with Synaptic) and change this. Right click on the printer icon, select Properties and edit the URI box. For the printer (not for a printer/fax) you can also set the URI to "socket://<your printer URL>:9100" and it will work. However, if you have a printer/fax you need to use &#8220;hp:/net/Photosmart_C6100_series?zc=HP547597&#8221;. Also the fax device (the icon Properties) must have a Make/Model of &#8220;HP Fax hpcups&#8221;. This cannot be changed with system-config-printing. The only way I found to get the fax to work was to use

hp-setup -i 192.168.0.31

or to use the ```
hp-toolbox
``` GUI. The toolbox sets the URI wrong, but it can be corrected in system-config-printing. The Model/Make parameters are set correctly by toolbox. Note that my printer URL is 192.168.0.31. Yours will be different.

I am about to try this same setup on Precise Pangolin 12.04.

Hope this helps somebody.

---

### Post by robert.kratky on 2012-10-20
Thanks, this helped.

---

### Post by andybnj on 2012-12-15
Thanks so much for this tip, I ran thru all the problems (backend failed, jobs in held state, device comm error,etc).  Uninstalled and reinstalled hplip, still not working.  Finally reinstalled hplip again, went thru the HP device manager (toolbox) where I had to first connect via usb.  Problem seems to be that after the setup specifying wireless, it still has the uri as usb.  So after the initial setup, deleted the printer and then added again with the hp-setup -i <ip address> ... so now I am in business and printing from 12.04 to my Deskjet 3520.

---

### Post by Ralph L on 2013-02-18
I made a mistake in the directions in Post #1 for the printer and fax URI.  The printer URI should be "hp:/net/Photosmart_C6100_series?ip=192.168.0.31" (no quotes).  If you set up the printer/fax with hp-toolbox, this URI needs to be edited into the Device URI setting using system-config-printer.  Likewise "hpfax:/net/Photosmart_C6100_series?ip=192.168.0.31" needs to be edited into the fax Device URI using system-config-printer.

---

### Post by DavidLG on 2013-05-28
I have spent days trying to figure out why I could only print with a USB cable to my HP 3520 printer.  I deleted the printer after set up, entered the command hp-setup -i <ip address>, and it did the trick for me.  Tanks for the tip!

---

### Post by christ8 on 2013-11-22
Thanks David for this post.  I always have this hp error and it really helps to have this reference to fix it.

---

### Post by steve69 on 2014-01-09
If any of you are using a Netgear R7000 Nighthawk router, there is a firmware upgrade that fixes this issue for Macs as well as Ubuntu machines.  The troubleshooting that cinched it for me was an inability to ping the printer.  After the firmware update, all is well.

---

