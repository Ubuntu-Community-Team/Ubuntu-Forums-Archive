---
title: "Newbie installing wireless on Thinkpad T60 - not a clue!!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by phil81uk on 2008-06-12
My first day with Ubuntu (or Linux whatsoever).

Step one - I need to make wireless work so that I can sit in bed a learn Linux.

The wireless light on my dashboard is off, even with the wireless hardware switch in the ON position. My wireless works fine in Vista (I have dual boot).

My T60 Thinkpad is IBM model 2007-FVG (UT0FVUK). It has the following wireless adaptor:

ThinkPad 11a/b/g Wi-Fi wireless

I found the following post, but it says that it doesn't work on 64Bit systems (my Ubuntu is x64).

To be honest I don't even know where to start. I'm told that it's different to double-clicking an EXE file in Windows, and I just don't know.

I did a search and I think I need driver PIW4539. The manual said to do some SUDO GREP command to check if the driver is installed it is not. But I'm not even sure if that's the correct driver.

Thank you.

---

### Post by arckeda on 2008-06-12
Hey, I noticed that no one replied, and I would love to help you install wireless.  First, I need more information though.  Type the following command and tell me what you get: ```
lspci | grep Network
```  It should print out your wireless card / model, if it doesn't work, type ```
lspci
``` and search it manually to find your card.  If your card isn't a PCI card, tell me everything you know about it.

---

### Post by phil81uk on 2008-06-12
Wow, faster, more pollite, and knowledgable than paid support!!

Thank you for help. I followed the instructions and I got the following:

```

03:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

```

I hope that once I see how this driver is installed then I can do the next driver (for my navigation "nipple") by myself.

---

### Post by burakerenn on 2008-06-12
You can check here, it's for feisty but worth to try.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_T60p](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_T60p)

---

### Post by paulderol on 2008-06-12
the nipple is covered in the thinkpad-themed packages in synaptic, and may well work right now. as far as the Atheros wifi cards, you may want to switch to MadWifi as a manager for the connection...

---

### Post by phil81uk on 2008-06-12
Well, I've spent hours reading and it all points to MadWifi. But their site is down at present ([www.madwifi.org](www.madwifi.org)).

Also, the instructions tend to install MadWifi include the SVN command. However when I try to install SVN to make this command work I get:

```

$sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package subversion

```

Same when I try to do "sudo aptitude install build-essential". I get a "Couldn't find package" error. And this command seems to be required in many instructions on how to set up my wireless.

Thank you.

---

### Post by jtrindle on 2008-06-12
I'm going to assume your wired ethernet is working, or you won't get too far in the package acquisition process... whether via Synaptic or downloading source with Subversion.

You may very well find it easier to download with Synaptic from the GUI rather than apt-get.  

System->Administration->Synaptic Package Manager

search for subversion.

If you don't find it, select Settings->Repositories->Ubuntu Software and check at least the first two categories (main and universe) under "Downloadable from the Internet".  Check multiverse too if you have no objections to the licensing.

After doing this click Close and then Reload to get new package descriptions over the internet.  Then you should be able to do a search and find subversion.

---

### Post by phil81uk on 2008-06-12
Thanks. I installed SVN and the Build Essential thing.

I found this page which apparently has the driver for my device: [http://hardware4linux.info/component/15212/](http://hardware4linux.info/component/15212/)

But of course I have no idea how to install the driver.

---

### Post by phil81uk on 2008-06-12
Fighting on, apparently MadWifi comes with Ubuntu. The Mad Wifi website is down.

But the current release does not work with my Wifi Card. I need to compile the prerelease.

I will try to find how to do this. I found two tutorials but they refer to dead links on the MadWifi site.

---

### Post by phil81uk on 2008-06-12
Ok, I think I've found the solution here: [http://ubuntuforums.org/showthread.php?t=712663](http://ubuntuforums.org/showthread.php?t=712663)

I will carry this out once the MadWifi site is back up.

Thanks for now.

---

