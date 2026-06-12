---
title: "New to everything, rescued an old office PC. I'm already started, just need advice."
date: 2016-02-01
forum: New to Ubuntu
---

### Post by SuperTrainStationH on 2016-02-01
Well I've been reading around and looking at what's already been posted  and haven't seen anything that seems specific to what I want to ask, so  please excuse me and point me in the right direction if this is  redundant.

I've gotten my hands on an unassuming old IBM/Lenovo office PC which had no operating system. 

My  friend handed me a DVD of Xubuntu 15.10 and it seems to be running  fine, though for full disclosure, my background is with Mac OS X and  while I'm computer literate I don't have a huge amount of experience  with "tinkering" or doing things "manually", though I'm obviously  starting to go in that direction.

I basically want to use this  computer as a "glorified typewriter" for word processing, as well as  viewing photos and videos, and as far as those three things go, it's  already ready to roll with the included programs.

I basically just have three questions.


[LIST=1]
[*]the computer has an ethernet port in the back, but using a cable to connect it to my router or even directly into my modem doesn't seem to be getting me any closer to actually being able to connect to the internet,  but when i had a Windows PC a few years back there was no step other  than just plugging in the cable. I tried fiddling with the network settings as I would have expected I'd need to but I don't seem to be getting anywhere. I'm guessing that I'm either just  inexperienced in doing what I'm trying to do, or that the networking  card in the computer is incompatible with the operating system. I tried  just googling for stuff on my own but I guess I've either haven't found  answers, or did find answers and just aren't clever enough yet to have  figured them out.
[*]When playing back videos, the sound comes out from this horrible little "bell" speaker inside the PC. I plugged in external speakers using the audio port in the back of the computer but the sound still comes out of the bell speaker rather than the external speakers. Any advice for this would be great.
[*]I'm going to need to buy a printer and I guess in spite of all the documents I've read promising me that most USB printers are as simple as plugging them in and "winging it", I guess I'm being overly cautious and want to ask if there's any more specifics to it or advice that could be offered.
[/LIST]

Thanks and i'm sorry if this is unwelcome or redundant.

---

### Post by grahammechanical on 2016-02-01
I am not using Xubuntu. So, I can only give general directions.

> When playing back videos, the sound comes out from this horrible little  "bell" speaker inside the PC. I plugged in external speakers using the  audio port in the back of the computer but the sound still comes out of  the bell speaker rather than the external speakers. Any advice for this  would be great.

Xubuntu should have somewhere Sound Settings. Find that. Open it and with your external speakers plugged in to the motherboard's audio out or line out socket and you should see an option in Sound Settings>Output tab to select the audio out as an output source. It is kind of like plug & play. The option is not there until we plug in an audio cable.

As regards ethernet, the driver modules should be standard and are usually set up as kernel modules during installation. We still need to set up a connection. You need to look for some Xubuntu style of network manager and make sure if Enable Networking is ticked.

When we install Xubuntu/Ubuntu we are asked to confirm that there is a connection to the internet. Ethernet is preferable. Did you install Xubuntu and have an internet connection at the same time? If so, then I cannot see why you are having a problem. If the live/install session had ethernet access to the internet to download updates then Xubuntu has drivers for your ethernet adapters. So, why are you not getting internet access with ethernet after installation? It is a mystery to me.

Regards.

---

### Post by ajgreeny on 2016-02-01
For sound settings click on the volume icon in the panel and at the bottom of the pop-up menu you should see **Sound Settings**

This will open Pulseaudio volume control which allows you to set the volume of all the different output hardware in your machine.
Hopefully that will allow you to get sound from the speakers you want.

There is also the command alsamixer in terminal which opens a ncurses-like sound mixer.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture" hardware.
Esc will save and exit.

---

### Post by DuckHook on 2016-02-01
You mention that it's an "old" computer. It is possible that your hardware peripherals are not supported in the Xubuntu kernel and require further drivers.

So, in addition to the recommendations from grahammechanical and ajgreeny (do what they suggest first), please give us your hardware specs, especially your sound card and your network card. If you got the old manuals when you bought the computer, then this would be ideal. Otherwise, and seeing as you have no internet connection on this machine, I'm assuming that you are accessing this forum on some other machine, in which case I'm afraid you will just have to retype back to this thread the results of:```
sudo lshw -C network -C multimedia | egrep -i 'product|name|configuration'
```I've filtered the results a lot to require minimal retyping.

Let's worry about the printer after we get the rest working properly.

---

### Post by SuperTrainStationH on 2016-02-01
@grahammechanical 

The option to bring up the sound settings at the upper menu is extremely obvious, but when I click on it, nothing happens, the drop down menu just vanishes and there&#8217;s no result, so I really can&#8217;t change anything other than the volume slider thats accessible from the same drop down menu.

As far as the network manager goes, I accessed it easily, as I did when trying to set this up before seeking help.

It has three tabs, &#8220;General&#8221;, &#8220;DNS&#8221; and &#8220;Hosts&#8221;. 

