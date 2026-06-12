---
title: "required kernel toshiba support not enabled (Trusty bluetooth support)"
date: 2015-04-23
forum: New to Ubuntu
---

### Post by davidjfarmboy on 2015-04-23
Hi all, sort of new to this part of linux and I'm trying to set up bluetooth to work with Ubuntu 14.04 on a Toshiba Satellite M645. Standard setup methods have not worked and I have tried toshset to no avail. It seems like it should be possible because I checked with lsmod | grep toshiba and the output is 

toshiba_acpi           28272  0 
sparse_keymap          13948  1 toshiba_acpi
wmi                    19193  1 toshiba_acpi
toshiba_bluetooth      12867  0 

so to my knowledge base capability is there (am I right?). Anybody know how to get it set up and running? What drivers, software, commands, dependencies, etc. do I need? Help would be greatly appreciated, please and thank you!

---

### Post by Bucky Ball on 2015-04-23
Welcome. How are you trying to get it to work? What software are you using to try and connect with your bluetooth device? Have you installed Bluez from the repos? I have a Toshiba Satellite Pro L510 and this is what I get:

```
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi
wmi                    19177  1 toshiba_acpi
toshiba_bluetooth      12852  0
```

The only difference to yours is the numbers and bluetooth works faultlessly here.

---

### Post by fburolo on 2015-04-24
Same here on my Satellite C50-B-15N with Ubuntu 15.04. Bluetooth present, but not working.

Bluez is already installed. It's not that I can't connect to a Bluetooth device, but that I can't even configure Bluetooth on my laptop to even start connect with anything. I just can't turn it on. Most "special" keys (brightness, touchpad toggle etc) are not working either. It should all be settable with toshset, but it is not....

---

### Post by fburolo on 2015-04-26
It came to my mind that this could also be a firmware related problem. Or, perhaps, something related to the fact that Ubuntu still ships with Bluez 4.x, while there is Bluez 5.x rolling for quite some time now?

---

### Post by mattharris4 on 2015-04-27
This sounds like an oversight in Ubuntu.  I don't even know if the developers at Canonical even thought of bluetooth compatibility when compiling the OSes, there is a good chance they did not and that is the crux of your issue, forcing you to use a non Canonical program which may be buggy in and of itself.  Bluetooth use in computers is esoteric enough yet that maybe the developers need to be nicely pushed into attempting to make the Canonical OSes bluetooth capable without going out of the Canonical system to attempt to make it work (I use a bluetooth headset with my cell phone from time to time, I like it for that purpose -- maybe in the future I will be able to use it for Skype computer to computer calls -- I do have a pair of headphones claiming to do this but do not have any computers with bluetooth to try that feature out).  

I think bluetooth technology in computers will become more and more useful over the years, I do know some Windows users can use it to transfer files from computer to computer or computer to other device, maybe even in the future instead of using a USB cord to connect a printer (or scanner, speakers, mouse, keyboard, etc.) without a USB dongle to a computer we will press a button and enter a passcode into a printer to connect it to the computer wirelessly.  I do think it is worth the time for Canonical programmers to attempt to make this possible.  Maybe a programmer will read this thread and send it up the chain of command there for possible approval to rectify your issue.

As for Bluez I am not familiar with that program.  Are you sure Ubuntu ships with a version of that program (or did it install with something else you downloaded)?  Is it intended for a Debian based OS (Canonical OSes are Debian based)?  If the program is not a Debian based program it will not work in a Canonical OS without changing a lot of code (which is way beyond my expertise).   Frankly this may be the first time this issue has come up here although evidently Bucky Ball has bluetooth working on his computer so there is a way to do it with some bluetooth cards.  Also, it is possible that bluetooth hardware is like video and sound cards where there has to be specific firmware installed to make it work properly and you don't have it installed (or it may not even be available like some esoteric video cards).  If your bluetooth card is from Nvidia this is more likely -- especially if it was made more than 1-2 years ago (I don't know if they even make bluetooth cards).  With video and sound cards everyone using a computer needs them to work so developers have put a lot of work into making this happen.  With bluetooth as esoteric as it is regarding computer use likely the work needed to make it universally (or almost universally) working hasn't happened yet because Linux, Canonical and Debian programmers haven't thought it important to deal with.

