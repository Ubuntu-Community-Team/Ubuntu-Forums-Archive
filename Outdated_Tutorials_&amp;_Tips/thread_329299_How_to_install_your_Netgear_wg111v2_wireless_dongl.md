---
title: "How to install your Netgear wg111v2 wireless dongle on Edgy"
date: 2007-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by phossal on 2007-01-01
Install your Netgear wg111v2 using ndiswrapper. Some have reported success using the existing rtl8187 driver, but I recommend against it. Your first task is to confirm which hardware you're actually using. **Ubuntu Forum member, kvonb, figured out that some of the wg111v2's actually use the wg111v1 chipset - they're essentially mislabeled.** His recommendation for discovering which hardware you're using requires that you plug it in, and run: (*The light on your hardware may or may not work. Disregard it.)
```
lsusb | grep NetGear
```The output will show one of two devices: 0846:4240 is the v2. If you're using v1, you can follow the same steps, but the driver you install will be different. 



[COLOR="SlateGray"]**STEP: **[/COLOR]Blacklist the existing drivers:
```
sudo gedit /etc/modprobe.d/blacklist
```
Copy and paste the following to the bottom of the file. Save it. Close it.
```
#wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b
blacklist r8187
```


[COLOR="SlateGray"]**STEP: **[/COLOR]Download the driver from [Netgear]("http://kbserver.netgear.com/release_notes/D102843.asp")
Select version 1.3 (if you're using v2). Download wg111v2_1_3_0.zip to your desktop. Right-click on the file and extract it to your desktop. For ease of use, rename the extracted folder to: "NetgearV2".


[COLOR="SlateGray"]**STEP: **[/COLOR]Configure NDISWRAPPER. Replace <username> with yours. Edit path as necessary. One command at a time.
```
sudo ndiswrapper -i /home/<username>/Desktop/NetgearV2/Driver/WIN98/net111v2.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Add the module to /etc/modules
```
sudo gedit /etc/modules
```
Copy and paste the following to the bottom of the file. Save it. Close it.
```
ndiswrapper
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Reboot your machine. Insert your wg111v2. Confirm proper installation:
```
ndiswrapper -l
```
The output should show:
[I]Installed drivers:
net111v2 driver installed, hardware present[/I]

---

### Post by phossal on 2007-01-01
Removed

---

### Post by kvonb on 2007-01-02
-

---

### Post by phossal on 2007-01-02
[Removed]

---

### Post by kvonb on 2007-01-02
-

---

### Post by phossal on 2007-01-02
[Removed]

---

### Post by rbhigday on 2007-01-04
> **phossal said:**
> Do not immediately insert the wg111v2. Avoid the gui configuration tools. Disable wep/wpa on your router. The wg111v2 is "supported out of the box" using the r*818* driver, meaning it does not require the ndiswrapper. Ignore that. Devices beginning with serial numbers like 1AC* (wg111v2) use the ndiswrapper.

**[COLOR="#536d8c"]NOTES: [/COLOR]**
The light on my wg111v2 dongle blinks at lengthy intervals. The light activity is not a good reference point for connectivity or operation. Ignore it.
I successfully installed both versions of the Netgear wg111 (wg111, wg111v2) on 32bit Ubuntu. *There is a reported incompatibility with 64bit Ubuntu*.
I installed **all** of the drivers for both versions (wg111, wg111v2) in ndiswrapper to test which work, and which do not. Each version works with all of its respective drivers.
"wlan0" should be replaced with the appropriate interface (wlan1, eth0, eth1, etc) in the tutorial below. When I install both wg111, and wg111v2 they appear as wlan0 and wlan1 for me.

**[COLOR="#536d8c"]DEVICES: [/COLOR]**
0846:4240 - You may have success with version 1 driver (Note kvonb's experience above)
0846:6a00 - You may have success with version 2 driver


.
**[COLOR="#536d8c"]1. [/COLOR]**Install ndiswrapper, specifically ndiswrapper-utils-1.8
```

sudo apt-get install ndiswrapper-utils-1.8

```




**[COLOR="#536d8c"]2. [/COLOR]** Blacklist existing drivers.*
```

sudo gedit /etc/modprobe.d/blacklist

```

Copy and paste the following to the bottom of the file. Save it. Close it.
```

#wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b

```

NOTE: I have used both versions of the wg111. I found that both dongles (wg111, wg111v2) were recognized "out of the box" using the r*818* drivers, but would not associate with the router.  Blacklist them, download the appropriate version driver from Netgear, and use ndiswrapper.




**[COLOR="#536d8c"]3. [/COLOR]** Visit Netgear to download your driver at:  [http://kbserver.netgear.com/release_notes/D102843.asp](http://kbserver.netgear.com/release_notes/D102843.asp)

Select version 1.3. Download wg111v2_1_3_0.zip to your desktop. Right-click on the file, and extract the compressed folder to your desktop. For ease of use, rename the extracted file "NetgearV2". 




**[COLOR="#536d8c"]4. [/COLOR]** Configure ndiswrapper. Replace <username> with yours. Edit path as necessary. One command at a time.
```

sudo ndiswrapper -i /home/<username>/Desktop/NetgearV2/Driver/WIN98/net111v2.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```




**[COLOR="#536d8c"]5. [/COLOR]** Add the module to /etc/modules. 
```

sudo gedit /etc/modules

```

Copy and paste the following to the bottom of the file. Save it. Close it.
```

ndiswrapper

```




**[COLOR="#536d8c"]6. [/COLOR]** Reboot your machine.

**[COLOR="#536d8c"]7. [/COLOR]** Insert your wg111v2.

**[COLOR="#536d8c"]8. [/COLOR]** Confirm proper ndiswrapper installation.
```

sudo ndiswrapper -l 

```

The output should show: (If it doesn't. Do not continue. Seek help.)

Installed drivers:
net111v2 driver installed, hardware present




I hit the wall here because I get

Installed drivers:
net111v2 driver installed

> To find out if you have these odd v1 modules:

Code:

lsusb | grep NetGear

should show:

Code:

Bus 00x Device 00x: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)


If you get this do you have v1 or v2?
The important part is the 0846:4240, forget the rest!

---

### Post by kvonb on 2007-01-04
-

---

### Post by Jose Catre-Vandis on 2007-01-04
"but would not associate with the router"

Beg to differ with you on this. The adapter links perfectly with my router (Netgear as well) "out of the box" using the driver built into the kernel, so there is no need for ndiswrapper, and it is worth trying this way first. You do need to sort out your interfaces file and include the ESSID for your LAN wireless network, and accept that you won't get any flashing lights on your adapter.

It is worth blacklisting the following
```
blacklist bcm43xx
blacklist islsm
blacklist islsm_usb
blacklist islsm_pci
blacklist prism2_usb
```

and set up your interfaces file as follows:

```
sudo gedit /etc/network/interfaces
```
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid *youressid*
wireless-mode managed
```

Which assumes you have dhcp running, but it works just as well with a static IP

---

### Post by rbhigday on 2007-01-04
ok I did it!!!!!!!!!!!!!!!
not bad for a newbie :), well at least I think so reading all the horror stories about wireless!!

Now a question how do I install my wep back on? I can not do wpa as the wife laptop is not that advance yet.

---

### Post by phossal on 2007-01-05
Removed

---

### Post by phossal on 2007-01-05
[Removed]

---

### Post by phossal on 2007-01-05
[Removed]

---

### Post by kvonb on 2007-01-06
-

---

### Post by exc220 on 2007-01-08
Hi everyone!
I followed you're guide (with ndiswrapper) and it seems to work fine even with the light!
However I have encountered a problem. When I start my PC with the WG111v2 plugged in it all doesn't work, it seems like it loads the rtl8187 driver, even though I added them in the blacklist, and from the logs it seems like it endlessly scans for the AP on all the channels! However when I start my PC with the usb dongle unplugged and I plug it in after ubuntu has completed the startup it work flawlessly??!?!:confused: 
Any help on this?

Ciao!

---

### Post by phossal on 2007-01-08
Removed

---

### Post by Rotarychainsaw on 2007-01-19
Thanks I just got mine working too. Very good write up. I was also curious about the whole 'using the old driver if it is plugged in on boot' thing too. It seems we only have to wait to sign in before we plug in the dongle and everything will be OK, right? Also, my system locked up like it was using the old driver, even though I had been browsing the web for a little while, Is that common? It may have been a fluke....

---

### Post by phossal on 2007-01-19
Removed

---

### Post by Rotarychainsaw on 2007-01-19
I'm using the network manager applet to control all of the connecting. I'll explain the locking up... Out of the box I could plug in the wg111 and it would be seen but as soon as I tryed to connect to a router with it my whole system would lock up. Mouse wouldn't move, couldn't get into a tty etc. This happened once so far after switching to ndiswrapper. It hasn't happened again, but I've only been using this for about an hour. 
Either way, it seems to be working well enough right now, so thanks.

edit: 2 times now haha, but I was on myspace both times. Evil site.

edit: 3 times now. I'm gonna see if its the net applet messing up or something.

---

### Post by phossal on 2007-01-19
Removed

---

### Post by Rotarychainsaw on 2007-01-19
Yeah, but I used an ethernet cable for a long time with no crashes. It only happens with the wireless. I turned off beryl and it seems to be working a little better now. I will continue to investigate.

---

### Post by phossal on 2007-01-19
Removed

---

### Post by Rotarychainsaw on 2007-01-19
I believe it's version 2 - 0846:6a00 -. not sure on chipset or anything. I tryed using the dongle before I knew what ndiswrapper was and it would just lock my computer up. I'm using edgy on a 32 bit computer. Right now it's working pretty good. I think maybe beryl was straining the computer or something, it is really old.

---

### Post by phossal on 2007-01-19
Glad you're up and running! :D

---

### Post by exc220 on 2007-01-22
> **Rotarychainsaw said:**
> Thanks I just got mine working too. Very good write up. I was also curious about the whole 'using the old driver if it is plugged in on boot' thing too. It seems we only have to wait to sign in before we plug in the dongle and everything will be OK, right? Also, my system locked up like it was using the old driver, even though I had been browsing the web for a little while, Is that common? It may have been a fluke....

I have moved on to Edgy and now I don't have wait for Ubuntu to boot to plug in the usb dongle! It works flawlessly!

---

### Post by phossal on 2007-01-24
Removed

---

### Post by phossal on 2007-01-30
Removed

---

### Post by phossal on 2007-02-16
Removed

---

### Post by thorsten.rehm on 2007-02-16
I have lately started my WG111v1 under Ubuntu Edgy using this [doc]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29") and this [driver]("http://kbserver.netgear.com/release_notes/d102869.asp").
Everything works.

---

### Post by phossal on 2007-02-16
Removed

---

### Post by finferflu on 2007-02-16
> **phossal said:**
> The recent headers update destroyed my wireless installation. I installed the updates, restarted, and I could not get wlan0 to be recognized. I reinstalled from an older 6.10 disk that I had and used this tutorial to get back up and running. I've avoided updating the headers since. I haven't had time to try to diagnose the problem. If you have info, please update the thread.

You can choose which kernel you want to run at boot time (If you press ESC while GRUB is loading). I don't know how poor is my language, but I think you get the point.

---

### Post by Micronaut on 2007-02-17
I have spent 8 hours per day, for the past 7 days attempting to install a wg111v2 onto Ubuntu 6.10 with no success.   Ubuntu need to clean this up if they ever hope to compete with Microsoft for a desktop operating system :(

---

### Post by phossal on 2007-02-17
Removed

---

### Post by kvonb on 2007-02-17
-

---

### Post by Debord on 2007-02-17
First, I will thanks for this guide. After many hours strugling to get my wirless usb up its know up and running! I am so greatfull!

For those who have problem to get the dongle to function on startup of your ubuntu system (I am on debian etch, sorry) edit /etc/wlan/wlan.conf (think it has to do with wireless-tools, installed for the proper wireless pci card and so on) and uncheck every thing that is enebled (with `#´in front of the line). That fixed my problem on startup and know everything is function exeptept the lite on the usb dongle.

(excuse my bad english)

---

### Post by daveb1 on 2007-02-18
Hi All

First post, so hello all.  

> **phossal said:**
> 

**[COLOR="#536d8c"]3. [/COLOR]** Visit Netgear to download your driver at:  [http://kbserver.netgear.com/release_notes/D102843.asp](http://kbserver.netgear.com/release_notes/D102843.asp)* 
[COLOR="DimGray"][SIZE="1"]*If you're using the version 1 chip, this isn't the driver for you. Use the v1 driver.[/SIZE][/COLOR]


Can I make a suggestion at this point to refer people to post 5 of the thread where kvonb mentions his v2 dongle is actually a v1. As a complete noob, I followed the instructions exactly, my dongle says WG111V2, so I carried on as though the instructions were correct for my hardware, not realising that if I did "lsusb | grep NetGear" I'd find out it was a v1 inside, and that the remaining instructions were slightly wrong.

I got as far as point 8, then found out the hardware wasn't present. Kvonb helpfully mentions > without the "hardware present", then you have the wrong driver, so download and install the v1 drivers and just remove the v2 drivers.The download and install bit is fine, but how do I remove the V2 drivers?

I've tried going back to point 4 and substituting the V1 inf files (there's 2 in the zip file) in the first line, but they don't work.

Any help appreciated.

Dave

ubunto 6.10
P4 3Gig, 1024 Meg RAM, WG111V1 (although it says WG11V2 on the side)

---

### Post by phossal on 2007-02-18
Removed

---

### Post by Fitzy_oz on 2007-03-08
Thanks to everyone who contributed on this thread, especially phossal and kvonb.  My wireless dongle worked without issue following the guide and information here.

Thanks Heaps Guys :)

---

### Post by phossal on 2007-03-10
kvonb,

I got [this post]("http://phossal.com/thread?view=702216933") recently:

> oli commented on 2007-03-09 at 07:11:01

Thanx for HowTo, unfortunately it doesnt work for me. Got this error in step5;

oli@unknown:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/**2.6.17-10-generic/kernel/drivers**/net/ndiswrapper/ndiswrapper.ko): Invalid argument

im using this card;
oli@unknown:~$ lsusb | grep NetGear
Bus 005 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)


