---
title: "When is Ubuntu going to get wirless figured out?"
date: 2011-02-25
forum: Recurring Discussions
---

### Post by whatthefunk on 2011-02-25
This is becoming a major source of frustration and will likely lead to me ditching Ubuntu.

Network-manager, the network software that comes with Ubuntu, is complete garbage.  When I first put on Ubuntu, network-manager would drop wireless connections constantly, but did very well with wired connections.  I only have wireless at the moment, so I uninstalled network manager and installed wicd.  After working for a good while, it just decides to stop completely.  It tells me that my password is bad.  Ive spent the last two days trying to fix this with no success at all.  The only way to resolve this problem seems to be to reinstall Ubuntu which obviously sucks.  (Ive had to reinstall twice because of this already and I dont plan to do it again.) 

Im not the only one with these problems.  A quick glance through these forums shows that a large portion of problems with Ubuntu are with internet connection, something that should be easy.

So when is Ubunut going to decide to do something about this recurring, well-documented problem?

---

### Post by dmizer on 2011-02-25
Since this does not appear to be a support request, I've moved this to recurring discussions.

Thank you.

---

### Post by Copper Bezel on 2011-02-25
Everything that causes cancer in rats causes Linux to lose WiFi. On my previous PC, my first experience with Ubuntu was several hours of searching for support and trying to build a Madwifi driver from source. My local Linux guru at the time helped me through the process of installing the Windows driver in a wrapper instead - apparently, my card was being mis-recognized - but Ubuntu had such a series of problems with this internal network card even after we got the driver running that I ended up getting a USB dongle instead, for which I had to install another Windows driver. I upgraded Ubuntu from 8.04 to 8.10 and the internal network card started working consistently but could no longer connect to WPA2 networks, because something got dropped in the handshake or whatever. Booting into Fedora or Ubuntu Netbook Remix solved that problem, but I didn't *want* to use Fedora or UNR.

Now, on the other hand, I'm on fully supported hardware. I had to drop a couple of scripts I found into my suspend and wake processes, because they didn't restart the driver and my wireless card got lonely and unresponsive, but now my networking is rock solid, moreso than I see on folks' Windows machines.

Still, I never want to hear the syllables "ndiswrapper" again. Ever. For any reason. = D

So yes. WiFi is a pain. I sincerely doubt that the problem has anything to do with Ubuntu specifically. It's more like a fact of life.

---

### Post by whatthefunk on 2011-02-25
So how exactly did you solve your problem?  My driver is solid.  Im using the WinXP driver with ndiswrapper and not having any problems with it.  My problems are with the software that doesnt know how to connect to the internet.

---

### Post by Copper Bezel on 2011-02-26
I never did solve the WPA2 problem on that machine, but as I said, I could have just switched to Fedora at the time. I had a patched Madwifi driver module for a while, and then one of the subsequent kernel updates along the way actually fixed the problem with recognizing the card so that the extra module wasn't necessary.

My current machine just uses a chipset that Ubuntu is friendlier with. I've never had any problems with it to solve (except for the little suspend thing.)

---

### Post by walt.smith1960 on 2011-02-26
A lot of WiFi problems seem to be the luck of the hardware draw.  Some manufacturers seem to put effort into Linux support, others do not.  If a manufacturer will not devote resources to writing stable drivers and won't release hardware design info enabling others to write stable drivers, there isn't much users can do except to not buy those products. If the product is an integral device like mini PCIe, the user is pretty much screwed.

---

### Post by Shmantiv_Radio on 2011-02-26
I have to agree with this. I recently bought a Samsung N130 netbook, and the wireless has been a nightmare. The default driver in Ubuntu 10.04/10.10 is in the staging area of the kernel, and in the message log it actually says something like "in the staging area, you have been warned". 
Anyway, the WIFI connection will just randomly stop, not drop but stop. It would only work again after I restarted the machine. The only way I could find to slightly improve it was to blacklist the driver in modprobe, and use ndiswrapper instead, but after a while even that starts to have the same problem, the connection just randomly *stops*.

