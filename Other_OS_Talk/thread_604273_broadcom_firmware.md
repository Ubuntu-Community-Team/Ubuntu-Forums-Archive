---
title: "broadcom firmware"
date: 2007-11-05
forum: Other OS Talk
---

### Post by igknighted on 2007-11-05
I need a distro that includes the broadcom firmware so I can test the wireless on my laptop.  I don't want to screw around with the partition tables until I see how the broadcom drivers perform, because I may just keep windows on the laptop.  So is there any distro that includes this?

---

### Post by K.Mandla on 2007-11-06
I don't recall one offhand. Can you be more specific about the card? Maybe someone has used an identical model and can suggest one that way.

---

### Post by jrusso2 on 2007-11-06
I believe PCLinuxOS does.  And Linux Mint might also.

---

### Post by igknighted on 2007-11-06
> **K.Mandla said:**
> I don't recall one offhand. Can you be more specific about the card? Maybe someone has used an identical model and can suggest one that way.

Its the 4311 (rev1).  Ubuntu and Mandy both complain about needing the firmware.  I will give PCLOS and Mint a shot.

---

### Post by rcdeacon on 2007-11-06
Mepis could also be a solution. I use in on my laptop. I does come with what you need. I had to opt for ndiswrapper and I have the windows drivers on my usb flashdrive. I can get pclinuxos to work using the driver off the flash drive and Mepis, using "network assistant" have proven to be quite good in getting the broadcom stuff working. They also have a great, helpful forum as well.

---

### Post by init1 on 2007-11-06
The only distro that sets up my broadcom chip correctly is Mepis. It uses ndiswrapper, and has a great GUI for setting up WEP/WPA. If you prefer, there is also Antix. It's based on Mepis but has Fluxbox rather than KDE.

---

### Post by igknighted on 2007-11-06
> **init1 said:**
> The only distro that sets up my broadcom chip correctly is Mepis. It uses ndiswrapper, and has a great GUI for setting up WEP/WPA. If you prefer, there is also Antix. It's based on Mepis but has Fluxbox rather than KDE.

Hmm... I have a rather strong dislike for ndiswrapper.  My chip is, in theory, supported by the broadcom bcm43xx driver, it just needs a firmware package that, to my understanding, is not included in Ubuntu because it is non-free.  I was hoping that one of those other distros that don't have such qualms would at least let me try out the bcm43xx driver w/ firmware, rather than resort to ndiswrapper (if it's ndiswrapper or vista, likely this laptop will remain vista)

---

### Post by Bachstelze on 2007-11-06
> **igknighted said:**
> Hmm... I have a rather strong dislike for ndiswrapper.  My chip is, in theory, supported by the broadcom bcm43xx driver, it just needs a firmware package that, to my understanding, is not included in Ubuntu because it is non-free.  I was hoping that one of those other distros that don't have such qualms would at least let me try out the bcm43xx driver w/ firmware, rather than resort to ndiswrapper (if it's ndiswrapper or vista, likely this laptop will remain vista)

You can install the firmware in any distro... Or do you want it right out of the box ? If it's just that you don't want to mess with the partitioning until you're sure it works, just test it from a Live CD (Ubuntu or any other).

*EDIT : just tried to install the bcm43xx firmware on a laptop with a 4306 in Gutsy's Live CD and it works perfectly.*

---

### Post by igknighted on 2007-11-07
> **HymnToLife said:**
> You can install the firmware in any distro... Or do you want it right out of the box ? If it's just that you don't want to mess with the partitioning until you're sure it works, just test it from a Live CD (Ubuntu or any other).

*EDIT : just tried to install the bcm43xx firmware on a laptop with a 4306 in Gutsy's Live CD and it works perfectly.*

Yeah, I ended up going with kubuntu gutsy.  It's working perfectly.  I had to dig up a cat5 to connect me first, and for some reason restricted driver manager doesn't run on the liveCD.  But there was a great script I found in the forums to install the firmware and it fired right up, so I went ahead and installed.  It didn't install the firmware to the HD, but since I was online then via the cat5, it found the firmware via the restricted manager.  Thanks for the suggestions everyone.