Any idea what's happening?

---

### Post by kvonb on 2007-03-11
-

---

### Post by phossal on 2007-03-11
What?! :shock: You bailed on the W-G? Wow! Next you'll be filing for lateral transfer to another forum. I have to say it's a shock. I'm still using ndiswrapper, although on 32bit Ubuntu, using the v2 - having lent away the v1 - and all works very, very well. I had hoped to help the guy out, but I haven't gotten such an error since - only after an update last month. 

Bit the bullet and ran cables. That's quite a change. Well, now you'll just be able to post helpful advice much, much faster. What are broadbands speeds like on your side of the planet?

---

### Post by kvonb on 2007-03-11
-

---

### Post by Genecks on 2007-03-18
56k modems scare me. I don't want to relive that part of the 1990s. :( 

**Other than that**, as I read this guide, I notice there are two conflicting guides:

One guide is from the original thread creator, and yet some comments are from kvonb.

Which set of directions do I follow for wg111v2? 

kvonb's comments mixed me up, and now I'm unsure of which directions to follow.

Are the directions on the website, which is located in the first post, all I need to set up wg111v2? Or are there some mistakes in that guide? I didn't see any timestamp update, so I keep thinking the guide was never edited.

---

### Post by phossal on 2007-03-18
I created the guide. Kvonb's first response to me helped me fix a few details, and then he posted later confirming the status of the two chip sets. 

