---
title: "Trouble with Wireless."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by rokumanxes on 2008-04-28
Hello, all.

Anyway...  Let's get down to business.
I've just installed ubuntu and as of now, my only
problem is the wireless.

I apologize if that's where it belongs, but keep in
mind, I AM an ABSOLUTE BEGINNER to ubuntu.

I have a Broadcom 802.11g that came with my laptop.
I've read some methods, but they're all too confusing
for a noob such as myself.

If anyone could post some totally simple, self explained instructions, that would be GREAT.

The big problem I suppose is with the "b43-fwcutter"
When trying to install I get this dialogue.

"An errer occured
The following details are provided:
E: b43-fwcutter: subprocess post-installation script returned error exit status 1"

Thanks for any help.

---

### Post by doorknob60 on 2008-04-28
Try using ndiswrapper
```
sudo a[t-get install ndisgtk
```
and using the Windows driver for it (find the correct driver on Broadcom's site, [www.driverguide.com](www.driverguide.com) ,or Google)

---

### Post by rokumanxes on 2008-04-28
> **doorknob60 said:**
> Try using ndiswrapper
```
sudo a[t-get install ndisgtk
```
and using the Windows driver for it (find the correct driver on Broadcom's site, [www.driverguide.com](www.driverguide.com) ,or Google)

I assume I just type that into the terminal?
If so, it says "command not found"

---

### Post by bikeboy on 2008-04-28
Just a typo. It's apt-get not a[p-get.

---

### Post by rokumanxes on 2008-04-28
> **bikeboy said:**
> Just a typo. It's apt-get not a[p-get.

Thanks.

Now...

What does all this mean?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndisgtk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:011-1) ...
--13:29:43--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
rokumanxes@rokumanxes-laptop:~$

---

### Post by bikeboy on 2008-04-28
I think that means the file failed to download, which would make sense if you can't get wireless to work. Any chance you can temporarily connect using a LAN cable?

---

### Post by rokumanxes on 2008-04-28
> **bikeboy said:**
> I think that means the file failed to download, which would make sense if you can't get wireless to work. Any chance you can temporarily connect using a LAN cable?
I plugged the Ethernet cable into the port, but...
it wouldn't... connect.
I don't have a password or anything of that sort on it...
I'm not understanding ubuntu at all...
:(

---

### Post by bikeboy on 2008-04-28
Does left-clicking the network icon (towards the top right part of the screen) give you the 'wired network' option? It would normally automatically switch to wired when a cable gets plugged in, but might not have for some reason.

---

### Post by sam_delta on 2008-04-28
dont worry, i know how lost you feel typing commands and seeing lots of text on the terminal, ull lern ubuntu and get used to ubuntu withing no time, its a very powerfull OS,,,,,,,

first, you may want to try to enable  your hardware drivers by going into sytem>administrator>hardware drivers hopefully, you'll have broadcom drivers listed under hardware drivers,, if so, enable broadcom wireless drivers, , if no broadcom wireless drivers appear under hardware drivers windows then you may need to install b43-fwcutter manually, 

if you have no wired connection
follow the procedure on post # 9 on 
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)

EDIT
try enabling wired connection as bikeboy sayd, there are much easier procedures to install b43-fwcutter having a wired connection

sam

---

### Post by rokumanxes on 2008-04-28
> **bikeboy said:**
> Does left-clicking the network icon (towards the top right part of the screen) give you the 'wired network' option? It would normally automatically switch to wired when a cable gets plugged in, but might not have for some reason.
It did, but all I got in that spot was two monitors.
The icon,
and I didn't have access to the internet.
Firefox, google.
Yeah, didn't happen.

---

### Post by sam_delta on 2008-04-28
try clicking onto the monitors, and click "wired" if enabled

---

### Post by rokumanxes on 2008-04-28
> **sam_delta said:**
> try clicking onto the monitors, and click "wired" if enabled

Boy... do I ever feel silly.

Um...  I had the wrong end of the cable running to my laptop...
Oops...

Oh well, I'm on my laptop now...

Now to figure out the wireless.:lolflag:

---

### Post by sam_delta on 2008-04-28
try the following procedure to reinstall b43


make sure you have your wired connection and do this

go to a terminal and type to remove



```
sudo aptitude purge b43-fwcutter
```

update your repos with


```
sudo aptitude update
```

to reinstall type

```
sudo aptitude install b43-fwcutter
```

itll ask you if you want to fetch some firmware, make sure you answer "Y" for yes

then restart pc, goto system>.administrator>hardware drivers drivers, and activate broadcom driver


tell us how it goes

sam

---

### Post by starryeyedboy on 2008-04-28
hey. i use a broadcom wireless card too.

before u use b43 - we might wanna check what exactly is ur wireless card.. try typing this into your terminal:

> lspci -v

this will list all ur hardware stuff. look for your broadcom card info. mine look like this:

> 03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
	Subsystem: Broadcom Corporation Unknown device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d0200000 (64-bit, non-prefetchable) [size=16K]
	Memory at d0000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>


now, could u do that, n post the info? if u are using a bcm4328 like me, its better to use ndiswrapper. otherwise, its better to use b43.

also, since u have net now, if u need immediate help, u might wanna visit the #ubuntu chat on irc. just use add/remove to install "xchat" 

if u are going to use ndiswrapper, please refer to these instructions:
> [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html](http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html)

but make sure u remove previous versions of ndiswrapper! to do this, go to system>administration>synaptic package manager then search for ndiswrapper, n remove everything. alternatively, if u wish to do it manually, refer to this post:

> [http://ubuntuforums.org/showthread.php?t=507378](http://ubuntuforums.org/showthread.php?t=507378)

and now if ur gonna use b43... i don't know how =D so check out the #ubuntu chat for that. lots of ppl use b43. here's the b43 info website:

> [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43)


cheers mate.

---

### Post by rokumanxes on 2008-04-28
> **sam_delta said:**
> try the following procedure to reinstall b43


make sure you have your wired connection and do this

go to a terminal and type to remove



```
sudo aptitude purge b43-fwcutter
```

update your repos with


```
sudo aptitude update
```

to reinstall type

```
sudo aptitude install b43-fwcutter
```

itll ask you if you want to fetch some firmware, make sure you answer "Y" for yes

then restart pc, goto system>.administrator>hardware drivers drivers, and activate broadcom driver


tell us how it goes

sam

That worked wonders.

I really appreciate it.
To all of you.

---

### Post by sam_delta on 2008-04-28
> **rokumanxes said:**
> That worked wonders.

I really appreciate it.
To all of you.

glad it worked :)

now... enjoy ubuntu :p!!!!

---