When I opened the &#8220;Help&#8221; feature for the Network Settings program, it says that there should be FOUR settings,  &#8220;General&#8221;, &#8220;DNS&#8221;, &#8220;Hosts&#8221; and &#8220;CONNECTIONS&#8221;, the latter of which is nowhere to be found in my Network Settings, even though the Help feature even shows a screenshot of what the Connections tab is supposed to look like, and its exactly like I&#8217;d expected it to look and work on any other computer, my problem is the tab just flat out doesn&#8217;t exist for me to interact with, nor would I had even known it was supposed to be there if it weren&#8217;t for the &#8220;Help&#8221; feature saying so, and there&#8217;s no feature or option allowing me to enable or disable networking in general. 

So after all this I&#8217;m left with no internet access. I guess the struggle will continue.

@duckhook

Oops, I guess I should have been more specific than &#8220;old&#8221;. The machine is a 2005 IBM branded Lenovo ThinkCentre. 

The results are as follows.

 product: NM10/ICH7 Family High Definition Audio Controller
       configuration: driver=snd_hda_intel latency=0
       product: 82573E Gigabit Ethernet Controller (Copper)
       logical name: enp2s0
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=1.0-7 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s


At the very least all this has started getting me comfortable with using the terminal. At the risk of making myself sound older than I am, it&#8217;s bringing back nostalgic memories of the Apple II&#8217;s back at my elementary school&#8217;s computer lab. :P

Well thanks guys I didn&#8217;t expect to be so welcome or to receive so much help so suddenly.

---

### Post by Bucky Ball on 2016-02-01
Welcome. For future reference: much better for your chances of support to split your questions in to separate threads as otherwise it can get confusing (which is what is happening here with answers flying in for three different support requests), takes longer to get anywhere, and individual questions often don't get the specific attention they deserve to get fixed. 

We encourage you to split up your support requests and put them in appropriate forum areas. You will get better help faster in ***Networking & Wireless*** for your ethernet issue, for instance. 

Good luck.

PS: The ethernet cable *should* work without further tinkering, try tweaking with Pulseaudio Volume Control while you have some sound running for the sound issue (change the device port in playback), HP and Brother printers are friendly. (Apparently Canon work OK too, but no experience of them personally).

---

### Post by sudodus on 2016-02-02
There are a lot of tips for old computers in this link (including IBMs and Intel graphics).

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by mastablasta on 2016-02-02
> **SuperTrainStationH said:**
> 
the computer has an ethernet port in the back, but using a cable to connect it to my router or even directly into my modem doesn't seem to be getting me any closer to actually being able to connect to the internet,  but when i had a Windows PC a few years back there was no step other  than just plugging in the cable. I tried fiddling with the network settings as I would have expected I'd need to but I don't seem to be getting anywhere. I'm guessing that I'm either just  inexperienced in doing what I'm trying to do, or that the networking  card in the computer is incompatible with the operating system. I tried  just googling for stuff on my own but I guess I've either haven't found  answers, or did find answers and just aren't clever enough yet to have  figured them out.


It should work out of the box unless you somehow disabled it.

> 
When playing back videos, the sound comes out from this horrible little "bell" speaker inside the PC. I plugged in external speakers using the audio port in the back of the computer but the sound still comes out of the bell speaker rather than the external speakers. Any advice for this would be great.


Try the alsamixer. otherwise you will need to provide more info and possibly data from boot log in case there are any errors at boot or wrong sound card loaded. 
> 
I'm going to need to buy a printer and I guess in spite of all the documents I've read promising me that most USB printers are as simple as plugging them in and "winging it", I guess I'm being overly cautious and want to ask if there's any more specifics to it or advice that could be offered.



HP, Samsung and Brother have good Linux support. HP has really good support: [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)
eidt - I use Samsung as it was small enough to fit on the empty stand and was perfect for my needs.

---

### Post by KenSharp on 2016-02-02
Does **lspci** show a network card?

If so, what does **ethtool**&#8203; tell you?

---

### Post by coldraven on 2016-02-02
As you are having to use another PC to post here try doing this.
Typing this command will list your hardware and save it in a text file called hardware.txt. Then copy the file onto the other PC using a memory stick. Then when someone asks for details you can just copy/paste the relevant section into the code tags on the forum. (the # symbol)
Hope this helps :)
```
sudo lshw > hardware.txt
```

P.S. the extension txt on the filename is not necessary in Linux but will be needed if you transfer it to a Windows machine.  
Linux can work out what sort of file it's looking at and open it with the correct application. You can do this yourself using the file command.
For example if you find a file called "mystery123" do this and you will get information about it.
```
file mystery123
```

---

### Post by mastablasta on 2016-02-02
lspci lists all PCI devices (devices directly tied to motherboard).

lshw lists all hardware

lsusb lists USB devices

...

Have a look at this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by stalkingwolf on 2016-02-02
i have found on rare occassions that changing distros solves these issues.  might try mint or zorin or kubuntu

---

### Post by Mike_Walsh on 2016-02-02
I'll agree with stalkingwolf; a different distro would, in all likelihood, help. I'll go so far as to recommend one; Puppy Linux. I run it on a machine of similar vintage to your own (2005).....and it just **works**. It's designed from the ground up to make 'elderly' hardware useful & productive again. I tend to use it as my day-to-day system now; Xubuntu doesn't get that much use these days, due to each successive round of updates gradually breaking the functionality of my hardware, little by little.

Have a look at the Puppy Forums, and ask around. They're a very helpful, friendly bunch, and will soon make some sensible suggestions.

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

Hope that helps.


Mike. ;)

---