I really don't want to have to install Windows.. :(

---

### Post by JDShu on 2011-02-26
I've said this before, but if you're buying new hardware, and you want it to be Linux compatible, the best way is to look through Amazon or Newegg reviews, maybe search keyword "Linux". Chances are, the hardware that works perfectly will have reviews that talk about Linux compatibility. It is reality that we're still not at the stage where we can expect all hardware to work on Linux (though the improvement over the past few years has been massive), so a bit of research before buying will lessen a lot of the pain later.

---

### Post by cariboo on 2011-02-26
@whatthefunk, so you're saying that when you manually connect to your wirless ap, you have a good solid connection? Why do you need ndiswrapper? Isn't there a module included in the kernel for your wireless device?

I have 5 different wireless devices, all different modules, and the only one I have a problem with is a D-link WUA-2340, which was marked Windows only on the box. I can only get it to work running 32-bit, the windows 64-bit drivers just don't work.

---

### Post by whatthefunk on 2011-02-26
> **cariboo907 said:**
> @whatthefunk, so you're saying that when you manually connect to your wirless ap, you have a good solid connection? Why do you need ndiswrapper? Isn't there a module included in the kernel for your wireless device?

I have 5 different wireless devices, all different modules, and the only one I have a problem with is a D-link WUA-2340, which was marked Windows only on the box. I can only get it to work running 32-bit, the windows 64-bit drivers just don't work.

I had a solid connection after I used ndiswrapper.  It lasted for a couple weeks and then suddenly went out.  The module included in the kernal for my device doesnt work very well.  It allows me to connect, but at less than 1 Mbps.  Downloading ndiswrapper while using the included module took a couple hours and its only a few thousand k.

---

### Post by cariboo on 2011-02-26
You were blaming network-manager and wicd for connection problems, when you manuall connect do you have problems with dropped connections. When I say manual connection, I mean from the command line, as documented [here]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by whatthefunk on 2011-02-26
Ahh...yes yes.  Sorry, I didnt read your post right.  Ive spent a month trying to connect through the command line.  Ive tried nearly a hundred different variations of the connect commands.  I usually get the error message "No DHCPOFFERS received"  I can see all the networks, but I cant actually connect to any of them.

---

### Post by cariboo on 2011-02-26
If you can't connect to the ap, then I'd suggest the problem is the driver. If the driver worked for several months and then quit, what changes did you make before it stopped working reliably?

---

### Post by ronacc on 2011-02-26
I can tell you for sure that there is a wireless problem with natty , I suspect it has to do with the kernel and not just one driver , more than one card has the problem ( see various posts in the natty developement forum ) my wireless has been rock solid through many releases and was solid with natty at repo open but started randomly disconnecting when 2.6.38 came in . and it is not my card , modem (dsl) or router since maverick , suse and sabayon on the same box don't have the problem but the natty alpha2 live cd also does . and yes I've filed a bug , that was instantly invalidated .

---

### Post by cariboo on 2011-02-27
There have been some kernel regressions, with this kernel. I don't know what package you filed the bug against, but it may be worth re-submitting it as a kernel bug.

---

### Post by ronacc on 2011-02-27
actually apport filed that one . that was the only time the disconnect generated a crash report . the reason it rejected was that suposedly I had an out of date package which was BS , I checked and I had the latest version of that package that was available in the main repo .I may try again through LP directly  . I have checked my logs and the disconnect shows no error it just happens essentialy the same series of events in both the kernel and sys logs it disconnects , serches several times to re=establish the connection and then times out without ever doing it . then I have to disable wireless and re enable it to get it to connect again .

---

### Post by 3rdalbum on 2011-02-27
My wireless is a lot more sensitive with Natty, but it's not a Network Manager issue. The Network Manager software is mostly pretty good, the only problem really is that it's not very verbose if something goes wrong (for instance, it disappeared when /sbin/dhclient3 became corrupted; it should have displayed an informative error message).

A lot of people used to blame Network Manager when the problem was really the underlying driver or Ndiswrapper.