Some computer accessory sales sites offer a USB dongle that isn't any larger than a penny that is supposed to allow a computer to use bluetooth technology.  Maybe you could buy one (they don't cost much) and see if that would take care of this issue.  This is a stab in the dark but since Bucky Ball has bluetooth working on his computer maybe one of these dongles would be compatible with Bluez or another bluetooth program and work in Linux.  Here is one that is bluetooth 4.0 compatible although the description does not say whether it works in Linux OSes:  [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=7835049&CatId=909](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=7835049&CatId=909)

I wish you the best of luck getting bluetooth to work on your computer, David.  I am interested in knowing if you can get it working and how you did it if you do.  Theoretically this could be an issue that will need to be escalated all the way to Linus Torvalds, the inventor and current leader of the Linux movement and main programmer dealing with the Linux kernel (which is the backbone of all Linux OSes no matter what company compiles the OS) but I would not pursue that until you have exhausted all of your options within the Canonical system.  Please post back here with your progress on this.

---

### Post by fburolo on 2015-04-27
Actually, Bluetooth usually works (more-less) normally in GNU/Linux systems, already. :-) The problem seems to come up only with some Toshiba devices, for some reason or another... Like those owned by [**[COLOR=#000000]davidjfarmboy[/COLOR]**]("http://ubuntuforums.org/member.php?u=1980097") and me, obviously... :-/
Bluez is part of the standard Ubuntu Bluetooth stack, and yes, it is intended for GNU/Linux generally, including Debian and Ubuntu. In fact, Debian already started to ship with Bluez 5.x, while Ubuntu is still on 4.x, which is kinda unusual.

Buying an external dongle is a crappy solution. We have already bought our Bluetooth adaptors integrated in our laptops... Since Bluetooth is very low priority for me ATM, I am keeping it (otherwise I would just return it, as I have just bought this a couple of days ago), and try to fix it over time, and hope it will be fixed somehow in a new version of Ubuntu or something. I just like to have every component of my laptop funtional. ATM, only Bluetooth and some of the [fn] key are not working for me...
Bluez being outdated on Ubuntu, and this is a recent Bluetooth 4.x LE adaptor, it COULD be the problem, but it doesn't have to be. When I catch some time, I might test it with Debian or another distro having a more recent version of Bluez. But it could also be a problem regarding Toshiba-specific kernel modules, or missing firmware (which I haven't find out where to get it, or what exactly should I get, while Toshiba support sucks big time when it comes to giving such info).

I don't know... Any idea to a fix is welcome.

---

### Post by mattharris4 on 2015-04-28
Fburolo, thanks for commenting back. This thread is quite the education for me as well.  I agree that a bluetooth dongle is a crappy solution, I suggested it in lieu of tearing your laptop apart and replacing the bluetooth board inside with something compatible with Ubuntu.  I do agree that it could be something to do with the computer itself -- likely the bluetooth board inside needing something that the OS does not have -- and that it could certainly be a Toshiba-specific issue.  I am interested in reading the solution to this issue myself even though I don't have the feature on my computer (at least that I know of).  

I also heard about the release of Debian OS Jessie (actually it released less than a week ago, certainly not enough time for Canonical programmers to integrate it into Ubuntu).  You already know this but for others reading I will say that Ubuntu runs on a Debian base so I suspect the new version of Bluez along with new versions of everything else will be on either 15.10 or 16.04 LTS (Debian only updates about every other year so I suspect their programmers have made a lot of changes in that time).  Although this tech is esoteric as of now I suspect it will be standard equipment on all computers, cell phones (in a version capable of transferring data, not just for use of a headset), printers, scanners, external disk drives, etc. within ten years.

You also aren't the only person having problems with Toshiba CS regarding Linux.  We had another guy post here that wiped his drive (which had Win 8.1), installed Linux and it would not boot.  Toshiba CS told him to buy a $40 DVD set to reinstall Windows and all of the drivers (and evidently by omission not run Linux on it).  IIRC it turned out to be that boot-repair needed to be run properly but one commenter said some Toshibas have the UEFI tweaked from the factory to not run anything but Windows (all new HPs have this problem as well) and code might have had to be changed so the UEFI thought it was booting Windows and not Ubuntu (or whatever flavor OS he was using).  For the record Lubuntu installed without major issue (I did have to go in and unmute Alsamixer which isn't that difficult) on my year old Toshiba C55D-A5163 and that did ship with Win 8.1.  I haven't had the "pleasure" of speaking to Toshiba CS but from what people here are saying it sounds like they (or at least multiple CS agents there) don't know anything about Linux OSes whatsoever.

