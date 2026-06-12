---
title: "Macbook pro (early 2011) - Having trouble with WiFi &amp; Eth."
date: 2015-02-04
forum: New to Ubuntu
---

### Post by wizrddreams on 2015-02-04
Hello all,

I am brand new to Linux OS's. 
I have installed 14.04LTS on my Macbook Pro 8,1 as a dual boot using rEFInd as a boot manager. 

I'm running into a basic issue (I hope). 
My WiFi is not working. 
I was able to set up the WiFi during the install but now that I've restarted and booted back into Ubuntu it's not working.

I've tried going to System settings ->Software & Updates->Additional drivers
I select the "Broadcom 802.11 Linux STA Wireless driver source from bcmwl-kernel-source (proprietary)" then choose apply changes.
Then nothing happens. 
I also see "This device is not working"

Additionally I tried to install the drivers, I honestly don't know if this is even the right thing to do.
But the commands and process I used for that is shown in the terminal history below.
I first tried with apt-get but being I have no way of connecting to the internet, I found a reference that had links to drivers so you could install without the internet. 
This does not seemed to have worked. Nor am I entirely sure of what "mod probe" is doing.

I figure showing these commands will help others diagnose the problem:
[IMG]http://i.imgur.com/XL40bK7.png[/IMG]

Here is the rest of the history related to my actions to try to diagnose the wireless problem:
[IMG]http://i.imgur.com/2dAAmxx.png[/IMG]

Here is the output of a few different commands that I found in other forums as useful for diagnosing the problem:
[IMG]http://i.imgur.com/waDBPEm.png[/IMG]

I am really not sure where to go with this at this point. 
Any advice and help will be much appreciated. 
I've been trying. I'm new to having to tinker with hardware settings like this. 

*Network Info:*
I have a wireless network setup.
My newer Macbook connects to it no problem (what I'm typing on).
When I boot into OS X on the dual booted Mac it also connects to the WiFi. 

The dual-booted Mac has an ethernet port, as you can probably see in the terminal output above.
I've tried connecting the ethernet directly to the dual-booted Mac while in Ubuntu, but no luck.
The connectivity symbol in upper right, does a loop of trying to connect and then disconnecting for ~5-6min before just giving up I guess. 

Please help!

---

### Post by wizrddreams on 2015-02-09
To solve this I connected to the ethernet. 
I had a bad cable as it turns out. 
If your computer does not have an ethernet port, my best advice is buy a "plug&play" usb ethernet port. 
Unless you have issues with internet service, once the ethernet is connected you can download the WiFi drivers.

See this video:
[https://www.youtube.com/watch?v=4VVosf9p5GM](https://www.youtube.com/watch?v=4VVosf9p5GM)

(I'll write explicit instructions for how to download the drivers later)

---