---

### Post by ronacc on 2011-02-27
filed bug # 726058  , I filed against NM since I cant prove its kernel regression , the devs will sort it .

---

### Post by NCLI on 2011-02-28
Seriously, people still have trouble with WiFi? I haven't had a problem for years now.

Anyway, look through [this list]("http://www.ubuntu.com/certification/catalog") before purchasing your next system if you want to be on the safe side.

---

### Post by Shining Arcanine on 2011-03-01
> **whatthefunk said:**
> This is becoming a major source of frustration and will likely lead to me ditching Ubuntu.

Network-manager, the network software that comes with Ubuntu, is complete garbage.  When I first put on Ubuntu, network-manager would drop wireless connections constantly, but did very well with wired connections.  I only have wireless at the moment, so I uninstalled network manager and installed wicd.  After working for a good while, it just decides to stop completely.  It tells me that my password is bad.  Ive spent the last two days trying to fix this with no success at all.  The only way to resolve this problem seems to be to reinstall Ubuntu which obviously sucks.  (Ive had to reinstall twice because of this already and I dont plan to do it again.) 

Im not the only one with these problems.  A quick glance through these forums shows that a large portion of problems with Ubuntu are with internet connection, something that should be easy.

So when is Ubunut going to decide to do something about this recurring, well-documented problem?

Post output of "lspci" and "lspci -n". Which drivers have you used? Is this a laptop or a desktop? Does it run 24x7? Have you been able to replicate this issue on another distribution?

By the way, how is this a well documented problem?

---

### Post by 3rdalbum on 2011-03-01
> **NCLI said:**
> Seriously, people still have trouble with WiFi? I haven't had a problem for years now.

Anyway, look through [this list]("http://www.ubuntu.com/certification/catalog") before purchasing your next system if you want to be on the safe side.

You could easily buy a wifi card on that list, and then find that a kernel regression in Ubuntu 11.10 turns it into a brick on that version, and Canonical won't be able to do anything about it.

---

### Post by juancarlospaco on 2011-03-02
wirless of the norbook can be a pronblem sometim

---

### Post by whatthefunk on 2011-03-03
> **cariboo907 said:**
> If you can't connect to the ap, then I'd suggest the problem is the driver. If the driver worked for several months and then quit, what changes did you make before it stopped working reliably?

I made no changes at all.  One day it worked, one day it didnt.  I shut down normally.  I checked logs and there doesnt appear to be anything mysterious.  It just stopped working.  I thought it was a driver issue too, so I uninstalled ndiswrapper and went back to the previous module which used to connect, but very slowly.  I still couldnt connect.  I reinstalled ndiswrapper and the WinXp module...still nothing.  So Im thinking that its not a driver.  I have no idea....

---

### Post by whatthefunk on 2011-03-03
> **Shining Arcanine said:**
> Post output of "lspci" and "lspci -n". Which drivers have you used? Is this a laptop or a desktop? Does it run 24x7? Have you been able to replicate this issue on another distribution?

By the way, how is this a well documented problem?

I used the driver that was automatically assigned to the device by the system and then the WinXp driver.  Laptop.  It does not run 24x7.  I dont want another distro.

This is a well documented problem because there are thousands of messages on this forum regarding this issue, there are millions more on other forums, and there are pages upon pages of bug reports.  Ubuntu sucks at wireless.

---

### Post by boydrice on 2011-03-03
> **whatthefunk said:**
> I used the driver that was automatically assigned to the device by the system and then the WinXp driver.  Laptop.  It does not run 24x7.  I dont want another distro.

This is a well documented problem because there are thousands of messages on this forum regarding this issue, there are millions more on other forums, and there are pages upon pages of bug reports.  Ubuntu sucks at wireless.

No offense but if you believe Ubuntu "sucks at wireless" why wouldn't you want to try another distro?

---

### Post by whatthefunk on 2011-03-04
> **boydrice said:**
> No offense but if you believe Ubuntu "sucks at wireless" why wouldn't you want to try another distro?

