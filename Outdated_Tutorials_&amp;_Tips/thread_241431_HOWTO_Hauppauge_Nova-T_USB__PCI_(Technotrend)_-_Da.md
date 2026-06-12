---
title: "HOWTO: Hauppauge Nova-T USB / PCI (Technotrend) - Dapper"
date: 2006-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by goldaryn on 2006-08-22
Hi all.. 

I had a terrible time getting my Nova-T USB (Technotrend chipset) working.  So here's a guide.

Basically, you need the firmware for the device. This is made easy by a script that's in the linux-doc package.
This automatically downloads the Windows drivers and extracts the firmware for you. All you have to do then is copy it to the right place.

Here we go.

**(1) Plug in the device, and check that Linux can see it:**

type in:

$ sudo lsusb         

(or, for PCI cards, sudo lspci )

I get:

*Bus 002 Device 002: ID 0b48:1005 TechnoTrend AG Technotrend/Hauppauge USB-Nova*

There it is.. 

**(2) Let's update sources.list so that we can get the linux-doc package**

Dapper: [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)
Edgy: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories)
Feisty: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

**(3) Get the linux-doc package.**

$ sudo apt-get install linux-doc

**(4) Find the script and run it**

For me it's /usr/share/doc/linux-doc-2.6.15/Documentation/dvb/get_dvb_firmware.gz

# If you can't find it, do this
#  
# $ sudo updatedb
# $ locate get_dvb

Copy it to your home dir, extract it, make it executable:

$ cp /usr/share/doc/linux-doc-2.6.15/Documentation/dvb/get_dvb_firmware.gz ~
$ cd ~
$ gunzip get_dvb_firmware.gz
$ sudo chmod +x get_dvb_firmware

Now run it:

$ ./get_dvb_firmware tda10046    # tda10045 for PCI cards

Nearly finished! The firmware has now been extracted, now copy it to where it should be.

$ sudo cp *.fw /lib/firmware

Finished! The firmware is in place. Now reboot your PC.

You should now be able to scan and watch TV channels through Kaffeine (look for it in Synaptic). 

You will need to know the name of your local DVB transmitter, Google it. (Mine is Winter Hill)

g.

---

### Post by silid on 2007-04-02
thanks for this post.

i have read and used this before - but it took me so long to find it this time that i have replied to make it easier to find.

it is funny that support for these devices is better under linux than windows.

---

### Post by Ronius on 2007-05-01
Hi there

Do you happen to know any way I can just check that my Nova USB-T is properly working with Ubuntu? I'm using Kaffeine and trying to scan for channels using settings I found for Belmont UK (which don't appear to be included in Kaffeine). However, it does not seem to be receiving any of them, and I'm not sure whether it's because there is a bad signal here (which would make sense in student accommodation) or because something has gone wrong setting up my box.

It's probably worth noting that occasionally the signal bar goes up to 50% when I scan, and the SNR bar is nearly always at 90-100%; however, no channels appear.

Thanks a lot

Watty

---

### Post by silid on 2007-05-03
If kaffeine allows you to do a scan then it has detected the hardware. notice what happens if it is not conencted to your computer when you start kaffeine. I would suggest that it is either a weak signal or more likely the frequencies you are scanning are not quite right.

---

### Post by zjxc50 on 2007-08-10
Note: Looks like technotrend have done some housekeeping!!
Found the .zip files on the url below

$ ./get_dvb_firmware tda10046
--21:14:33--  [http://www.technotrend.de/new/217g/tt_budget_217g.zip](http://www.technotrend.de/new/217g/tt_budget_217g.zip)
           => `tt_budget_217g.zip'
Resolving [www.technotrend.de](www.technotrend.de)... 88.198.155.229
Connecting to www.technotrend.de|88.198.155.229|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:14:34 ERROR 404: Not Found.

try this one....

[http://www.technotrend-online.com/download/software/217/tt_budget_217g.zip](http://www.technotrend-online.com/download/software/217/tt_budget_217g.zip) 
or http://www.technotrend-online.com/download/software/217/{filename}

Cheers

:popcorn:

---

### Post by mtron on 2007-08-12
there are new hg drivers and a new firmware for this stick. It had problems with disconnects.

 See [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick)

---