---

### Post by fburolo on 2015-04-28
Well, yes... Seems like Toshiba is Microsoft's favourite b*tch lately... :-D Fortunately, I bought my computer without any OS pre-installed and UEFI was disabled in BIOS by default (but it is available as an option), so I had no problem installing and booting Ubuntu on it. :-) The quick start guide that came with the notebook, however, did state basically that Toshiba couldn't care less about their non-Windows users. Well, I guess next time I will not buy another Toshiba computer anymore, nor recommend it to anyone.

Back on topic, I did some research, and I found out the Bluetooth is not necessarily a Toshiba issue, but maybe an Atheros one.
I have a Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter, which seems to be a combined WiFi/Bluetooth device, and DuckDuckGoing and Googling show that people keep having problems with this particular Atheros adapter in Linux. :-/
Any idea for a fix now, anybody?

---

### Post by mattharris4 on 2015-05-03
> **fburolo said:**
> Well, yes... Seems like Toshiba is Microsoft's favourite b*tch lately... :-D Fortunately, I bought my computer without any OS pre-installed and UEFI was disabled in BIOS by default (but it is available as an option), so I had no problem installing and booting Ubuntu on it. :-) The quick start guide that came with the notebook, however, did state basically that Toshiba couldn't care less about their non-Windows users. Well, I guess next time I will not buy another Toshiba computer anymore, nor recommend it to anyone.

Back on topic, I did some research, and I found out the Bluetooth is not necessarily a Toshiba issue, but maybe an Atheros one.
I have a Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter, which seems to be a combined WiFi/Bluetooth device, and DuckDuckGoing and Googling show that people keep having problems with this particular Atheros adapter in Linux. :-/
Any idea for a fix now, anybody?

I do have to agree that certain computer manufacturers need Linus' middle finger shoved into their eyes (here's looking at you HP which is even worse than Toshiba regarding Linux compatibility).  It is too bad that Toshiba evidently has such a bad attitude toward their non-Windows customers, especially since they evidently sell computers without an OS pre-installed.  What does Toshiba think people are going to put on a computer that does not come with an OS from the factory -- C++?  Maybe Fortran?  (both are ancient programming languages, C++ does have some use as a minor part of Windows today but no one installs them stand-alone on their computers nowadays).  Give me a %&*()#@ break!  People buy a computer without an OS to use Linux with, if they want to be in that market they need to support it!

I guess I was very fortunate that Lubuntu installed on my year old Toshiba laptop without major issue and that everything works on it.  I even dual-booted it with Windows 8.1 which many people are having trouble getting to work immediately no matter what the manufacturer.

As for the solution to your BT issue unfortunately I think the ultimate answer is for someone at Canonical or for one of Linus' crew (or a volunteer programmer if that is allowed, I know in other areas volunteer programmers are encouraged to attempt to solve such issues even for Canonical OSes -- although admittedly I am unfamiliar with written policy on this) to compile a driver for it.  I know I don't have the skills to do it (I am admittedly not a programmer).  That makes the USB BT adapter look more like the solution for you, at least in the short-term.  At least some of these adapters are the size of a US penny (or the size of newer wireless mouse adapters).  I am not the one having this issue and this still makes me wish I had earned a degree in computer programming while I was either attending or working at the university (my degrees are in accountancy and taxation which admittedly allowed me to make a great living over the years so I do not regret earning those degrees).

One more question:  How well does your Wifi work?  Since this is a combined unit I am curious.  It would seem that if the Wifi works the BT would as well but stranger things have happened I guess.  Good luck with this whatever route you end up taking to solve it.

---

### Post by Bucky Ball on 2015-05-04
Could we please get back on topic: i.e. fixing the bluetooth?

This is a support thread and not the place for lengthy digressions on what Canonical is and isn't doing right or the state of Ubuntu generally. Please use a NON-support area for such missives, either ***The Cafe*** or ***Ubuntu, Linux, OS Chat***. Thanks. 

PS: For the record, bluetooth has always worked faultlessly for me from 8.04 LTS on. ;)

---