I run Lubuntu on it because its an older laptop.  Ubuntu and all its other derivatives dont run well on it, so theyre out.  Mint runs alright, but gives me some compatibility issues.  Puppy...I just dont like it.  Arch..I dont feel like Im good enough at Linux to go into it yet.  Also, the Ubunutu family has programs that I want.  Outside of the wireless issue, I love it.

---

### Post by cariboo on 2011-03-04
Through this whole thread, you haven' once mentioned the make and model of your device. It may help if you do, as others may have some insight into what the problem may be. BTW is this a device you can remove and try in a different computer?

Have you tried another distro using a live cd, or even Windows to see if the device still works, it could possibly have gone defective, the prism based device in an old HP laptop I had, showed the same type of symptoms. Replacing it with a used broadcom device solved the problem in a couple of minutes.

---

### Post by |{urse on 2011-03-04
Network-Manager has given me problems and so has wicd but one or the other always works better and I just use whichever. So.. Hey it's free. Learn a programming language and make a better one if you don't like it. It seems to be only kernel drivers for Atheros5x chipsets and bcmwl that are to blame for the wireless issues in linux, but smarter people than I write kernel drivers and wireless applets. Maybe i could make a wireless applet with dzen2 but not in a feature rich environment like gnome or kde. I think you basically could just fetch information from "iwlist scanning" to populate the menu, right? That's offtopic a bit but I'm very thankful for all many free programs that do such a great many things perfectly 97% of the time.

---

### Post by Copper Bezel on 2011-03-04
[QUOTE=cariboo907]Through this whole thread, you haven' once mentioned the make and model of your device. It may help if you do, as others may have some insight into what the problem may be.[/QUOTE]

Yeah, with a little Google-fu, it's not hard to find out the chipset of your wireless card based on your PC's model number. Google that + Ubuntu, and you'll probably find out whether or not there's an easy fix in a few minutes.

---

### Post by cblnchat on 2011-03-04
> **Copper Bezel said:**
> 

Still, I never want to hear the syllables "ndiswrapper" again. Ever. For any reason. = D

So yes. WiFi is a pain. I sincerely doubt that the problem has anything to do with Ubuntu specifically. It's more like a fact of life.

I hear ya! I HATE "ndiswrapper"!  I went thru that with my desktop a few years ago with 9.04 and 9.10.  I actually stopped using ubuntu cause of it!  Until i started again with my netbook :)  Luckly WiFi works right away on my netbook!

---

### Post by whatthefunk on 2011-03-07
> **Copper Bezel said:**
> Yeah, with a little Google-fu, it's not hard to find out the chipset of your wireless card based on your PC's model number. Google that + Ubuntu, and you'll probably find out whether or not there's an easy fix in a few minutes.

There is not an easy fix.  Ive been messing around with this for four months now.  Ive read every thread on the internet about it and nothing works.  There are also a lot of other people out there with this exact same problem.

Yes, the device works.  If I reinstall the OS, everything will work fine for a couple weeks and then it will suddenly stop.  This has happened three times now.  It is not a device issue and Im 99% sure that its not a driver.  Ive reinstalled everything related to the driver and it still doesnt work.

cariboo907...I havent posted any details in this thread because its really not a call for help.  Ive been through that several times and have given up.

---

### Post by ikt on 2011-03-07
> **3rdalbum said:**
> You could easily buy a wifi card on that list, and then find that a kernel regression in Ubuntu 11.10 turns it into a brick on that version, and Canonical won't be able to do anything about it.

So then don't upgrade to that version until the regression has been fixed?

---

### Post by bikeboy on 2011-03-07
"When is Ubuntu going to get wirless (sic) figured out?"

About two years ago.

---

### Post by aysiu on 2011-03-07
> **bikeboy said:**
> "When is Ubuntu going to get wirless (sic) figured out?"

About two years ago.
Not on my netbook, which (ironically enough) came with Ubuntu preinstalled.

Broadcom 4312. Still takes 45-90 seconds to reconnect after resume from suspend.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

---

