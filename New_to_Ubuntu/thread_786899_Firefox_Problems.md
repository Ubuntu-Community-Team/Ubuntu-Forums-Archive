---
title: "Firefox Problems"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Steve.G on 2008-05-08
Ok, first off. I have read copious threads in reference to Firefox, etc. This is my first time running Linux with a GUI. I used to have an old slackware box, and I have been playing with Linux off and on since then.

Here's my scenario: I just did a fresh install of Hardy on my machine. I have 512Mb of RAM which I tested using memtest86 for 22 hours, 0 errors. I have a 2.4GHz Pentium processor.

Periodically, FF will just crash for no apparent reason. Sometimes, it will refuse to launch at all. If I try to run it from the terminal I just get a "segmentation fault". Other times it will run fine for a while and then crash and after it crashes it refuses to re-launch for a while.

I have the flash plugin installed (the adobe one that auto-plays.. not the adobe/macromedia one, and not gnash), other extensions I have are Customize Google and Adblock.
[U]
Also[/U], there are some pages that refuse to load no matter what I do. I get a message stating that it appears to be a valid page but Firefox can't establish a connection. Strange. Websites like speakerheart.com come to mind, but there are others as well.

It's a very fresh install, and this is my hobby computer (built from spare parts and running xubuntu :) )so I don't mind messing with it to get it working. My tech knowledge is well...I'd say good, but outdated.

I know others have had these same or similar problems, but I have yet to see a solution that works for me. I have tried much of what has been posted in the forums already, but to no avail. Anyone care to help me out here?

---

### Post by neurostu on 2008-05-08
are you running 8.04 or 7.1?  I was getting similar issues with 8.04 so I went back to 7.1.

---

### Post by Steve.G on 2008-05-08
8.04... so my best resolution is just to downgrade? I can just do that through the terminal w/o having to download a new iso right? What's the command to do that?

---

### Post by Bigtime_Scrub on 2008-05-08
> **Steve.G said:**
> 8.04... so my best resolution is just to downgrade? I can just do that through the terminal w/o having to download a new iso right? What's the command to do that?

I had similar problems with FF too. I just kept 8.04 and downgraded the FF. Install FF2 and see how that goes, its cleared things up for me.

---