### Post by mattharris4 on 2015-05-04
Back on task, here is a post from another recent thread in a similar vein.  Here is the thread link:  [http://ubuntuforums.org/showthread.php?t=2276479](http://ubuntuforums.org/showthread.php?t=2276479) 

Here is the pertinent post originally written by jeremy31:

I have a Toshiba P875 and I tried 4 wifi/bt combo cards before the  bluetooth even showed up in lsusb.  The one that finally worked was an  Atheros AR5B195, it has an Atheros AR9285 wifi with AR3011 bluetooth.  I  tried a couple Intel combo cards and another Atheros AR5B225 that had  AR9485/AR3012

My other Toshiba was factory equipped with a Wifi/Wimax card and it  would be able to find and use bluetooth on my other cards but the wifi  was always hard blocked 				


Maybe this will help you, it would involve finding an Atheros WiFi/BT combo card AR5B195.  Of course it would involve some research on your part to make sure this card will fit inside of your particular laptop, sizing of the laptop case has shrunk quite a bit over the past five or so years so the internal parts have likely shrunk to fit.  Good luck David, I hope you find a solution to this issue.

---

### Post by fburolo on 2015-05-04
Hey, thank you very much, [**[COLOR=#000000]mattharris4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1964569")! :-)

The linked thread didn't have the solution, but it pointed me into the right direction. :-)
"dmesg | grep -i blue" and "dmesg | grep -i firmware" showed the exact firmware file that couldn't be loaded on my system, which is **AthrBT_0x31010100.dfu**. So one basically needs to get that file and its pair **ramps_0x31010100_40.dfu**, put them both into /lib/firmware/ar3k/ (or /usr/lib/firmware/ar3k/ in 14.04, I think) and reboot. Then it works! :-)

Ephialta, on this other thread ([http://ubuntuforums.org/showthread.php?t=2260501](http://ubuntuforums.org/showthread.php?t=2260501)), links to a Windows driver archive (.cab) containing the missing firmware files.

So, now I am all set up. :-) And hopefully the next version of Ubuntu and other distros will have an updated firmware.

However, I have noticed WiFi connection weakening, and occasionally breaking, while a device is connected via Bluetooth...

---

### Post by mattharris4 on 2015-05-07
Congrats, fburolo.  I was just going to post from another post in the referenced thread regarding an alternate bluetooth program called blueman.  The post doesn't give any info on how to get it or much about it other than to say it worked with his computer.  Obviously that may be a moot point now but I am glad I was able to help.

Your wifi connection deteriorating while using bluetooth sounds like your wireless card isn't getting enough power to it to run both functions.  I don't see where that is a Linux issue unless the OS requires more CPU capability than Windows does and that combined with the capacity of your power block (I assume the computer is plugged in to AC current when you do this, if you are attempting to run both off of battery try AC power and see if it still does it) does not allow for both to run properly.  It is possible that you will only have this issue while either on battery or on AC power when also charging the battery on your laptop, when the battery is fully charged the extra power available could make your wifi/bluetooth card run both functions properly.  I say this because many Toshiba laptops (including mine) come with only a 45W power block compared with the standard 65W power block on other manufacturers consumer level computers.  IMO with a normal non power-miser CPU 45W leaves precious little current to run a laptop and charge the battery at the same time.  I don't seem to have lack of power issues with my Toshiba but I don't have bluetooth (that I know of) and have the AMD E1-2100 CPU which is a power-saving CPU that only draws 9W (my mother's Celeron 900 based eMachines laptop CPU uses 35W by itself, fortunately it came with a 65W power block for AC power, you may have a CPU in your Toshiba that draws similar current levels) -- that could make a big difference here IMO.

---

### Post by jeremy31 on 2015-05-08
The firmware needed by Atheros should be part of linux-firmware with a few exceptions.  Post the results of ```
lsusb
``` as there may be a few devices that aren't supported

---

### Post by fburolo on 2015-05-10
> **jeremy31 said:**
> The firmware needed by Atheros should be part of linux-firmware with a few exceptions.  Post the results of ```
lsusb
``` as there may be a few devices that aren't supported

It is, but it is outdated, and misses some files, so it doesn't support some adpters entirely out of the box, like the one I have.
You don't get the name of these combo adapters with lsusb, but with lspci. Mine is Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01), and Bluetooth doesn't work without the fix I already explained. Now I'm fine, thanks. Hopefully, linux-firmware will be updated, and avoid us the hassle in the future.

Now, if the OP has the same adapter, this is a solved thread. But I guess he abandoned us. :-D


@mattharris4: I already know Blueman. It is available in the official repos, and is just a Bluetooth manager. So, while it is more capable than what you get by default, it still won't work without the needed firmware and modules. :-)

---