The guide at the site [http://phossal.com](http://phossal.com) is the one I consider accurate, as it's the one I use each time I have to reinstall Ubuntu after screwing it up helping someone solve some other problem. ;)

---

### Post by finferflu on 2007-03-27
Come on! what's the point of deleting the tutorial from this forum, just to have it on some other website??? Now that website is down, and I needed that tutorial. I am amazed. I think some stuff should always be on the Ubuntu website in order to be easily reached.

---

### Post by Jose Catre-Vandis on 2007-03-27
> **finferflu said:**
> Come on! what's the point of deleting the tutorial from this forum, just to have it on some other website??? Now that website is down, and I needed that tutorial. I am amazed. I think some stuff should always be on the Ubuntu website in order to be easily reached.

Check the 2nd or 3rd post in the thread, phossal's orginal tut is there inside quotes

but, try to use the built in drivers first before turning to ndiswrapper

---

### Post by finferflu on 2007-03-27
Ah, thanks, I found another working tutorial in the wiki fortunately :)

I already tried the built in drivers, but the light on the dongle was not blinking. I already knew that I needed ndiswrapper, I only needed this tutorial again, because I've just done a fresh install.

Thanks :)

---

### Post by Jose Catre-Vandis on 2007-03-27
The "blinking" light does give comfort, but I had to hide it out of sight after about 10 minutes when in Dapper. With Edgy, no "blinkin" light. but it works just the same, and I can look at the adapter :-)

---

### Post by finferflu on 2007-03-28
LOL!
That's very weird anyways, mine didn't give any life sign...

---

### Post by phossal on 2007-03-28
I don't know everything there is to know about the hardware. I'd be curious to understand more about how the light is powered. While the light was never a reliable source when first configuring the hardware, after a week or two of running non-stop, it came on and stayed on. 

Strange behavior. Maybe it needs a charge?

---

### Post by phossal on 2007-03-28
> **Jose Catre-Vandis said:**
> but, try to use the built in drivers first before turning to ndiswrapper

I have both versions of the dongle. Neither of mine work with the "built-in" experimental Realtek drivers. I've always had luck using ndiswrapper. The "built-in" driver coughs up an error when using iwconfig. It won't allow me to set the essid; frequency error.

---

### Post by dwightf on 2007-03-30
I have to thank you guys for this. I had been struggling with getting my dongle working. Now it works, thanks to getting the right driver for v1 in. Crazy, I thought like everyone else I had v2. Oh well. Also, as soon as I got the thing recognized, the light's been on. go figure.

Keep up the good work.

---

### Post by rjfioravanti on 2007-04-06
I went to the site to download that driver, wg111v2 1.3, but when I unzipped it I do not find any .inf files.  Only a bunch of exe files and msi files.  have they changed their download so that those files are now embedded in other files?  What should I do


The built in experimental driver seems to work for me... however the computer often just freezes up. I seem to be able to reproduce the freeze quite reliably by checking my hotmail account, it freezes during sign-in or sometimes when I am closing the window. 

I figured if I use ndiswrapper I may get rid of this problem.  Do you think I am barking up the right tree?

---

### Post by userundefine on 2007-04-06
Just wanted to say thanks.  This tut worked for me without fault !

---

### Post by phossal on 2007-04-06
> **rjfioravanti said:**
> I went to the site to download that driver, wg111v2 1.3, but when I unzipped it I do not find any .inf files.  Only a bunch of exe files and msi files.  have they changed their download so that those files are now embedded in other files? 