### Post by tyroeternal on 2008-05-08
Definitely give FF2 a go, the FF3 Beta is still... well... beta :(

---

### Post by neurostu on 2008-05-08
If search in this forum you will find a ton of threads about how to replace ff3 with ff2. Just search and you will find them.

Here is a post i started on the issue. [http://sudan.ubuntuforums.com/showthread.php?t=767821](http://sudan.ubuntuforums.com/showthread.php?t=767821)
but there are plenty more.

---

### Post by sailor2001 on 2008-05-08
I've had a 'bloat' issue with ff2 and buggy ff3.   download seamonkey, quite a bit lighter, (mozilla-seamonkey based on netscape) or for a REALLY light browser: kazehakase

---

### Post by bone2006 on 2008-05-08
I've had strange issues with firefox myself.  not sure if it was a setting or something I did.  But I would suggest using you remove your settings and restart firefox

sudo mv /home/USER/.mozilla /home/USER/firefoxbackup

Do this while firefox is closed and then restart firefox and it will recreate all your configuration as if it was a default install.  

I guess it would be the same as uninstalling /purge and then reinstall, but for me it's just easier to backup your config and then start up firefox.  Your bookmarks will at least be in the backed up directory

---

### Post by crjackson on 2008-05-08
A couple of things leap out to me.  

Firstly, Hardy installs a default version of a free flash plugin which causes problems, and you seem to have that one installed.

Secondly, you have the AdBlock extension installed which is also known to be problematic for some.

Thirdly, Iced-Tea Java is installed by default (I believe)

I suggest you go to the synaptic package manager and completly remove ALL flash support and iced tea java (be sure your browser is closed).  

Then install flashplugin-nonfree, and all the sun java 6 packages.

Then followup with an install of "xbuntu restricted extras".

Once everything is installed, log-off, and then log-in again and give it a spin.  I don't know anything about the google plugin so it would be a good idea to remove that too.

Once you get the basic install working for firefox, you can install your plugins one at a time and test each one be sure it isin't a problem.

Firefox 3 is still beta and doesn't work well with all plugins just yet.

---

### Post by AlexBellisBrown on 2008-05-08
The problem for me is that Firefox 3 only crashes when Flash gives it "the finger". Almost always with embedded video. Im sure the firefox team will fix this. Firefox 2 is unaffected.

---

### Post by neurostu on 2008-05-09
crjackson: You don't know about customizegoogle? Its one of the best plugins, it lets you do a couple of great things. 1 you can choose to have all google ads removed from search, gmail, (anything google) etc... but the main thing I use it for is for Streaming search results.  What this does is when you scroll to the bottom of a google search page, customizegoogle automatically grabs page 2 and appends it to the bottom of page one, so instead of having to click next page I just keep scrolling.

Customize google has a lot of great things you can tweak. I would definately recommend you try it out.

---

### Post by Steve.G on 2008-05-09
Well, I downgraded to Firefox 2. I also checked to make sure Iced-Tea wasn't installed and I don't think it is. I downloaded the packages for Sun Java. I also changed my DNS to OpenDNS. Still nothing. I can't get to cnn.com or track a package via usps. I tried to ping those hosts and the DNS resolves them and shows me the IP, but ping returns "host unreachable". Running host on them seems to function correctly.

I have tried several things based on what I have read here in the forums, but to date I have had 0 success in getting certain sites to load. Thanks for all the help in this thread, btw. Where do I look next?

---

### Post by love2learn on 2008-05-12
> **Steve.G said:**
> Well, I downgraded to Firefox 2. I also checked to make sure Iced-Tea wasn't installed and I don't think it is. I downloaded the packages for Sun Java. I also changed my DNS to OpenDNS. Still nothing. I can't get to cnn.com or track a package via usps. I tried to ping those hosts and the DNS resolves them and shows me the IP, but ping returns "host unreachable". Running host on them seems to function correctly.
 
I have tried several things based on what I have read here in the forums, but to date I have had 0 success in getting certain sites to load. Thanks for all the help in this thread, btw. Where do I look next?
 
I have to admit, I havent read the whole thread nor am I a resident expert but,
I have a couple of questions:
 
*1. I tried to ping those hosts and the DNS resolves them and shows me the IP, but ping returns "host unreachable". *
 
are you pinging the host name or the ip address? 
 
have you tried a traceroute? 
 
If you would post the output of the ping of the name and the ip address and the traceroute outputs as well it will help to make sure it is not a networking problem.

---

### Post by Steve.G on 2008-05-12
```
ping cnn.com
PING cnn.com (64.236.24.12) 56(84) bytes of data.

--- cnn.com ping statistics ---
27 packets transmitted, 0 received, 100% packet loss, time 26010ms

ping 64.236.24.12
PING 64.236.24.12 (64.236.24.12) 56(84) bytes of data.

--- 64.236.24.12 ping statistics ---
22 packets transmitted, 0 received, 100% packet loss, time 21009ms
```

```
traceroute cnn.com
The program 'traceroute' can be found in the following packages:
 * traceroute-nanog
 * traceroute
Try: sudo apt-get install <selected package>
bash: traceroute: command not found
sudo apt-get install traceroute
Reading package lists... Done
Segmentation faulty tree... 50%

```

strange, eh? Then I tried to run Synaptic, figuring I could get the package there.. which was working last night w/o problems...
```
sudo synaptic
Segmentation fault
```

So a quick reboot later I was able to install traceroute... :confused:

```
traceroute cnn.com
traceroute to cnn.com (64.236.24.12), 30 hops max, 40 byte packets
 1  home (192.168.1.254)  3.859 ms  4.470 ms  4.454 ms
 2  adsl-75-16-47-254.dsl.irvnca.sbcglobal.net (75.16.47.254)  18.662 ms  20.575 ms  24.422 ms
 3  dist4-vlan60.irvnca.sbcglobal.net (67.114.50.66)  28.540 ms  32.289 ms  34.139 ms
 4  bb2-g2-0.irvnca.sbcglobal.net (151.164.41.239)  150.447 ms  150.439 ms  152.336 ms
 5  151.164.93.167 (151.164.93.167)  49.872 ms  51.789 ms  55.731 ms
 6  asn1668-aol.eqlaca.sbcglobal.net (151.164.248.62)  59.633 ms  48.276 ms  52.155 ms
 7  bb1-las-P0-0.atdn.net (66.185.137.128)  64.016 ms  76.271 ms  20.966 ms
 8  bb2-hou-P6-0.atdn.net (66.185.152.27)  182.565 ms  184.524 ms  188.776 ms
 9  bb1-hou-P1-0.atdn.net (66.185.152.152)  72.140 ms  75.948 ms  79.886 ms
10  bb1-atm-P7-0.atdn.net (66.185.152.184)  113.388 ms  117.250 ms  121.061 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```

```
host cnn.com
cnn.com has address 64.236.24.12
cnn.com has address 64.236.29.120
cnn.com has address 64.236.16.20
cnn.com has address 64.236.16.52
cnn.com mail is handled by 10 atlmail3.turner.com.
cnn.com mail is handled by 10 atlmail5.turner.com.
cnn.com mail is handled by 10 nycmail1.turner.com.
cnn.com mail is handled by 10 nycmail2.turner.com.
cnn.com mail is handled by 30 lonmail1.turner.com.
cnn.com mail is handled by 40 hkgmail1.turner.com.

```

---

### Post by VitalBodies on 2008-07-25
> **Steve.G said:**
> Ok, first off. I have read copious threads in reference to Firefox, etc. This is my first time running Linux with a GUI. I used to have an old slackware box, and I have been playing with Linux off and on since then.

Here's my scenario: I just did a fresh install of Hardy on my machine. I have 512Mb of RAM which I tested using memtest86 for 22 hours, 0 errors. I have a 2.4GHz Pentium processor.

Periodically, FF will just crash for no apparent reason. Sometimes, it will refuse to launch at all. If I try to run it from the terminal I just get a "segmentation fault". Other times it will run fine for a while and then crash and after it crashes it refuses to re-launch for a while.

I have the flash plugin installed (the adobe one that auto-plays.. not the adobe/macromedia one, and not gnash), other extensions I have are Customize Google and Adblock.
[U]
Also[/U], there are some pages that refuse to load no matter what I do. I get a message stating that it appears to be a valid page but Firefox can't establish a connection. Strange. Websites like speakerheart.com come to mind, but there are others as well.

It's a very fresh install, and this is my hobby computer (built from spare parts and running xubuntu :) )so I don't mind messing with it to get it working. My tech knowledge is well...I'd say good, but outdated.

I know others have had these same or similar problems, but I have yet to see a solution that works for me. I have tried much of what has been posted in the forums already, but to no avail. Anyone care to help me out here?

segmentation fault? Do you have a blank disk in your drive?

---