---

### Post by weblordpepe on 2007-11-07
Whewf. The world is saved from one more Vista machine.

---

### Post by styven on 2007-11-08
Good evening all,

It seems that your issue is sorted which is great.

However for the benefit of those that may be struggling, I used the following to get wireless working on my HP nx6310 laptop........

styven@styvens-laptop:~$ sudo apt-cache search fwcutter
[sudo] password for styven:
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware
styven@styvens-laptop:~$ 

Mind you in gutsy it prettty much does it for you, see screenshot.

Hope that will help someone.

Steve.

---

### Post by igknighted on 2007-11-08
> **weblordpepe said:**
> Whewf. The world is saved from one more Vista machine.

Actually it just moved it from my laptop to my desktop, sorry.

---

### Post by kevdog on 2007-11-08
Hope you like the broadcom firmware --  I really never have.  Not as much range and slower than ndiswrapper.  Hopefully one day it will be better.  Seriously however what do you have against ndiswrapper??? Pain to set up, however I believe the performance is worth the pain.

---

### Post by igknighted on 2007-11-08
> **kevdog said:**
> Hope you like the broadcom firmware --  I really never have.  Not as much range and slower than ndiswrapper.  Hopefully one day it will be better.  Seriously however what do you have against ndiswrapper??? Pain to set up, however I believe the performance is worth the pain.

I dislike it for the same reason I hate wine... supporting linux development.  You might want to try the broadcom firmware again.  I'm getting great performance, even compared to madwifi.  I'm getting over 80% signal in a room that typically gets around 60%.

---

### Post by Bachstelze on 2007-11-08
> **igknighted said:**
> I dislike it for the same reason I hate wine... supporting linux development.

Well... By using their stuff, you kind of support Broadcom, which is one of the most Linux-unfriendly companies on the planet. Personnally, if I had a laptop with an integrated Broadcom WiFi, I'd certainly use an USB wifi adapter with a Ralink or Zydas chip.

---

### Post by igknighted on 2007-11-08
> **HymnToLife said:**
> Well... By using their stuff, you kind of support Broadcom, which is one of the most Linux-unfriendly companies on the planet. Personnally, if I had a laptop with an integrated Broadcom WiFi, I'd certainly use an USB wifi adapter with a Ralink or Zydas chip.

Haha, touche.  Actually I have a cardbus wifi card with an atheros chip I could use.  But in honesty, I bought the laptop thinking from the reviews of others that it would be an atheros chip.  Now that I've paid broadcom for the hardware, I'm kinda stuck with it.  At least by using the free driver (even with non-free firmware), I can send back bug-reports.  Besides, atheros isn't totally free either.

Basically, it works, so I am content.

---

### Post by Dimitriid on 2007-11-08
> **igknighted said:**
> Hmm... I have a rather strong dislike for ndiswrapper.  My chip is, in theory, supported by the broadcom bcm43xx driver

I have the same chip: Ubuntu Gutsy asks to install the firmware as a "restricted driver" ( which is not technically a driver but is a restricted...thingie....controled by ubuntu restricter drivers and...thingies :)   )

I can report that it works well enough with disconnection issues from time to time depending on signal strenght ( low signal = very unreliable ) I had many problems on Gutsy with Network Manager ( laptop wouldn't shut down with it ) so i cant comment too much of its wireless capabilities since ive been using wicd.

---

### Post by igknighted on 2007-11-08
> **Dimitriid said:**
> I have the same chip: Ubuntu Gutsy asks to install the firmware as a "restricted driver" ( which is not technically a driver but is a restricted...thingie....controled by ubuntu restricter drivers and...thingies :)   )

