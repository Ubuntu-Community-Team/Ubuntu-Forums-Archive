---
title: "HOWTO: Speedtouch USB ADSL Modem"
date: 2005-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by darrell on 2005-06-27
Since Hoary is running on kernel 2.6.10, you do not need the speedtouch package to get these adsl modems to work. All you actually need apart from a Hoary installation cd is some firmware for your modem.

I've now made this specific to the UK, as that's all I can test. In other countries using PPPoA it should work by changing the VPI/VCI numbers. (see below). Otherwise, [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) may be able to help.

The procedure I outlined in my previous posts on configuring speedtouch is broken because the latest firmware .deb contains renamed firmware files, so the hotplug script provided with the speedtouch package can't find them, exits with an error and never gets around to bringing up the connection with the ISP. It would be simple enough to replace the hard-coded firmware file names with the new ones, but why install a package which is not needed? This new method does without the speedtouch package, but includes creating an alternative hotplug setup so that the automatic connection to the ISP still happens after the adsl line comes up.

The HOWTO follows.

In this HOWTO, I assume that you have no working net connection in Ubuntu. For now, you will need a computer that is capable of connecting to the internet, whether this be another computer, or your Ubuntu box booted with some other operating system (maybe you've set it up to dual-boot Ubuntu and Windows).

I am working on utilizing the firmware which you should have on your Speedtouch Windows installation cd - I will update the howto once I have demonstrated to myself that this works. You will still need a net connection at some point to read/print these instructions, though!

**Step 1: Stuff to download**

Get hold of some firmware for your modem. The firmware is the code which needs to be loaded into the modem every time it is plugged in or the computer is switched on. Without the firmware, nothing else will happen.

There is a useful debian package containing the firmware at [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb) 

You might also like to save this HOWTO webpage - then you can copy and paste configuration file stuff later on, rather than type it in from a printed copy of the HOWTO.

I have created a hotplug script called speedtch.txt which is attached to this post. download this.

So, confirm before you leave your net-connected pc, that you have the above firmware package, the hotplug script, and these instructions, on a floppy, or burnt to a cd, or possibly on a Windows partition on your dual-boot Ubuntu box, which you can mount in Ubuntu.

**Step 2: Boot into Ubuntu and install the necessary software**

You will need to install the package *libatm1* - put your Hoary cd in the drive and open a terminal. Then type: 
```
sudo apt-get install libatm1
``` 
This should install the package from the Hoary cd
Now insert the floppy/cd containing the firmware downloaded earlier (or mount the relevant partition if you managed to save somewhere on your Ubuntu machine) and type:
```
sudo dpkg -i /path/to/your/download/speedtouch-firmware_0.3012k_all.deb
```
This will install the firmware files to your computer.

**Step 3: Configure your software**

load the pppoatm module, and set up your machine so it is loaded at every boot:
```
sudo modprobe pppoatm
sudo gedit /etc/modules
```
in the editor window, add 
```
pppoatm
``` 
at the bottom of the list, save and exit.

Create a pppd connection script to control logging on to your ISP:
```
sudo cp /usr/share/doc/ppp/examples/peers-pppoe /etc/ppp/peers/adslscript
sudo gedit /etc/ppp/peers/adslscript
```

change the line:
```
# user "myusername@myprovider.net"
```
to:
```
user "your-own-isp-username"
```

remove:
```
# Load the pppoe plugin. Change the ethernet interface name if needed.
plugin rp-pppoe.so
eth0
```
and replace with
```
# These options configure pppd to talk with the kernelspace speedtch driver.
# Don't forget to adapt the VP.VC pair to your ISP/country settings.
# (see http://www.linux-usb.org/SpeedTouch/faq/index.html#q12)
plugin pppoatm.so
0.38 #UK
```

Towards the bottom, comment out (ie put a # at the beginning of the line):
```
noaccomp

*and*

default-asyncmap
```
save and exit the editor

Now, set up your isp password:
```
sudo gedit /etc/ppp/chap-secrets
```
In the editor window, add a line:
```
your-isp-user-name * your-isp-password *
```
Save file and close editor
```
sudo gedit /etc/ppp/pap-secrets
```
In the editor window, add an identical line to that just added to the chap secrets file. Save and close editor. You will only use one of these two files, depending on the authentication method used by your isp, but is doesn't hurt to have both on your system.

Finally, setup the hotplug system to automatically connect when the modem is plugged in and at boot time:
```
sudo cp /your/path/to/speedtch.txt /etc/hotplug/usb/speedtch
```
Make this script executable 
```
sudo chmod +x /etc/hotplug/usb/speedtch
```

Now, enter
```
tail -f /var/log/messages
```
plug in your modem and (hopefully) watch it connect. you should see in the messages display, the speedtch module being loaded, the adsl line synchronising, then the pppd process establishing the connection, and your computer being allocated its ip address and dns servers.
use ctrl-c to get out of the scrolling messages display.

You should now be connected to the internet. 

Please post any questions/problems with the above, and I will try to help.

Darrell

---

### Post by camara on 2005-07-05
Hi, Darrell. First of all thanks for the help. The installation of the speedtouch 330 (frog) on my Ubuntu has been taking my days lately. With your instructions, it went *almost* there!! So I feel there must be a small tweak  somewhere to do yet,

I did everything as you say. Then, when I restart the computer and try to use internet, it just stalls there... no error sign (I guess there'd be a timeout sooner or later), no download sign, nothing! I'm from Portugal, so I used 0.35 in the VPI/VCI thing.

There is one slight thing to add (and it may make the difference!): when I installed Ubuntu yesterday, I connected it via ethernet using another (windows) computer, so that the installer could get stuff from outside. I then ran your instructions. I removed the ethernet cable, plugged the modem, restarted, and the rest you already know...

Big thanks in advance

---

### Post by Ifumag on 2005-07-05
Thanks for the help there pal, when i finally set it all up i felt so good, truly a moment of pure [Frisson](http://gamufi.com)

---

### Post by darrell on 2005-07-05
Hi Camara

Do you get an IP address assigned from your ISP? - to check, from a command line:

```
ifconfig
```

you should get something like
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35849281 (34.1 MiB)  TX bytes:35849281 (34.1 MiB)

ppp0      Link encap:Point-to-Point Protocol
          **inet addr:80.229.150.88  P-t-P:195.166.128.72  Mask:255.255.255.255**
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:32725  Metric:1
          RX packets:417285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:464076351 (442.5 MiB)  TX bytes:44431357 (42.3 MiB)
```

I've highlighted the important bit in bold. If you've got this (your IP address will of course be different to mine - you just need to have one), it's probably a routing issue, especially since you configured an ethernet connection as your default connection during installation. Type:

```
route
```

you should have a default route which points to your adsl modem interface (probably ppp0):

```
**default**         lo0-plusnet.pte 0.0.0.0         UG    0      0        0 **ppp0**
```

but you've probably got one which points to your ethernet interface (for example eth0). In that case:

```
sudo route del default
sudo poff adslscript
sudo pon adslscript
route
```

you should now see a default route pointing to your speedtouch interface.

If this has solved your problem, you need to make sure that your ethernet interface isn't set as the default route the next time you boot. Do this by editing your /etc/network/interfaces file:

```
sudo gedit /etc/network/interfaces
```

and comment out the "gateway" instruction in the ethernet section (probably eth0). Also comment out any lines which start with "dns".

Please let me know how you get on.

I should give credit to linux speedtouch pages, referenced in the HOWTO above. All I'm really doing is rehashing the information there.

Darrell

---

### Post by camara on 2005-07-05
Hi Darrel,

Here go the results for the commands you suggested:
>ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:EB:82:82  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Memory:feafc000-0 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:165740 (161.8 KiB)  TX bytes:165740 (161.8 KiB)



>route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

I think it is strange that it doesn't even start the ppp0. Is there anything missing in my system? The whole process ran smoothly, following every step you described. 

Thanks again

---

### Post by darrell on 2005-07-06
OK, all my stuff yesterday about routing was a bit premature - might still need it, though. From your ifconfig output the ppp interface has not been brought up, so lets go back a bit. 

do
```
tail -f /var/log/syslog
```
unplug and replug the modem. Post the syslog output here. 

Can you connect to the 'net from another machine while trying all this on your ubuntu box? if so, we could go sort of interactive here on the forums - let me know when you'd like to do this.

Darrell.

---

### Post by camara on 2005-07-06
Darrel,

Here goes the log you asked for:

Jul  6 09:50:06 localhost pppd[8539]: pppd 2.4.2 started by root, uid 0
Jul  6 09:50:06 localhost kernel: usb 4-1: found stage 1 firmware speedtch-1.bin.0
Jul  6 09:50:06 localhost kernel: usb 4-1: found stage 2 firmware speedtch-2.bin.0
Jul  6 09:50:09 localhost pppd[8492]: connect(0.35): Address already in use
Jul  6 09:50:09 localhost pppd[8418]: connect(0.35): Address already in use
Jul  6 09:50:09 localhost pppd[8539]: Using interface ppp0
Jul  6 09:50:09 localhost pppd[8492]: Exit.
Jul  6 09:50:09 localhost pppd[8418]: Exit.
Jul  6 09:50:09 localhost pppd[8539]: Connect: ppp0 <--> 0.35
Jul  6 09:50:10 localhost kernel: ADSL line is synchronising
Jul  6 09:50:23 localhost kernel: usb 4-1: USB disconnect, address 4
Jul  6 09:50:23 localhost kernel: usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Jul  6 09:50:23 localhost kernel: Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
Jul  6 09:50:23 localhost kernel:  [pg0+542452267/1070015488] usb_unlink_urb+0x47/0x7e [usbcore]
Jul  6 09:50:23 localhost kernel:  [pg0+544612127/1070015488] speedtch_usb_disconnect+0x2b/0x6a [speedtch]
Jul  6 09:50:23 localhost kernel:  [pg0+542433446/1070015488] usb_unbind_interface+0x38/0x69 [usbcore]
Jul  6 09:50:23 localhost kernel:  [device_release_driver+80/92] device_release_driver+0x50/0x5c
Jul  6 09:50:23 localhost kernel:  [bus_remove_device+57/104] bus_remove_device+0x39/0x68
Jul  6 09:50:23 localhost kernel:  [device_del+67/103] device_del+0x43/0x67
Jul  6 09:50:23 localhost kernel:  [pg0+542456104/1070015488] usb_disable_device+0x65/0xd6 [usbcore]
Jul  6 09:50:23 localhost kernel:  [pg0+542440580/1070015488] usb_disconnect+0x96/0x10e [usbcore]
Jul  6 09:50:23 localhost kernel:  [pg0+542443569/1070015488] hub_port_connect_change+0x5e/0x32a [usbcore]
Jul  6 09:50:23 localhost kernel:  [pg0+542444828/1070015488] hub_events+0x21f/0x2d0 [usbcore]
Jul  6 09:50:23 localhost kernel:  [pg0+542445005/1070015488] hub_thread+0x0/0xe4 [usbcore]
Jul  6 09:50:23 localhost kernel:  [pg0+542445034/1070015488] hub_thread+0x1d/0xe4 [usbcore]
Jul  6 09:50:23 localhost kernel:  [autoremove_wake_function+0/58] autoremove_wake_function+0x0/0x3a
Jul  6 09:50:23 localhost kernel:  [ret_from_fork+6/20] ret_from_fork+0x6/0x14
Jul  6 09:50:23 localhost kernel:  [pg0+542445005/1070015488] hub_thread+0x0/0xe4 [usbcore]
Jul  6 09:50:23 localhost kernel:  [autoremove_wake_function+0/58] autoremove_wake_function+0x0/0x3a
Jul  6 09:50:23 localhost kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Jul  6 09:50:23 localhost pppd[8539]: Terminating on signal 15.
Jul  6 09:50:28 localhost last message repeated 5 times
Jul  6 09:50:28 localhost kernel: usb 4-1: new full speed USB device using uhci_hcd and address 5
Jul  6 09:50:29 localhost kernel: usb 4-1: device descriptor read/64, error -71
Jul  6 09:50:29 localhost pppd[8539]: Connection terminated.
Jul  6 09:50:29 localhost pppd[8539]: Exit.
Jul  6 09:50:29 localhost kernel: usb 4-1: khubd timed out on ep0in
Jul  6 09:50:33 localhost usb.agent[8847]:      speedtch: already loaded
Jul  6 09:50:33 localhost pppd[8884]: Plugin pppoatm.so loaded.
Jul  6 09:50:33 localhost pppd[8884]: PPPoATM plugin_init
Jul  6 09:50:33 localhost pppd[8884]: PPPoATM setdevname - remove unwanted options
Jul  6 09:50:33 localhost pppd[8884]: PPPoATM setdevname_pppoatm - SUCCESS:0.35
Jul  6 09:50:33 localhost usb.agent[8847]:      speedtouch: loaded successfully
Jul  6 09:50:33 localhost pppd[8885]: pppd 2.4.2 started by root, uid 0
Jul  6 09:50:33 localhost usb.agent[8895]:      speedtch: already loaded
Jul  6 09:50:33 localhost pppd[8945]: Plugin pppoatm.so loaded.
Jul  6 09:50:33 localhost pppd[8945]: PPPoATM plugin_init
Jul  6 09:50:33 localhost pppd[8945]: PPPoATM setdevname - remove unwanted options
Jul  6 09:50:33 localhost pppd[8945]: PPPoATM setdevname_pppoatm - SUCCESS:0.35
Jul  6 09:50:33 localhost usb.agent[8895]:      speedtouch: loaded successfully
Jul  6 09:50:33 localhost usb.agent[8865]:      speedtch: already loaded
Jul  6 09:50:33 localhost pppd[8999]: Plugin pppoatm.so loaded.
Jul  6 09:50:33 localhost pppd[8999]: PPPoATM plugin_init
Jul  6 09:50:33 localhost pppd[8999]: PPPoATM setdevname - remove unwanted options
Jul  6 09:50:33 localhost pppd[8999]: PPPoATM setdevname_pppoatm - SUCCESS:0.35
Jul  6 09:50:33 localhost usb.agent[8865]:      speedtouch: loaded successfully
Jul  6 09:50:33 localhost pppd[8946]: pppd 2.4.2 started by root, uid 0
Jul  6 09:50:33 localhost pppd[9000]: pppd 2.4.2 started by root, uid 0
Jul  6 09:50:33 localhost kernel: usb 4-1: found stage 1 firmware speedtch-1.bin.0
Jul  6 09:50:33 localhost kernel: usb 4-1: found stage 2 firmware speedtch-2.bin.0
Jul  6 09:50:37 localhost pppd[8946]: connect(0.35): Address already in use
Jul  6 09:50:37 localhost pppd[8885]: connect(0.35): Address already in use
Jul  6 09:50:37 localhost pppd[9000]: Using interface ppp0
Jul  6 09:50:37 localhost pppd[8946]: Exit.
Jul  6 09:50:37 localhost pppd[8885]: Exit.
Jul  6 09:50:37 localhost pppd[9000]: Connect: ppp0 <--> 0.35
Jul  6 09:50:38 localhost kernel: ADSL line is synchronising

I'll be around during next few hours so we can proceed with this interaction! ;) 
I have a laptop connected to the internet (with that famous modem) in the meantime. This laptopt has been the actual router of my home little net...

---

### Post by darrell on 2005-07-06
sorry camara, I got into a urgent, long, long phone call. Am looking at your log now.

---

### Post by darrell on 2005-07-06
let's try to do things manually.

first of all, move the hotplug script out of the way so it doesn't run:
```
sudo mv /etc/hotplug/usb/speedtch /etc/hotplug/usb/speedtchxxx
```
get a second terminal going to monitor the syslog:
```
tail -f /var/log/syslog
```
unplug the modem, wait a few seconds until you see in the log that the unplugging has been recognised.
in the first terminal again:
```
sudo rmmod speedtch
```
now plug in the modem again and report what the syslog says (it should load the speedtch module, load the firmware, and bring up the adsl line - this could take 30 seconds or so)

---

### Post by angelwings on 2005-07-06
Hi there,

Camara I have the same problem has you, and I think the problem is that your ISP don't use PPPoATM, it uses PPPoE (I live in Portugal too, and my isp is clix), but I can't get my connection to work with the [ http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html ]( http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html ) tutorial using the PPPoE method, maybe darrell can help us connecting with the pppoe protocol.

---

### Post by camara on 2005-07-06
Darrel, 

I just did as you were saying, and the syslog gives:
...
Jul  6 21:20:53 localhost kernel:  [pg0+542445005/1070015488] hub_thread+0x0/0xe4 [usbcore]
Jul  6 21:20:53 localhost kernel:  [autoremove_wake_function+0/58] autoremove_wake_function+0x0/0x3a
Jul  6 21:20:53 localhost kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Jul  6 21:21:21 localhost kernel: usbcore: deregistering driver speedtch
Jul  6 21:21:39 localhost kernel: usb 4-1: new full speed USB device using uhci_hcd and address 3
Jul  6 21:21:39 localhost kernel: usb 4-1: device descriptor read/64, error -71
Jul  6 21:21:39 localhost usb.agent[8151]:      speedtch: already loaded
Jul  6 21:21:39 localhost usb.agent[8151]:      speedtouch: loaded successfully
Jul  6 21:21:39 localhost usb.agent[8158]:      speedtch: already loaded
Jul  6 21:21:39 localhost usb.agent[8158]:      speedtouch: loaded successfully
Jul  6 21:21:40 localhost usb.agent[8163]:      speedtch: loaded successfully
Jul  6 21:21:40 localhost usb.agent[8163]:      speedtouch: loaded successfully
Jul  6 21:21:40 localhost kernel: usb 4-1: modprobe timed out on ep0in
Jul  6 21:21:40 localhost kernel: usbcore: registered new driver speedtch
Jul  6 21:21:40 localhost kernel: usb 4-1: found stage 1 firmware speedtch-1.bin.0
Jul  6 21:21:40 localhost kernel: usb 4-1: found stage 2 firmware speedtch-2.bin.0
Jul  6 21:21:45 localhost kernel: ADSL line is synchronising
Jul  6 21:22:08 localhost kernel: DSL line goes up
Jul  6 21:22:08 localhost kernel: ADSL line is up (512 Kib/s down | 128 Kib/s up)


Indeed, Angelwings is right!!! Our protocol should be pppoE!... I guess I must  install br2684ctl... I just did.

I'll take a look back at that page (I have done it ALL through already several times...). Anyway, I don't want to mess too much so that Darrel can follow my steps. 

Best

---

### Post by camara on 2005-07-07
[QUOTE=angelwings]Hi there,

Camara I have the same problem has you, and I think the problem is that your ISP don't use PPPoATM, it uses PPPoE (I live in Portugal too, and my isp is clix), but I can't get my connection to work with the [ http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html ]( http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html ) tutorial using the PPPoE method, maybe darrell can help us connecting with the pppoe protocol.[/QUOTE]

Angelwings: have you tried this one?
[http://s1x.homelinux.net/projects/speedtouch_suite](http://s1x.homelinux.net/projects/speedtouch_suite)
I have... and was also unlucky!... :(:(
all went well until I got an I/O error with some files (I think it were some xml files)

Good luck!

---

### Post by angelwings on 2005-07-08
Finally my internet connection is working!
I had reinstalled ubuntu, then I followed the [ http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html ]( http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html ) step by step

and it's working now, i'm so happy

good luck camara, try reinstalling the system again, then follow the tut.

---

### Post by camara on 2005-07-08
I think I found my problem (although I'll go again with all the process...). My connection is RDIS (ISDN), so I guess the driver was wrong... 
By the way, did you install Ubuntu without net? I mean, I have installed it using my laptop as a router... I wonder if that's a problema also.

Obrigada!

---

### Post by angelwings on 2005-07-08
yeah, installed without net using the hoary amd64 install cd.

De nada!

---

### Post by camara on 2005-07-08
UP and RUNNING!!!! YEESSSS!
Thanks all!

Next step: now make my desktop become de router of the home net... GLUP

---

### Post by angelwings on 2005-07-08
YAY! grats :P

yeah, I would like to do that too

---

### Post by pinguimtux on 2005-09-04
Hey guys! I'm from Portugal too, and I'm using Sapo ADSL.

I did what it says here [http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html) 2 ou 3 times already, but no luck. It did work with Suse though. I guess the problem is that the firmware isn't loading, because the LED on the right stays orange instead of green...I guess I'll reinstall the system, but I'm not sure if this will fix the problem...If someone as another way..just let me know!

Fiquem bem!

---

### Post by pinguimtux on 2005-09-04
Ok! I finally have a working internet connection in my Ubuntu system!

  :grin:

---

### Post by genbie on 2005-09-05
How do I manually disconnect/connect? This is useful if I want to reconnect after my connection is terminated by the ISP for example. Issuing "pppd call speedtouch" did not work :-(

---

### Post by vbmaster on 2005-09-05
Hey Guys!

Another one from Portugal here.  

I'm posting in this thread because in the past I did a lot of search to put my speedtouch modem running in a light Linux Distro that I had. Unfortunatelly I was unsuccessful.

Now, i'm about to put ubuntu on my system and I have already read a lot of tuturials. By your answers I think the best one for me to look in first is this:

[http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html)

But in a specific step it ask us for our login and ISP password to put in a file (chap-secrets I think), and the problem is that I was wondering if this is a secure method?

Can anyone claryfy me? For the Portugal ones, my ISP is SAPO ADSL.

Thanks a lot. ;) and....sorry my english. :P

---

### Post by jeffreyvergara.NET on 2005-09-13
[QUOTE=genbie]How do I manually disconnect/connect? This is useful if I want to reconnect after my connection is terminated by the ISP for example. Issuing "pppd call speedtouch" did not work :-([/QUOTE]

I also have a problem with this... how can I reconnect after disconnection? is there any way to autoconnect after disconnection. I've just successfuly installed Ubuntu and configured my ADSL so i havn't encountered any disconnections yet.


note: a total linux newbie here

---

### Post by Keffin on 2005-09-13
[QUOTE=jeffreyvergara.NET]
Quote:
Originally Posted by genbie
How do I manually disconnect/connect? This is useful if I want to reconnect after my connection is terminated by the ISP for example. Issuing "pppd call speedtouch" did not work


I also have a problem with this... how can I reconnect after disconnection? is there any way to autoconnect after disconnection. I've just successfuly installed Ubuntu and configured my ADSL so i havn't encountered any disconnections yet.


note: a total linux newbie here[/QUOTE]

Following the naming in the guide, you would call "pppd call adslscript" to reconnect. Alternatively you can just unplug the modem from your computer, wait a couple of seconds, then plug it back in again. The latter assumes you installed the speedtch hotplug script as per the guide. I have found no way to auto-connect on disconnection, but then I haven't tried very hard.

---

### Post by Gallows on 2005-09-15
I'd just like to add that this howto is spectacular - I use PPP over ATM using UK based ISP Pipex.  It worked 1st time absolutely no worries!

-Gallows

---

### Post by jeffreyvergara.NET on 2005-09-17
hehehe... I don't need the how to reconnect anymore, i just noticed that the Internet connection reconnects it self. but i noticed that when i resume my pc at suspended mode, the connection has been disconnected, because my gaim IM accounts has been disconnected, and my downloads are in 0kbps.

---

### Post by Kirin on 2005-09-19
I'm (trying) to set up a friend with Ubuntu, the only obstacle being the damn SpeedTouch modem. She – sadly – is inside Kingston Communications' sphere of influence. I found the [settings](http://www.help.karoo.net/bbsettings.html) on the KC website. I changed the VP/VC pair to 1.50, but nothing happens after the modem syncs. I suspect it may have something to do with this bit:

> Encapulation: RFC2364 PPPoATM (LLC) 

Which I *think* means that it uses LLC encapulation, which – I think – isn't standard in the UK. Am I right? If so, how would I go about setting it to use LLC?

Thanks for any help anyone can give me!

---

### Post by gruszczy on 2005-10-08
Hello!

I tried to configure my modem, using this HOWTO and linux-usb.org HOWTO, but it didn't work. However, when I look in the log I can see:

```
Oct  9 01:07:34 ubuntu kernel: [4295853.102000] ADSL line is synchronising
Oct  9 01:07:49 ubuntu kernel: [4295868.102000] ADSL line is up (384 Kib/s down | 96 Kib/s up)
```

I try to open some website in mozilla, but it can't be done. I used script from this HOWTO and tried typing in pppd call, but none of these work. While using pppd call I can see in the log, that chap-secrets work fine, dns servers are found, but still, I cannot connect with any website (and there are no othere messages in the log). Cany anyone help me?

---

### Post by Grae on 2005-11-16
Thanks for the great howto, i've tried others but none of them would work for me! now I can begin exploring Ubuntu's apt-get feature!!! :D

---

### Post by Grae on 2005-11-16
hopefully someone can help with this!

when i reboot i find it hasn't connected to the net and i have found if I ```
sudo modprobe pppoatm
```
It can then connect when i call the adslscript, whereas before it wouldn't!

Am i just being impatient or is something up?

Oh I've checked /etc/modules and pppoatm is there, should it be further up the list as opposed to at the end?

---

### Post by Grae on 2005-11-17
Scrap that i was just being impatient!!!

sorry
:oops:

---

### Post by rufian1 on 2005-12-10
[QUOTE=gruszczy]Hello!

I tried to configure my modem, using this HOWTO and linux-usb.org HOWTO, but it didn't work. However, when I look in the log I can see:


Code:
Oct  9 01:07:34 ubuntu kernel: [4295853.102000] ADSL line is synchronising
Oct  9 01:07:49 ubuntu kernel: [4295868.102000] ADSL line is up (384 Kib/s down | 96 Kib/s up)
I try to open some website in mozilla, but it can't be done. I used script from this HOWTO and tried typing in pppd call, but none of these work. While using pppd call I can see in the log, that chap-secrets work fine, dns servers are found, but still, I cannot connect with any website (and there are no othere messages in the log). Cany anyone help me?[/QUOTE]
Thats is exactly my same problem. Modem seems to sync but no navigation is possible. Tried several alternate methods as the one in  [http://www.linux-usb.org/SpeedTouch/ubuntu/]("http://www.linux-usb.org/SpeedTouch/ubuntu/") but the same result. I think the problem is not related to firmware as the modem syncs. Maybe Ubuntu is not recognizing the internet connection? I am only a dumb newbee. Please Help.

---

### Post by robertobaggio2k on 2005-12-24
hello i used ur howto guideline and got my modem workin..thanks alot...im only having one little problem...whenver i restart my computer i gotta repeat a couple of steps u listed on ur guidelines to get it workin again...is there a way to get it workin on bootup without me redoin everythin over? thanks alot :)

---

### Post by Maggoo on 2006-02-21
[QUOTE=rufian1]Thats is exactly my same problem. Modem seems to sync but no navigation is possible. Tried several alternate methods as the one in  [http://www.linux-usb.org/SpeedTouch/ubuntu/]("http://www.linux-usb.org/SpeedTouch/ubuntu/") but the same result. I think the problem is not related to firmware as the modem syncs. Maybe Ubuntu is not recognizing the internet connection? I am only a dumb newbee. Please Help.[/QUOTE]

This is my prob as well, every goes swimmingly, right up till I try to actually see a site.

Anyone know how to make it work yet?

Thanks

Miles

---

### Post by dvrs on 2006-02-27
Darrell,

Props for an excellent howto - it was a pleasure to go through the steps and find that everything worked as planned on Breezy without a single hitch! :D  Thanks and keep up the good work. 

dvrs.

---

### Post by yorkieboy on 2006-04-04
Hi, I'm a complete new so my knowledge of ubuntu is pretty much zero.  I have 5.10 Breezy Badger and a speedtouch 330 usb modem, and I'm experiencing exactly  the same kind of problem as gruszczy and others.  I've followed through all the steps in Darrels howto, and still no result.  Any ideas?

---

### Post by johnmccracken on 2006-05-05
me to get the following :

May  5 16:30:16 localhost kernel: [4317604.473000] usbcore: registered new drive r speedtch
May  5 16:30:16 localhost kernel: [4317604.718000] usb 1-2: found stage 1 firmwa re speedtch-1.bin.4
May  5 16:30:17 localhost kernel: [4317605.298000] usb 1-2: found stage 2 firmwa re speedtch-2.bin.4
May  5 16:30:22 localhost kernel: [4317610.005000] ADSL line is synchronising
May  5 16:30:37 localhost kernel: [4317625.005000] ADSL line is up (7456 Kib/s down | 448 Kib/s up)

---

### Post by smdahmed on 2006-05-30
I just wanted to say Thank You. I had referred a lot of other websites and forums explaining on how to connect the speedTouch usb modem in Ubuntu. But this was it... I could get my modem up and running. Now I neednt bother about viruses too... :P

thanks a lot...

---

### Post by Udidin on 2006-06-21
Hi all,

Is there any reason why this approach would not work with Dapper Drake 6.06?

I've never used linux before this week, but I'm definitely going to learn more, as long as I can get web access!

I'll be installing Ubuntu 6.06 desktop, dual boot with win xp (for now ;)  ) and I have a Speedtouch 330 USB ADSL PPP modem (yea, I know, it was free:roll:  )

Any help greatly appreciated,

Udidin.

---

### Post by Aliarse on 2007-01-23
Hey All. 
Sorry for bumping such an old thread, but im having the same problem as described in here, and im in serious need of help. I've been trying to get this modem working for about 2 weeks now, and just today I've got the furthest I've ever gotten with it, but im still having problems.

The line syncs up correctly, but when i try to browse via firefox, it cannot reach any pages.

Here's my syslog that i get when i plug the modem in..

```
Jan 23 14:50:31 ubuntu kernel: [17183748.608000] usb 2-1: new full speed USB device using ohci_hcd and address 9
Jan 23 14:50:31 ubuntu kernel: [17183748.820000] usb 2-1: configuration #1 chosen from 1 choice
Jan 23 14:50:32 ubuntu kernel: [17183749.508000] usb 2-1: reset full speed USB device using ohci_hcd and address 9
Jan 23 14:50:32 ubuntu kernel: [17183749.972000] speedtch 2-1:1.0: found stage 1 firmware speedtch-1.bin
Jan 23 14:50:33 ubuntu kernel: [17183750.212000] speedtch 2-1:1.0: found stage 2 firmware speedtch-2.bin
Jan 23 14:50:38 ubuntu kernel: [17183755.480000] ATM dev 0: ADSL line is synchronising
Jan 23 14:50:53 ubuntu kernel: [17183770.480000] ATM dev 0: ADSL line is up (2304 kb/s down | 288 kb/s up)
```


I know it would be easier to just buy a router, but funds don't allow that ATM so this is my only option so any help would be GREATLY appreciated.  ):P

---

### Post by Aliarse on 2007-01-23
Anyone?? Really want to use Ubuntu, but until i can get a net connection its practically useless to me, so getting this working would be a +...:-\"

---

### Post by terapatrick on 2007-01-23
[http://www.linux-usb.org/SpeedTouch/index.html](http://www.linux-usb.org/SpeedTouch/index.html)
Try this page worked on my PPP over ATM.
READ rest of page PPPOE

---

### Post by Aliarse on 2007-01-24
This is one of the tutorials i've followed, and it still doesnt work.. :mad:

---

### Post by Cortesio on 2007-02-03
Thanks

---

### Post by jeffef on 2008-01-21
> **camara said:**
> Angelwings: have you tried this one?
[http://s1x.homelinux.net/projects/speedtouch_suite](http://s1x.homelinux.net/projects/speedtouch_suite)
I have... and was also unlucky!... :(:(
all went well until I got an I/O error with some files (I think it were some xml files)

Good luck![http://s1x.homelinux.net/projects/speedtouch_suite](http://s1x.homelinux.net/projects/speedtouch_suite)** Link now dead!**

---