To confirm that the download is still working properly, I visited the site and downloaded it myself:
[http://kbserver.netgear.com/release_notes/D102843.asp](http://kbserver.netgear.com/release_notes/D102843.asp)

The instructions on the page indicate that you should right-click and download. Then, you'll find the driver in a path something like this ~Desktop/wg111v2_1_3_0/Driver/WIN98. If you're having luck using the Realtek drivers (the built-in, experimental) drivers, you might have a v1. I have always used ndiswrapper.

---

### Post by rjfioravanti on 2007-04-07
Somehow I was just downloading the wrong file.. but I got the right wg111v2 file eventually and installed with ndiswrapper

doing so stopped the freezing on my computer i was describing

---

### Post by phossal on 2007-04-13
Repaired the thread.

---

### Post by kvonb on 2007-04-13
-

---

### Post by phossal on 2007-04-13
What? What? What? :shock: No way to get them working?

---

### Post by kvonb on 2007-04-13
-

---

### Post by kvonb on 2007-04-14
-

---

### Post by phossal on 2007-04-14
I'm still shocked by how poorly this device was supported given that it's one of the most widely available devices. You can *still* walk into any Best Buy in the States and find it among the 10 or so total Wireless USB Adapters they offer. I have to believe an overwhelming majority are used with Windows, obviously, but, for all of those people who are now giving Ubuntu a try, this tutorial may pick up steam rather than lose it. ***[COLOR="SlateGray"]The device is not only still available, it's only $39.00 or so. And it works.[/COLOR]*** Since I got mine working, I haven't had any major problems to report.

A geek or two tried to dissuade me from putting much effort into it. They even explained how demand for their devices was so much greater - yet I had never heard of them. Best Buy sells a lot of crap. ***[COLOR="SlateGray"]I love Ubuntu, but I want all its advantages and the ease of buying junk off the shelves at my local computer super mart.[/COLOR]***

I'm not sure this tutorial will still work with the next 'Buntu, but we'll figure out what *does* work. By the way, ***[COLOR="SlateGray"]I'm not at all excited about the next release. I'll be one of those guys running Edgy with Java 50 when all the noobs are trying to figure out how to install Java 6 on Ubuntu Zesty using the package manager.[/COLOR]***

---

### Post by kvonb on 2007-04-14
-

---

### Post by phossal on 2007-04-17
Kvonb, I need help with installing a link via update-alternatives on dapper. Is the syntax the same as on Edgy? I'm getting a question from a user regarding installing Java (see my sig), but he's having trouble getting update-alternatives to install his link. 

I use the form: (which is not working for him, for some reason)
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 300
```

Any ideas? It would be awesome if you dropped in and solved the guy's problems (as is your style ;) )

---

### Post by Alfdog on 2007-04-23
Great guide, I got this working in my feisty install.  Is there any way to get WPA working? Maybe a different driver?

---

### Post by phossal on 2007-04-25
The data sheet for the wg111 indicates that WPA is not supported (it clearly states that WEP *is*). My guess is that the same is true for the v2, but the data sheet is not quite as easy to find. If I'm guessing correctly, you won't find a driver to support it.

---

### Post by Alfdog on 2007-04-25
Huh, I was using it with wpa on Vista, maybe they were using some sort of 3rd party app to make it work.  I guess if I really want WPA, I'll just get a different unit off of Newegg.

---

### Post by exc220 on 2007-04-26
hi everyone!
Can i apply this guide to Feisty? I tried last night following every step of the guide that previously worked on my 6.10, but it didn't work...:(  Has anyone tried it on feisty?

---

### Post by phossal on 2007-04-26
I've been told it works, but I haven't installed Feisty yet. I downloaded it today, and I'll install it on a spare drive in the next day or two. I'll post back if you haven't posted success before then.

---

### Post by kvonb on 2007-04-27
-

---

### Post by kvonb on 2007-04-27
-

---

### Post by exc220 on 2007-04-27
update on my experience with feisty:

- my WG111v2 is recognized and can connect to my access point through gnome network manager which is very nice because it tells you info on the signal quality :) so I can properly go on the WWW and download files w/o issues
- HOWEVER....whenever i open aMule or uTorrent it disconnects from my AP and I can't go on the WWW anymore, at that point I have to unplug the pen and plug it back in and I can surf the web

It seems like the pen isn't fully supported yet, so maybe when it does certain operations required by aMule, uTorrent it panics and just turns off...

that's my experience...I guess I'm just gonna have try it through ndiswrapper even though i was lovin the network manager :)

---

### Post by rjfioravanti on 2007-04-27
has anybody tried feisty with ndiswrapper

I am having trouble setting it up... worked fine for me on edgy, trying on fresh install with feisty now

---

### Post by phossal on 2007-04-27
I can't even get Feisty to install. lol

---

### Post by rjfioravanti on 2007-04-27
why not

I am curious why did you use the WIN98 driver in the tutorial?

---

### Post by rjfioravanti on 2007-04-27
So I gave the WIN98 driver a quick try, but gave up on that quickly and tried the WINXP one in more detail following this tutorial

ndiswrapper seems to get installed ok, and I can associate with the network essid

but I can't seem to bind via dhcp when I do   sudo dhclient


If I try using static connection it seems to configure ok but then I just can't ping anything

does anyone have any other ideas for what I should try? I can give other info if requested

---

### Post by phossal on 2007-04-27
> **rjfioravanti said:**
> I am curious why did you use the WIN98 driver in the tutorial?

It's the one I had success getting a lease with.

---

### Post by rjfioravanti on 2007-04-27
update, I got it to work with WIN98 driver

Maybe I just missed a step the first time around

So I confirmed working with Feisty and ndiswrapper and WIN98 driver

i will post back if I run into problems

---

### Post by phossal on 2007-04-27
I still can't get feisty to install, because I can't get my screen resolution to work. lol Granted, I didn't try very hard.

---

### Post by kvonb on 2007-04-28
-

---

### Post by linuxusa on 2007-04-30
The good... 
I had this device working perfectly in edgy eft, with ndiswrapper, as the howto stated.


The bad... 
I have recently upgraded to Feisty Fawn 7.04, the netgear wg111v2 no longer works . I have tried Windows98 and XP driver. The system only sees a "usb storage device" when using ndiswrapper. 

After many hours of playing around, I have resorted to long wires instead of this device that used to work.



The interesting...
However, the built in driver (rtl8187) seems a little more promising.

After booting into Feisty fawn (even on the live disk) The dongle seems to "almost" work with the rtl8187 driver.
The system is able to see wifi networks, but it wont bind to any. Also the light doesn't light up.

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     Scan completed :
          Cell 01 - Address: 00:14:95:15:A0:E1
                    ESSID:"2WIRE388"
                    Mode:Master
                    Frequency:2.437 GHz
                    Quality=53/64  Signal level=21/65
                    Encryption key:on
                    Extra:tsf=0000002f1cbba8f6
          Cell 02 - Address: 00:18:F8:40:34:47
                    ESSID:"yellowRose"
                    Mode:Master
                    Frequency:2.437 GHz
                    Quality=3/64  Signal level=38/65
                    Encryption key:on
                    Extra:tsf=000000015b143563

Device:
Bus 003 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

----------------------------------

---

### Post by misty soul on 2007-04-30
I got a similar problem as everyone here : my WG111V2 stopped working after  the update to Feisty Fawn.

I finally got it working a few minutes ago :)

Looking in the supported cards page in the ndiswrapper site at sourceforge, I found a reference to another W98 driver from realtek (not from NetGear). I found the driver here: [http://download.opendrivers.com/uploaddrv/network/realtek/rtlsetup-8187(1221)(0412).zip]("http://download.opendrivers.com/uploaddrv/network/realtek/rtlsetup-8187(1221)(0412).zip") Note that the round parentheses are really in the file name. I unzipped the file and located the W98 driver path in the directories tree: RTL8187/WIN98/Netrtuw.inf.

Looking at my /etc/ndiswrapper directory, I saw my current driver directory was called net111v2, so I removed it using the ndiswrapper "-r" flag and installed the new driver:
```
ndiswrapper -r net111v2
ndiswrapper -i /my/download/path/RTL8187/WIN98/Netrtuw.inf
```

"ndiswrapper -l" showed me the netrtuw driver was installed and the hardware was present.

I unplugged and plugged again the USB dongle and looked at the bottom of the /var/log/messages file for the last messages. I saw a message from ndiswrapper about the netrtuw driver with its complete version number and saw two messages related to mywlan0 device that looked promising.

I finally switched from my current ethernet network to wireless using the NetworkManager applet. Since my access point uses WPA/PSK, I had to enter the passphrase in a popup and the network was up and running.

Well, since I did not use gnome key management before and the applet needed to store the WPA/PSK key, I was prompted for a passphrase for the keystore just after having entered the WPA/PSK key, beware not to mix eveything there! You may choose not to use the networkManager applet and configure your wireless key entirely from /etc/network/interface if you prefer.

Now I am wireless again and secure (yes, WG111V2 does support WPA/PSK).

---

### Post by phossal on 2007-04-30
What device do you actually have? Are you sure it's a V2?

---

### Post by linuxusa on 2007-04-30
> **misty soul said:**
> I got a similar problem as everyone here : my WG111V2 stopped working after  the update to Feisty Fawn.

I finally got it working a few minutes ago :)

Looking in the supported cards page in the ndiswrapper site at sourceforge, I found a reference to another W98 driver from realtek (not from NetGear). I found the driver here: [http://download.opendrivers.com/uploaddrv/network/realtek/rtlsetup-8187(1221)(0412).zip]("http://download.opendrivers.com/uploaddrv/network/realtek/rtlsetup-8187(1221)(0412).zip") 


Thanks for the insight, unfortunately, it did not work for me. All I see from ndiswrapper activity is:
mike@mike-desktop:/etc/modprobe.d$ sudo ndiswrapper -l
Installed drivers:
netrtuw         driver installed, hardware present

From /var/log/messages :
Apr 30 22:34:16 mike-desktop kernel: [ 1722.636799] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Apr 30 22:34:16 mike-desktop kernel: [ 1722.639300] usbcore: registered new interface driver ndiswrapper
Apr 30 22:34:31 mike-desktop kernel: [ 1737.113212] usb 3-6: new high speed USB device using ehci_hcd and address 6
Apr 30 22:34:31 mike-desktop kernel: [ 1737.250180] usb 3-6: configuration #1 chosen from 1 choice

---

### Post by misty soul on 2007-05-01
> **phossal said:**
> What device do you actually have? Are you sure it's a V2?

I think so, because it used to work with Edgy and the V2 drivers from NetGear (I don't remember if it was the driver from the CD or an update from their site), using WPA/PSK. It only stopped working when I switched to Feisty. My device ID is 0846:6a00 rather than  0846:4240, I understood this was also a v2, am I wrong ?

Everything was fine tonight when I posted my small contribution, but I was not able to restart it this morning :confused: . I had to go back to ethernet and am trying to understand what happens.

I am currently trying to understand the traces in /var/log/syslog (or /var/log/daemon, they are similar). NetworkManager forwards about 500 messages from wpa_supplicant. It seems to start well and then to change back and forth between 4WAY_HANDSHAKE and GROUP_HANDSHAKE states, then it blacklists my access point (Added BSSID 00:0f:b5:d9:ad:20 into blacklist) and tries again AP scan during one minute. However, since it has blacklisted my AP at this time, the following trials just fail. It gives up after one minute.

I think I will try without encryption as for now it is wpa-supplicant that seems to fail for me.

Here is an excerpt of my /var/log/syslog file during an attempt to switch to wireless.

```

May  1 11:01:41 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Setting scan request: 0 sec 0 usec 
May  1 11:01:41 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: DISCONNECTED -> SCANNING 
May  1 11:01:41 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Starting AP scan (broadcast SSID) 
 ... snip ...
May  1 11:01:41 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: SCANNING -> ASSOCIATING 
 ...snip ...
May  1 11:01:42 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: ASSOCIATING -> ASSOCIATED 
 ... snip ...
May  1 11:01:42 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: ASSOCIATED -> 4WAY_HANDSHAKE 
 ... snip ...
May  1 11:01:42 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE 
 ... snip ...
May  1 11:01:44 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE 
 ... snip ...
May  1 11:01:46 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE 
 ... snip ...
May  1 11:01:46 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE 
 ... snip ...
May  1 11:01:46 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE 
 ... snip ...
May  1 11:01:48 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE 
 ... snip ...
May  1 11:01:48 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE 
 ... snip ...
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Wireless event: cmd=0x8b15 len=20 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Wireless event: new AP: 00:00:00:00:00:00 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Setting scan request: 0 sec 100000 usec 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Added BSSID 00:0f:b5:d9:ad:20 into blacklist 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 33 37 34 2d 37 00 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
May  1 11:01:50 localhost NetworkManager: <information>^Iwpa_supplicant(26373): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
May  1 11:01:51 localhost upsmon[6158]: Poll UPS [ellipse500@localhost] failed - Driver not connected
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): pa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: GROUP_HANDSHAKE -> DISCONNECTED 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): WEXT: Operstate: linkmode=-1, operstate=5 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): EAPOL: External notification - portEnabled=0 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): EAPOL: SUPP_PAE entering state DISCONNECTED 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): EAPOL: SUPP_BE entering state INITIALIZE 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): EAPOL: External notification - portValid=0 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): EAPOL: External notification - EAP success=0 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: DISCONNECTED -> SCANNING 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Starting AP scan (broadcast SSID) 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Authentication with 00:00:00:00:00:00 timed out. 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 33 37 34 2d 37 00 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Added BSSID 00:00:00:00:00:00 into blacklist 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: SCANNING -> DISCONNECTED 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
May  1 11:01:52 localhost NetworkManager: <information>^Iwpa_supplicant(26373): WEXT: Operstate: linkmode=-1, operstate=5 
May  1 11:01:58 localhost NetworkManager: <information>^Iwlan0: link timed out. 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373):  
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): EAPOL: External notification - portEnabled=0 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): EAPOL: External notification - portValid=0 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Setting scan request: 0 sec 0 usec 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): State: DISCONNECTED -> SCANNING 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Starting AP scan (broadcast SSID) 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Scan timeout - try to get results 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Scan results: -1 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Failed to get scan results 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Failed to get scan results - try scanning again 
May  1 11:02:00 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Setting scan request: 0 sec 0 usec 
   ... snip ...