I can report that it works well enough with disconnection issues from time to time depending on signal strenght ( low signal = very unreliable ) I had many problems on Gutsy with Network Manager ( laptop wouldn't shut down with it ) so i cant comment too much of its wireless capabilities since ive been using wicd.

Apparently it makes a big difference which chip you have specifically.  Mine is the 4311 (rev 01) which seems well supported.  The 4318 and 4311 (rev 02) both seem, well, less well supported.  As for other models I have no idea.

---

### Post by weblordpepe on 2007-11-09
I'm running this in Ubuntu Gutsy:
[B]Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
[/B]
But it crashes when I go to use the WIFI network selection tool thing. It won't do WEP. Which is odd because it used to when I had ndiswrapper going.

I can't connect it at home :( Which stinks because thats where I want to use WIFI. I have WEP network at home, so my PDA will work.

---

### Post by VCSkier on 2007-12-01
Do any of you have any recent experience with bcm43xx on a Broadcom 4306?  My wife laptop has that card, and I installed Ubuntu 6.10 or 7.04 on it, and the connection was quite unreliable; disconnecting every 5 minutes or so.  The experience turned her off to linux, and so I've been waiting, hoping that support would improve...

Has stability improved for the 4306?  I plan on giving it another try when 8.04 is released, but I'm curious if there have been any changes.  Thanks!

---

### Post by igknighted on 2007-12-02
> **VCSkier said:**
> Do any of you have any recent experience with bcm43xx on a Broadcom 4306?  My wife laptop has that card, and I installed Ubuntu 6.10 or 7.04 on it, and the connection was quite unreliable; disconnecting every 5 minutes or so.  The experience turned her off to linux, and so I've been waiting, hoping that support would improve...

Has stability improved for the 4306?  I plan on giving it another try when 8.04 is released, but I'm curious if there have been any changes.  Thanks!

Use the latest version (7.10 currently).  Connect to the internet via cable (needed to dowload firmware).  Open the restricted driver manager, it will offer to download the firmware and install it.  When it is done, reboot or simply restart network-manager and your wifi will be ready to use.  If you use WPA2 encryption you will also need the wpa_supplicant app, but just search the forum, its fairly simple.

It works very well for me with a 4311 card at least.  I might suggest trying to get the new driver (b43, part of the mac80211 stack i believe) instead... this should be mainline in Gutsty's kernel IIRC, but maybe it didn't make it until 2.6.23...  In theory this is a better driver you might have better luck.

---

### Post by TripWire7 on 2007-12-02
I also have a broadcom 4311 card however I can't maintain my connection to my network.  It will work fine for about a minute and then it stops working,  I tried this
 
styven@styvens-laptop:~$ sudo apt-cache search fwcutter
[sudo] password for styven:
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware
styven@styvens-laptop:~$ 

and now I can't connect to my network
I'm as much of a noob as i can be being I've used different versions of windows my whole life, but vista made me mad so I'm using Ubuntu 7.10 now.  I really like it and got my sound and dvd drive figured out and working but now my wireless is giving me trouble, any ideas?

---

### Post by evadwolrab on 2007-12-02
> **styven said:**
> Good evening all,

It seems that your issue is sorted which is great.

However for the benefit of those that may be struggling, I used the following to get wireless working on my HP nx6310 laptop........

styven@styvens-laptop:~$ sudo apt-cache search fwcutter
[sudo] password for styven:
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware
styven@styvens-laptop:~$ 

Mind you in gutsy it prettty much does it for you, see screenshot.

Hope that will help someone.

Steve.
I get 'the software source for the package bcm43xx-fwcutter is not enabled' when I use that restricted package manager to do it automatically. I've enabled everything in the first tab in the repo's section of synaptic.

Any ideas anyone? I've tried searching synaptic for 'bcm' but nothing comes up.

---

### Post by hkgonra on 2007-12-02
> **evadwolrab said:**
> I get 'the software source for the package bcm43xx-fwcutter is not enabled' when I use that restricted package manager to do it automatically. I've enabled everything in the first tab in the repo's section of synaptic.

Any ideas anyone? I've tried searching synaptic for 'bcm' but nothing comes up.

getting the same error. How can I fix it ?

---

### Post by evadwolrab on 2007-12-03
> **hkgonra said:**
> getting the same error. How can I fix it ?
I've got mine working now. I *think* it was because I used Automatix and downloaded a bunch of stuff. Try using Synaptic and Automatix to install some other stuff first, then go back to the restricted drivers thing and it should work.

Obviously this isn't a direct fix to te problem, but it made mine work. Maybe someone on here can explain why it started working after I installed some stuff. Good luck.

---

### Post by VCSkier on 2007-12-04
> **igknighted said:**
> Use the latest version (7.10 currently).  Connect to the internet via cable (needed to dowload firmware).  Open the restricted driver manager, it will offer to download the firmware and install it.  When it is done, reboot or simply restart network-manager and your wifi will be ready to use.  If you use WPA2 encryption you will also need the wpa_supplicant app, but just search the forum, its fairly simple.

It works very well for me with a 4311 card at least.  I might suggest trying to get the new driver (b43, part of the mac80211 stack i believe) instead... this should be mainline in Gutsty's kernel IIRC, but maybe it didn't make it until 2.6.23...  In theory this is a better driver you might have better luck.

Thanks for the advice.  I did some research, and you were very right. There *is* a new and *improved* driver available, b43, but it is not included in 7.10.  It will be included by default in the kernel for Hardy (2.6.24).  I haven't been able to find what specifically has improved on this new driver though.  Is it likely that connection stability has improved, or are there just other minor improvements?

Also, does anyone know if it is likely that this new driver will be backported into 7.10, or if we will just have to wait for 8.04?

@ hkgonra and evadwolrab: bcm43xx-fwcutter is still listed in my gutsy repo's.  Specifically, it's in "Universe." Double check that universe is enabled, and then be sure to reload your repo cache.  Alternatively, if you're still having problems, you can install the new b43 driver manually [over here]("http://linuxwireless.org/en/users/Drivers/b43").  If you do, let me know how it runs for you...  is it noticeably better?

---

### Post by igknighted on 2007-12-04
> **VCSkier said:**
> Thanks for the advice.  I did some research, and you were very right. There *is* a new and *improved* driver available, b43, but it is not included in 7.10.  It will be included by default in the kernel for Hardy (2.6.24).  I haven't been able to find what specifically has improved on this new driver though.  Is it likely that connection stability has improved, or are there just other minor improvements?

Also, does anyone know if it is likely that this new driver will be backported into 7.10, or if we will just have to wait for 8.04?

@ hkgonra and evadwolrab: bcm43xx-fwcutter is still listed in my gutsy repo's.  Specifically, it's in "Universe." Double check that universe is enabled, and then be sure to reload your repo cache.  Alternatively, if you're still having problems, you can install the new b43 driver manually [over here]("http://linuxwireless.org/en/users/Drivers/b43").  If you do, let me know how it runs for you...  is it noticeably better?

Try out the Fedora 8 liveCD if you want to test the drivers.  You can boot their liveCD, install the firmware and restart nm-applet and it should work.  At least it would show you if the drivers are worth waiting for or even perhaps compiling your own on Ubuntu.

Here's the fedora guide for broadcom with b43:  [http://www.fedoraguide.info/index.php/Fedora8#Broadcom_bcm43xx_.28Method_2.29](http://www.fedoraguide.info/index.php/Fedora8#Broadcom_bcm43xx_.28Method_2.29)

---

### Post by weblordpepe on 2007-12-05
I know this isn't related in any way - but I am really starving and I might make some hot dogs.
Anyway I use the Backtrack Live-CD when I want to mess around with stuff. And that works great with my Broadcom chipset. Works out of the box. Of course being backtrack you have to turn on the network interface, but that's it. Works great.
I recommend BackTrack.

---