May  1 11:02:32 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Starting AP scan (broadcast SSID) 
May  1 11:02:32 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Scan timeout - try to get results 
May  1 11:02:32 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Scan results: -1 
May  1 11:02:32 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Failed to get scan results 
May  1 11:02:32 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Failed to get scan results - try scanning again 
May  1 11:02:32 localhost NetworkManager: <information>^Iwpa_supplicant(26373): Setting scan request: 1 sec 0 usec 
May  1 11:02:41 localhost NetworkManager: <information>^IActivation (wlan0/wireless): association took too long (>60s), failing activation. 

```

---

### Post by phossal on 2007-05-01
I just installed Feisty this morning. I installed build-essential using apt-get, and then ndiswrapper from source. It's version 1.43, or greater. One thing I notice right off, is that blacklisting the drivers doesn't work. If you use *ndiswrapper -l*, it will still show (rtl8187 alternative driver) unless you manually remove them. 

I did this:

```
#!/bin/bash
echo "Removing rtl8187..."
sudo rm -r /usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187
sudo rm -r /usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Kconfig
sudo rm -r /usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Makefile
sudo rm -r /usr/src/linux-headers-2.6.20-15-generic/include/config/rtl8187.h
sudo rm -r /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187
sudo rm -r /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko
```

Then I installed the driver as I would using the Edgy tutorial.

---

### Post by misty soul on 2007-05-01
I also got the message displaying  "(rtl8187 alternative driver)", so I completely removed the files as suggested and recompiled ndiswrapper 1.43 from source. The message disappeared, but my device still doesn't work :(

I turned off encryption, to no avail.

I tried several drivers (realtek, NetGear 1.3.0, NetGear 2.0.1 beta), none worked.

I am sure it worked last night with some configuration. I think I have screwed things a lot now, so I need to first understand all the errors I did and then do some cleanup. Unfortunately, I have no time for now, so I go back to wire and will try again later.

Thanks for your help.

---

### Post by phossal on 2007-05-01
I suspect the 'Buntu developers will have to clean up their mess - they've apparently screwed ndiswrapper - or the ndiswrapper gang will have to catch up. I suspect the latter, because the former can't do anything right, really. Screw free CD's. This is redhat repainted.

---

### Post by FritzBrown on 2007-06-11
This helped tremendously!:D  I followed the procedures (except: substitute *vi* for *gedit*, and a different path for the .inf file), and got my troublesome WG111v2 (not really) runing on xubuntu 6.06.1 Dapper!  Huzzah!:o

---

### Post by smoocat on 2007-07-07
Hi. Relative newbie here. I too have been trying to get my WG111v2 to work properly under Kubuntu Feisty.

The native RTL8187 driver worked fairly well for me at the beginning, despite the light on my dongle not lighting up. My main issue was that it would sporadically drop the connection, forcing me to reestablish the connection or unplug/replug the dongle. (I checked to make sure it wasn't an ISP issue, as the PC connected directly to the DSL modem works perfectly fine. This problem also didn't occur under XP.)

I decided to try out the ndiswrapper approach to see if it would resolve the issue. I tried the XP, which ended up not working. Then I tried both the Win98 and ME drivers from my Netgear cdrom, which showed up with the "device present" message. The lights began blinking (yay!), but the KNetworkManager status bar never moved past "configuring device" status (around 20%), and never reached connectivity. Now I'm left with no choice but to use Windows until I can resolve this issue (grrr..).

I'm tempted to revert back to RTL8187, but the situation there was far from ideal. That, and I sorta kinda deleted the files instead of backing them up/renaming them (I know, bad move), to avoid the "alternate driver:.." message in ndiswrapper.

Any advice would be greatly appreciated!

Good weekend to you all--

---

### Post by panurge77 on 2007-07-08
I posted a guide [here]("http://ubuntuforums.org/showthread.php?t=493958&highlight=rtl8187") for rtl8187 with ndiswrapper driver and network manager disabled

---

### Post by swarup on 2007-07-18
My question is regarding the use of the tutorial at the very beginning of this thread, and its use with Ubuntu 7.04 Feisty Fawn.

I have a Novatel Wireless Ovation U720 USB modem (an aircard) which is what I use to go online with. It is a Sprint aircard connection. Up until now, I've been the only person using the aircard. But I would like to get a wireless router (the Kyocera KR1 EVDO Mobile Router) so other computers in the house will also be able to go online using the aircard. It is known that the Novatel aircard modem works will with the Kyocera. All the computers are running on Feisty Fawn. And I have purchased three WG111v2 Netgear wireless adaptors, one for each computer. My question is: The Kyocera mobile router is $155 from the internet. If I purchase it, am I going to be able to configure the WG111v2 Netgear adapters to work with Feisty? There has been so much discussion about this back and forth, that I am somewhat confused. Some write on the forums that they got great success, and others say it is not working at all. On the basis of your experience, should I be able to configure the Netgear WG111v2 to work with Feisty using the tutorial at the beginning of this thread? 

And one further question: Will it work with a USB type 1 port? My laptop is an older one, and does not have a USB type 2 port. If need be, I could purchase a PCMCIA card which has a USB type 2 adaptor, but I'd prefer of course not having to do so.

Thanks!

---

### Post by swarup on 2007-07-19
Could someone take a look at the tutorial for configuring WG111v2 (ID 0846:6A00) on Feisty given on this website below, and let me know if you think it looks reasonable?

[http://ubuntuforums.org/showthread.php?t=499084](http://ubuntuforums.org/showthread.php?t=499084)

The fellow has written things out pretty clearly and it seemed like it might be pretty easy to follow if it works. Looking forward to hear your thoughts. 

I could also give a go at the one listed at the very beginning of this thread, by phossal (sp?). And he added some specific workarounds in another posting around 2/3 of the way through this thread, in which he explained how to make the tutorial work with Feisty. 

Which tutorial do you think would be easier or better for a newbie like me to follow?

Thanks!

---

### Post by swarup on 2007-07-20
Any thoughts on my previous two postings?

---

### Post by swarup on 2007-07-25
I now have the WG111v2 working. It actually worked basically out-of-the box, with no special drivers needed. I am using the native Linux driver, and there is no problem. It works great with my Kyocera K1 router and novatel U720 evdo modem. 

Now that I have seen it all work so well with the native Linux driver, I do not understand what all the fuss is about using NDISwrapper and all sorts of different Windows drivers and this driver and that driver. The native linux driver and the gnome network manager work just fine. Why tamper with it and take all sorts of time with complex driver installations?

---

### Post by rjfioravanti on 2007-07-25
The first time I tried it, it also worked out of the box. However I noticed somewhere that the driver was experimental, and any success with it should be emailed to somebody.... not encouraging

The computer would freeze up a lot when using it, as soon as I used ndiswrapper everything was great. 

More generally , often if it works out of the box, it works with greater performance when using ndiswrapper

so thats why fiddle

---

### Post by kvonb on 2007-08-16
-

---

### Post by Jetjoint on 2007-08-18
Thanks so much Kvonb. That problem of not working on reboot if plugged in has been driving me mad........... Your fixed worked!!!!!!!

Thanks again:)

---

### Post by kvonb on 2007-08-18
-

---

### Post by kvonb on 2007-10-05
-

---

### Post by iansane on 2007-10-06
Ok I read this and it's somewhat confusing as to which steps are actually the right steps. Also what do I do to get the .inf file if the only download of version 1 from netgear is a windows self installing exe? I followed the links givin and still had to search the sight for the initial release and all I could find was the exe that installs a config utility on windows. I followed all the steps in the first how to and then couldn't understand what the other replies are saying to change. Can someone redo the howto with all the changes? I'm just trying to do exactly what it says because I am lost as far as knowing what it is that I'm doing. Thanks

---

### Post by iansane on 2007-10-06
Ok that was confusing. v1 uses software version 2.1 not the initial release I guess. I did the noob thing to but I am a noob. My ndis shows no hardware present. I have to agree with the guy that worked on his for eight days though that the major thing holding Ubuntu back is that in Windows it would have been a one or two click process and takin at the most 5 to 10 minutes even with netgear stuff mislabled but I have learned that if I hated Ubuntu I wouldn't be hear on the forum and I wouldn't spend days on something like that. I like many people don't have time for that. Assignments are due, jobs have to be done. That's why I still have XP in reserve as a duel boot. I do love Ubuntu though.

---

### Post by kvonb on 2007-10-06
-

---

### Post by iansane on 2007-10-06
thanks kvonb

I have another question. I'm having the same trouble on Kubuntu 7.04 on an older computer. I replaced KDE with Xubuntu-desktop hoping it would help to not use so many resources for the desktop. 
I also have Ubuntu 7.04 on my best computer and the wireless works fine without doing anything. (same dongle). 
Is there a way to just find the generic driver in Ubuntu and transfer it via thumbdrive to the right directory in Kubuntu? Or did I loose something when I installed xubuntu-desktop?
I'm trying your way but was just curious about the other. Thanks

---

### Post by iansane on 2007-10-06
OK it does work on Kubuntu but had to get the right version (v1) which is called wg111_2_1. That is bad naming from Netgear. It looks like the 2 is for version 2 to a newb like me. Anyway, I still had to add it to the ndiswrapper unlike ubuntu fiesty which worked fine with it's own driver. I installed ndisgtk and added it that way. I know that's cheating right? LOL
Now I know how to use it on three different OS's. 4 if you count my XP. Thanks so much. :)

---

### Post by kvonb on 2007-10-07
-

---

### Post by ninothedog on 2007-10-24
Thanks to Phossal, Kvonb and others responsible for this thread. I have the wg111v1 that describes itself as a wg111v2 and it wouldn't hold a stable connection to my network. Following the instructions I found here, I got it working properly. I had tried most things but not "blacklist" and that did the trick.

Thanks also for the mini console lesson about using tab to autocomplete text. Very useful.

The advice:
enable the wireless interface and add details from the network GUI tool
(Menu->System->Administration->Network)"
did not work for me as my System menu did not contain an "Administration" selection, but I didn't need to do it anyway.


I'm relatively new to Linux, but ran a Unix network many years ago. Unlike most window users I've missed a command console and am thrilled to have one back. I loaded all my software packages by using apt-get and that beats the hell out of changing cds and entering license numbers all day long. - Getting off topic. Sorry. Thanks again for the sage advice.

---

### Post by phossal on 2007-10-27
> **kvonb said:**
> Haha, nothing is cheating my friend, if it works, it's good ;).

I couldn't agree with anything more.

---

### Post by phossal on 2007-10-27
> **ninothedog said:**
> Thanks to Phossal, Kvonb and others responsible for this thread.

Yeah, Kvonb deserves a lot of thanks. I've been "on vacation" with a new development job for 6 months or so, and it appears Kvonb is continuing to be as helpful as he was to me when I first got going. 

Glad someone else has benefited.

---

### Post by kvonb on 2007-10-27
-

---

### Post by fabrice79 on 2007-11-11
Hello, I've just used the tutorial provided here to make my WG111v2 dongle work on Gutsy, and after 2 days of hard work I managed it; I think its pointless to describe the exact drivers and version I used cause it looks like there are too many versions of this device and everyone needs its own procedure.

The thing I wanted to point instead is the fact that since Feisty, blacklisting the conflicting drivers... doesn't blacklist. Even renaming the "wireless" directory doesn't have any effect. I always had that "alternate driver" line after the ndiswrapper -l command.
The only useful thing is to delete or move the wireless directory, and now i have e perfectly working device (well almost... WEP doesn't work, but thats another step :D ), without the alternate driver showing up, while before it always stopped working after a while, or had problems starting, and so on.

So, my question is: what's wrong with blacklisting? Why it's not working?

---

### Post by kvineeth on 2007-11-22
I am also facing the same issue...were u able to resolve it?if so plz do let me know

---

### Post by kvineeth on 2007-11-22
If u have resolved this issue do let me know...i am stuck up with it

---

### Post by kvineeth on 2007-11-22
there was an earlier mail in this thread which states the foll:

--------------------------------------------------------------------------------

Hi everyone!
I followed you're guide (with ndiswrapper) and it seems to work fine even with the light!
However I have encountered a problem. When I start my PC with the WG111v2 plugged in it all doesn't work, it seems like it loads the rtl8187 driver, even though I added them in the blacklist, and from the logs it seems like it endlessly scans for the AP on all the channels! However when I start my PC with the usb dongle unplugged and I plug it in after ubuntu has completed the startup it work flawlessly??!?! 
Any help on this?

Ciao!


I am facing the same problem ...If anyone has resolved this plz do let me know

---

### Post by fabrice79 on 2007-11-22
As I told before, looks like blacklisting is not working; the only solution working for me it's to move (or delete, but better to keep it) the entire "wireless" directory (located: /lib/modules/2.6.22-12-generic/ubuntu/wireless/).

It would be useful to find out why the blacklisting isn't working and how to solve it.

---

### Post by secretkeeper81 on 2007-11-27
This tutorial worked perfectly for me on Edgy, but today I tried following the same steps on Gutsy, and although ndiswrapper says "hardware present, hardware installed" when I run iwconfig it doesn't show any wireless interfaces, except for the loopback interface.

Could this be because of the blacklisting not working? If so, can you explain in detail what you mean by "move the entire wireless directory"?

---

### Post by carpespasm on 2007-12-13
I'd just like to chime in and say that I had the problem with it loading the other driver as well. Edit: there still seems to be a problem with it loading the native driver even though I've got the wireless directory removed as fabrice79 suggested to do.

---

### Post by kvonb on 2007-12-15
-

---

### Post by fabrice79 on 2007-12-23
Thx kvonb, but thats a pain, everything worked fine by deleting the wireless directory, but after an update the alternate rtl8187 appeared again under ndiswrapper -l, and the problems are back. But the directory is still missing so i dont know what to do!

It looks like devs don't want us to use this dongle, since it works perfectly with ndiswrapper, but they keep hiding that stupid rtl8187 broken driver everywhere to screw everything up...

---

### Post by fabrice79 on 2007-12-23
Ok, after the last upate the "alternate driver: rtl8187" under ndiswrapper -l disappeared again :-|

---

### Post by m4cks on 2008-01-03
I would like to report my results (new gutsy install). I have been able to use both rtl8187 and the ndiswrapper driver, but both have problems:

Device is a netgear wg111v2 (real v2), reporting as 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

rtl8187:
No security: Works, but performance degrades after a while
WEP/WPA: Works, but performance degrades after a while

ndiswrapper (tried with both the netgear (win98) 1_3_0 drivers and also the realtek manufacturers/OEM drivers)

No security: works perfectly. fast. holds connnection.
WEP/WPA: associates to AP, but does not "talk".. some packets are sent, but I can't get a DHCP response.

...since no security is not an option, I'm still stuck with the rtl8187 and degraded performance. If anyone knows why security might not be working with ndiswrapper and the two drivers I tried, I'm all ears.

also, router (siemens) is saying this when I try to connect with security:

2008-01-03 01:09:47 GMT E |Wireless             |Station MAC 00:1B:2F:71:82:E9 - association failed - responding station does not support the specified authentication algorithm.

It should be noted that WEP/WPA works perfectly fine in windows with this device and AP.

---

### Post by fabrice79 on 2008-01-06
> **m4cks said:**
> I would like to report my results (new gutsy install). I have been able to use both rtl8187 and the ndiswrapper driver, but both have problems:

Device is a netgear wg111v2 (real v2), reporting as 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

rtl8187:
No security: Works, but performance degrades after a while
WEP/WPA: Works, but performance degrades after a while

ndiswrapper (tried with both the netgear (win98) 1_3_0 drivers and also the realtek manufacturers/OEM drivers)

No security: works perfectly. fast. holds connnection.
WEP/WPA: associates to AP, but does not "talk".. some packets are sent, but I can't get a DHCP response.

...since no security is not an option, I'm still stuck with the rtl8187 and degraded performance. If anyone knows why security might not be working with ndiswrapper and the two drivers I tried, I'm all ears.

also, router (siemens) is saying this when I try to connect with security:

2008-01-03 01:09:47 GMT E |Wireless             |Station MAC 00:1B:2F:71:82:E9 - association failed - responding station does not support the specified authentication algorithm.

It should be noted that WEP/WPA works perfectly fine in windows with this device and AP.

Same exact ptoblem. The workaround I use is to allow just the dongle MAC address in the router settings, but I would prefer to have WEP working.

Let us know if you find a solution.

---

### Post by rayman_08 on 2008-01-09
hi, newbie here...  I was following the commands on page one and did fine up to the point of 

sudo ndiswrapper ....desktop -> ndis command not found

I tried searching for how to work around it but hasn't been much help.  Anyone else ran into this issue and have been able to fix it?  Ubuntu 7.04

---

### Post by secretkeeper81 on 2008-01-09
You mean you don't have ndiswrapper installed?

Well then, if you have access to network connection, just open a terminal and type:

```
sudo apt-get install ndiswrapper
```

If you don't have access to network connection, here is the work-around:

you need to download the packages from another computer which is connected to the internet, go here and download the packages:

[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/?C=M;O=D](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/?C=M;O=D)

move them to the linux box with a usb drive or similar, then to install them, just follow these instructions:

[https://help.ubuntu.com/7.04/add-applications/C/install-file.html](https://help.ubuntu.com/7.04/add-applications/C/install-file.html)

---

### Post by kvonb on 2008-01-09
-

---

### Post by miketowninc on 2008-03-23
I get this:

inffile : invalid driver!
net111v2 : invalid driver!



thats all 

I followed the steps in the first post. and it still does not work!

Any help?

---

### Post by m4cks on 2008-04-07
What command line are you running?

You want to make sure you're running ndiswrapper -i whatever.inf   ..not the name of the directory or anything, just the .inf file.

---

### Post by miketowninc on 2008-04-17
Ok so I installed my WG11v2 through this [http://ubuntuforums.org/showthread.php?t=590942&page=1](http://ubuntuforums.org/showthread.php?t=590942&page=1)

Is yours better? 

Well my problem is that my card will not conect to a trendnet router with wep on or not. But it will connect to my neighboors wifi which has no wep on. So I am guessing that it doesn't like the trendnet router.


So I decided to make an ad-hoc with another wifi card. And  it claims that it connects but it doesn't not get any IP's. I tried it on my Windows XP and it does connect and get ips. So there has to be something wrong with something in ubuntu. Any help?

THANKS!!

---

### Post by swarup on 2008-05-03
Has anyone tried this install yet with Hardy?

I've got a wg111v2 (real v2) that worked great with me in Feisty. I installed it with NDISwrapper using the tutorial by Phossal in post #1 of this thread, together with Phossal's adjustment of that tutorial for use with Feisty, which he gave in post #86 of this thread.

Now I'd like to start using it with Hardy, which I've just installed. Reading around the web a bit, it sounds like the native driver still isn't working great in Hardy. So I plan to do the same install with NDISwrapper which I described above for Feisty. Will it in fact be the exact same steps in Hardy as it was in Feisty, or are there any adjustments needed?

---

### Post by fabrice79 on 2008-05-04
I used [this guide (post 6)]("http://ubuntuforums.org/showthread.php?t=590942#6") on Hardy and everything worked fine with me. Try and let us know. The good thing is that the "alternate driver: RTL8187" thing when you type ndiswrapper -l in terminal is no more a problem on Hardy.

---

### Post by sennep on 2008-05-06
> **fabrice79 said:**
> I used [this guide (post 6)]("http://ubuntuforums.org/showthread.php?t=590942#6") on Hardy and everything worked fine with me. Try and let us know. The good thing is that the "alternate driver: RTL8187" thing when you type ndiswrapper -l in terminal is no more a problem on Hardy.

Really? Did you get it working with encryption? or is it without encryption?

---

### Post by RoNnY45 on 2009-04-27
[COLOR=Orange][B]Worked like a charm for me.. thanks.. I'm now loving Ubuntu(linux) like anything .. forget MS (its n00b) :P

I've Ubuntu 9.04 :)
[/B][/COLOR]

---

