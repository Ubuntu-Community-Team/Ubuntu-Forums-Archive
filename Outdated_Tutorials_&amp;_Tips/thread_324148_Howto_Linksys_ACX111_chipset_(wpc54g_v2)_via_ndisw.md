---
title: "Howto: Linksys ACX111 chipset (wpc54g v2) via ndiswrapper"
date: 2006-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dmizer on 2006-12-23
**[COLOR="Red"]*** Linksys has updated their drivers, and this method is now a REAL pain to get working. ***[/COLOR]**
**[COLOR="Red"]*** Continue with the knowledge that this will take effort. ***[/COLOR]**

Linksys ACX111 chipset (wpc54g v2) via ndiswrapper EDGY, FEISTY, GUTSY, HARDY, IBEX, JAUNTY, or KARMIC

Note: There are _NO_ 64 bit drivers for this card.

[COLOR="Red"]Warning! this howto is specific to THIS card.  If you have a Linksys wpc54g card, look at the bottom and check which version it is.  If your card does not say "ver. 2" then this method can only be used as a guide, not as a howto.  Though you may be able to adapt it to your needs.[/COLOR]
[SIZE="3"][B]
Preface[/B][/SIZE]
==============================================
Unless you're using Dapper, the linksys wpc54g v2 appears at first to work out of the box.  And actually, it does work tolerably well for short periods of time.  But, if you're like me and spend more than a few hours at a stretch online, you'll run into this pesky little error:
```
acx: BUG: tx_head:1 Ctl8:0xC0 - failed to find free txdesc
```
which will eventually consume your resources until you are disconnected.  And, since I have not yet found a workable solution to this problem, I reached for my old NDISWrapper howto here: [http://ubuntuforums.org/showthread.php?t=201633](http://ubuntuforums.org/showthread.php?t=201633)

Also, using the native ACX driver for this card will not allow you to use advanced encryption like WPA.

I had to adapt the guide considerably to make it work here, but it's significantly easier than making it work in Dapper.
==============================================



[SIZE="3"]**--Prework--**[/SIZE]
[B]
Remove the card from the PCMCIA slot.[/B]

If you have not already done so, enable your multiverse and universe repositories.  If you do not know how, take a look here: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

**Install ndiswrapper.**

[INDENT][COLOR="Red"]note: if you've already installed ndiswrapper in prior (most likely unsuccessful) attempts in making this card work, you will need to both remove the ndisgtk package, as well as remove the drivers from the Ndiswrapper module.  See this post for instructions on how to remove previously loaded drivers: [http://ubuntuforums.org/showpost.php?p=3783621&postcount=30](http://ubuntuforums.org/showpost.php?p=3783621&postcount=30)[/COLOR]
[/INDENT]
For Edgy, use this command.
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.8
```
For everything else, use this line instead:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

also, please [COLOR="Red"]do NOT install the ndisgtk package[/COLOR] because of this bug: [https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983)

**Prepare the windows driver.**
1) Create a directory in your home folder called linksys:
```
cd
mkdir linksys
cd linksys
```
2) Download the Windows driver from Cisco.
```
http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip
```
3) Extract the archive:
```
unzip wpc54g_v2_driver_utility_v2.02.zip&&cd WPC54Gv2_40826
```
4) Fix file naming convention problem (Linux is case sensitive and Windows is not, thus requiring this step)
```
mv tnet1130.sys TNET1130.sys
```
```
sed -e 's/tnet1130.sys/TNET1130.sys/' LSTINDS.INF > LSTINDS.new&& mv LSTINDS.new LSTINDS.INF
```
*note* the above command searches the file LSTINDS.INF for "tnet1130.sys" and replaces it with "TNET1130.sys".  you are welcome to simply open LSTINDS.INF with your favorite text editor and make this change manually.

**Load the driver into ndiswrapper module.**
```
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper
```
[SIZE="3"]**--Make the arrangement work at boot--**[/SIZE]

**Blacklist the troublesome acx driver**

*note* This step is not necessary for Karmic because the ACX module is not included in Karmic.
```
sudo modprobe -r acx
echo "blacklist acx" | sudo tee -a /etc/modprobe.d/blacklist
```

**Make the ndiswrapper module load at boot**
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

[SIZE="3"]**--Check your configuration--**[/SIZE]

**Now insert your card and do the following**
```
ndiswrapper -l
```
[SIZE="1"]note: this is a lower case L, not an upper case i or the number one.[/SIZE]

**You should get output that looks something like this:**
```
Installed drivers:
lsbcmnds                driver installed
lstinds         driver installed, hardware present
```
If not, you may need to go back and review some of the steps or take a look at the wiki here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29), or simply post in this thread and I will be more than happy to assist you.

If all has gone well up to this point, then you can open networking and configure your card.  Congratulations, you now have a working wpc54g v2 card!

[SIZE="3"][B]
After word[/B][/SIZE]

For troubleshooting, see this thread: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

[SIZE="3"]**Footnote on enabling WPA**[/SIZE]
==============================================
I do not personally have the ability to test WPA encryption.  However, multiple sources indicate that this card does indeed work with WPA.

To make this card work with WPA encryption, follow the howto here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
as well as [blazerte's](http://ubuntuforums.org/member.php?u=37632) additional notes in this post: [http://ubuntuforums.org/showpost.php?p=4357062&postcount=32](http://ubuntuforums.org/showpost.php?p=4357062&postcount=32)

If you need more help than is provided by the above two links, I will most likely be unable to assist.
==============================================

version history:
[SIZE="1"]Jan. 22nd '07 - updated the howto for linksys' current driver release for this card.
Apr. 1 '07 - removed needless secondary driver, and tested Feisty beta
Apr. 14 '07 - updated links so they pointed to the new .org tld
June 18 '07 - minor change (typos)
Aug 18 '07 - formally retested feisty
Nov 12 '07 - howto works with gutsy per [ffadmraven](http://ubuntuforums.org/showpost.php?p=3753327&postcount=28)
Nov 19 '07 - added link for how to remove previously loaded drivers from Ndiswrapper.  Some minor formatting and language use changes.
Feb 23 '08 - added footnotes for enabling wpa advanced encryption.
Apr 09 '08 - included easier method of adding ndiswrapper to /etc/modules
May 14 '08 - included easier method of blacklisting native driver; cautionary note about using nano is no longer needed.
Jun 17 '08 - updated linksys ftp url per [jshuster](http://ubuntuforums.org/showpost.php?p=5201408&postcount=59) and added confirmation that the card works in HARDY
Jun 19 '08 - updated directions on tnet1130.sys case change
Jun 26 '09 - updated linksys ftp url, fixed typo in title, added troubleshooting link
Oct 30 '09 - Howto works with Karmic per [iliis](http://ubuntuforums.org/showthread.php?t=1291186). Added a few Karmic specific instructions.
Oct 2 '10 - Updated driver link per [poltr1]("http://ubuntuforums.org/showpost.php?p=9914295&postcount=109")[/size]

---

### Post by dmizer on 2007-03-31
The "acx: BUG: no free txdesc left" made it into Feisty at least for the time being.

I have tested this howto in Feisty and it does work with one minor modification.  When installing ndiswrapper, the line should read:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by brion@cbkidder.com on 2007-04-01
For what it's worth, this did not work with my WPC54G v3 card in Edgy.

When I tried to load the INF file via ndiswrapper, I got the following error:
couldn't copy LSBCMNDS.INF at /usr/sbin/ndiswrapper-1.8 line 144.

bummer

---

### Post by dmizer on 2007-04-01
yes.

that's why i put this at the very top of the howto:
> **dmizer said:**
> [COLOR="Red"]Warning! this howto is specific to THIS card.  If you have a Linksys wpc54g card, look at the bottom and check which version it is.  If your card does not say "ver. 2" then this method can only be used as a guide, not as a howto.  Though you may be able to adapt it to your needs.[/COLOR]

other versions of this card (the v3 for example) have different chipsets which require different techniques for making them work properly.

sorry.

---

### Post by darkhacker902 on 2007-04-13
Ok, I got to sudo modprobe ndiswrapper.

When i enter the command it gives me this:

FATAL: Could not open '/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory.


My card, the linksys WPC54G Ver.2 doesnt even show up in the network window, it used to, but i have tried a LOT of tuts on how to install it, and it doesnt now :(.


Please help, a bit of a noob here.



Ryan

---

### Post by dmizer on 2007-04-13
that kernel doesn't look like an edgy kernel.  if you're using dapper, give this method a shot instead: [http://ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g](http://ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g)

---

### Post by darkhacker902 on 2007-04-13
> **dmizer said:**
> that kernel doesn't look like an edgy kernel.  if you're using dapper, give this method a shot instead: [http://ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g](http://ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g)
How do I find out what version or Kernel Im Running? And how do I update?



Ryan

---

### Post by dmizer on 2007-04-13
> **darkhacker902 said:**
> How do I find out what version or Kernel Im Running? And how do I update?
well, in your previous post, this line:
> **darkhacker902 said:**
> '/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko'
has your kernel in it: 2.6.15-26-386 ... which looks like a dapper kernel.

you can also find out with this command:
```
uname -r
```

also ... system > about ubuntu should give you information about the name as well. it will say something like, "thank you for your interest in Ubuntu 6.06 - Dapper Drake"

you shouldn't have to upgrade yet.

my ndiswrapper howto for dapper drake has been retired, but is located here: [http://ubuntuforums.org/showthread.php?t=201633](http://ubuntuforums.org/showthread.php?t=201633) ... you can make that howto work by blacklisting a usb module.  if you're interested, i can walk you through it, but i think the method i linked previously will work better for you.

---

### Post by darkhacker902 on 2007-04-13
> **dmizer said:**
> well, in your previous post, this line:

has your kernel in it: 2.6.15-26-386 ... which looks like a dapper kernel.

you can also find out with this command:
```
uname -r
```

also ... system > about ubuntu should give you information about the name as well. it will say something like, "thank you for your interest in Ubuntu 6.06 - Dapper Drake"

you shouldn't have to upgrade yet.

my ndiswrapper howto for dapper drake has been retired, but is located here: [http://ubuntuforums.org/showthread.php?t=201633](http://ubuntuforums.org/showthread.php?t=201633) ... you can make that howto work by blacklisting a usb module.  if you're interested, i can walk you through it, but i think the method i linked previously will work better for you.Anything I can do to get this working, as I pointed out in the other thread that apparently doesnt work either. I just want to the thing to work....


Ryan

---

### Post by dmizer on 2007-04-13
i have responded in the other thread.

---

### Post by tturrisi on 2007-04-14
FYI,
I never have any issues using acx chipsets in Etch w/out using ndiswrapper.  One needs the most recent firmware.
[http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)

---

### Post by dmizer on 2007-04-14
the acx module with firmware change works for about 2 hours.  then my machine starts to get slow, and page load times are painful.  dmesg is filled with this:
```
acx: BUG: tx_head:1 Ctl8:0xC0 - failed to find free txdesc
```
eventually i cannot get any respose from the network including file shares, and my machine is crippled, requiring a reboot.

ndiswrapper does not have this dysfunction.

---

### Post by nidhogg16 on 2007-06-19
I probably would have gone back to Dapper anyways, but for my own understanding i would like some help with it.  My problem was with uninstall/reinstall, when i uninstalled it and tried to reinstall it would say that ndiswrapper-common is already installed, and i think i may have just missed something in the uninstall.  What commands would you put in for the uninstall?

---

### Post by ricflomag on 2007-08-03
This how-to partially works for me: sometimes, the connection is fully functional (WEP) for about 10 to 30 minutes, but then the computer freezes. Sometimes, the computer is very slow after boot, and "sudo rmmod ndiswrapper" makes it run smoothly again, but without connection of course...

I use a pretty fresh install of feisty.
Any clue ? Let me know if i have to submit more information.

---

### Post by dmizer on 2007-08-03
try booting without the card installed.  log in, then insert the card.

see if that makes any difference.  in the mean time, i'm going to install feisty on a spare machine so i can do more testing.

---

### Post by ricflomag on 2007-08-04
Thank you, but finally it seems that the card is damaged.  Sometimes it works and sometimes it doesn't.  If we take the card out, move it around, shake it, etc, it works for a few minutes.  After a few minutes, or when it heats up, it freezes the  computer.  So I decided to buy a new card.:)

---

### Post by rexy on 2007-08-16
this card works in feisty using the ndiswrapper. However the  network manager didnt connect when set to wpa. Defining the interface in /etc/network/interfaces and doing a /etc/init.d/network restart brings the interface up with wpa.

now i just gotta get it to work through network manager somehow

---

### Post by dmizer on 2007-08-17
> **rexy said:**
> now i just gotta get it to work through network manager somehow

you can try this: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) instead of network manager

---

### Post by rexy on 2007-08-18
that one didnt work either. It did detect the availeable wlans but failed to connect.

Wep worked with ndiswrapper and network manager
So i suspect network manager is just uneable to configure the card to use with wpa personal.

---

### Post by dmizer on 2007-08-18
have you configured wpa supplicant and all the required elements for getting wpa to work?  if not, see this thread: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

wpa does work with this card when driven with ndiswrapper.

---

### Post by rexy on 2007-08-20
> **dmizer said:**
> have you configured wpa supplicant and all the required elements for getting wpa to work?  if not, see this thread: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

wpa does work with this card when driven with ndiswrapper.

correct, that is the guide i followed to configure wpa with tkip.
I put the configuration in /etc/network/interfaces as directed.
I have not directly done anything with wpa_supplicant but it is running now, probably due to me configuring wpa in the interfaces file.

Doing a manual network restart will bring the interfaces up. It will not auto start however at boot or when coming out of suspend/hibernate. This because i assume networkmanager is responsible for managing the interfaces. Networkmanager just sees a static configuration and therefore does nothing.

I can remove the configuration from the interfaces file  and use network manager. It has the option to use wpa personal with a certain wlan hub, but it just fails to establish a connection or produce an error i can analyze. Setting it to WEP will just work fine.

i tried wicd as well but that program wasnt able to establish a connection using wpa either. My problem really is not that the card does not work, it's getting it to work without fixed settings so it gets configured at boot/suspend/hybernate and can be set to use separate wireless networks.

Is there anyway to make this card do WPA2 btw?

---

### Post by dmizer on 2007-08-20
well, frankly i'm not sure.  i don't have a wpa capable device for testing, but i do know that others have gotten wpa of some form to work with this card.

i know i had to disable network-manager on at least one of my systems in order to make my feisty test machine work.  you may also be successful by disabling network-manager:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```
then try connecting with wpa.  if it works, make the change permanent by creating these two text files with nothing but the word "exit" in them:
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

or you can simply uninstall network-manager.
```
sudo aptitude remove network-manager
```

you can also try alternate wireless managers.
many people have been successful with wifi-radar: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)
i've read lots of good things about wicd: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

both allow you to manage your wpa via gui.  but i'd suggest trying to disable network-manager first.

---

### Post by rexy on 2007-08-20
i have not touched networkmanager. I just added the wpa configuration to /etc/network/interfaces as directed in that wpa howto, and configured the card using the howto in this thread using ndiswrapper. That all works. 

The problem is doing it dynamicly through some network manager. Also, if network manager sees configuration in the interfaces file it appears it just does nothing, i have it running but it wont do anything anymore with the wireless connection because this is statically configured.

I'm just hoping a new version of NetworkManager is able to configure the card to use wpa better then the current one.

Also with  wicd or other types of wireless config tools dont i loose the automatic configuration and managing of networks that the network manager daemon provides?

Edit
User@Host:~$ cat /etc/network/interfaces

auto lo

iface lo inet loopback



auto wlan0

iface wlan0 inet dhcp


wpa-driver wext

wpa-ssid <SSID>

wpa-ap-scan 1

wpa-proto WPA 

wpa-pairwise TKIP

wpa-group TKIP

wpa-key-mgmt WPA-PSK

wpa-psk <wpakey>



this works, dmesg reports

[   31.288000] ndiswrapper: using IRQ 11

[   31.840000] wlan0: ethernet device 00:13:10:0a:7d:32 using NDIS driver: lstinds, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf

[   31.840000] wlan0: encryption modes supported: WEP; TKIP with WPA



lspci reports
07:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface


This on feisty on a Dell C610 lattitude. Getting it work is not the problem, getting it to automaticly configure through  network manager is. Also i'm not sure if wpa2 has to be supported or not by the card or if it's a software thing. If the latter it should be able to do it in theory right?

---

### Post by rexy on 2007-08-20
> **ricflomag said:**
> This how-to partially works for me: sometimes, the connection is fully functional (WEP) for about 10 to 30 minutes, but then the computer freezes. Sometimes, the computer is very slow after boot, and "sudo rmmod ndiswrapper" makes it run smoothly again, but without connection of course...

I use a pretty fresh install of feisty.
Any clue ? Let me know if i have to submit more information.

Did you try disabling WEP? there is no point in using wep. While it encrypts traffic anyone with the skills to capture your traffic will also be able to crack it anyway unless you change the key very frequently.

---

### Post by dmizer on 2007-08-20
> **rexy said:**
> Also with  wicd or other types of wireless config tools dont i loose the automatic configuration and managing of networks that the network manager daemon provides?

wicd features:
> Features

   1. backwards compatible with standard *nix networking commands (iwconfig, ifconfig, etc)
   2. wired networks
   3. named network profiles
   4. select between static IP addresses and DHCP on a per network basis
   5. store different static IPs, gateways, subnet masks, DNS server addresses per network
   6. wireless networks
[INDENT]1. [COLOR="Red"]automatically connect at boot[/COLOR] - no user intervention required, even for encrypted networks
2. keeps network keys in root accesible only (600) files (unencrypted, however)
3. automatically selects between static IP addresses and DHCP on a per network basis
4. encryption (template based)
[INDENT]1. WPA 1/2
2. WEP
3. LEAP
4. TTLS
5. EAP
6. PEAP [/INDENT][/INDENT]
   7. automatically connects at resume from suspend
   8. displays information about the network 

using wicd will allow you to configure your connection dynamically through a gui manager, and it will allow you to do so on boot.

sorry, i just realized i've already pointed you to wicd.  but i really do think it is your answer.  network-manager just doesn't cooperate with this card.

---

### Post by wieman01 on 2007-08-23
> **rexy said:**
> Did you try disabling WEP? there is no point in using wep. While it encrypts traffic anyone with the skills to capture your traffic will also be able to crack it anyway unless you change the key very frequently.
You can crack WEP keys within minutes. How often would you have to change the key? Every 4 - 5 minutes... Don't think that's doable. WEP should not be used at all, I agree.

---

### Post by rexy on 2007-08-24
Upgrading to WPA capeable devices is not always an option. My campus runs WEP to my knowledge and has some enterprise system where you log on to which is protected using certificates(asymmetric crypto) and which will then change keys in 5 minute intervals.

It might be less, dunno it's been awhile since i recently checked, but for all intents 
and purposes 5 minute intervals are fine since, going off the top of my head here , you need a substantial amount of data in order to get the right packets to deduce the wep key

Edit   the campus setting was  wpa-eap TTLS so i suppose they switched to wpa as well.

---

### Post by ffadmraven on 2007-11-11
Hi,

I just followed this for Gutsy, and it worked.  Just thought you would like to know.

---

### Post by dmizer on 2007-11-11
@ffadmraven,

thanks for the update.  i had already tested gutsy myself but hadn't updated the howto because i was waiting for verification.  i'll update the howto now.

thanks again!

---

### Post by lmarr28 on 2007-11-16
I can also confirm that this works with Gutsy.
I spent a few days trying to get my WPC54G V2 working with the info in a few other tutorials, but this is the only one that actually got it to work!

_Here's one problem I ran into that you may want to add to this article (for newbies to Linux like me):_
Prior to using this tutorial, if you have unsuccessfully used any other tutorials that involve ndiswrapper, you may need to remove the old drivers from ndiswrapper before this tutorial will work.  

In one of the other tutorials that I had tried, it had me load some different drivers into ndiswrapper.  Unfortunately, they were also named "lsbcmnds.inf" and "LSTINDS.INF".  So, when I tried to load the new Linksys drivers from this tutorial, ndiswrapper responded by telling me that they were already installed.  And, because the drivers that were already loaded were the wrong ones, I couldn't get it to work.

I tried uninstalling and reinstalling the ndiswrapper package, but that apparently does not remove the old drivers (took me a while to figure that one out).  After reinstalling the ndiswrapper package, it still kept telling me that I already had the drivers installed, but it still wouldn't work.

I found out that there were two directories created by ndiswrapper for the old drivers, but unfortunately, I can't remember exactly where the were located (I'm VERY new to Linux, and I don't have access to my Gutsy laptop at the moment).  I want to say they were something like:
```
/etc/ndiswrapper/lsbcmnds

/etc/ndiswrapper/lstinds
```

I removed the "old" drivers from ndiswrapper using the following commands:
```
sudo ndiswrapper -e lsbcmnds
sudo ndiswrapper -e lstinds
```

After doing that, I checked /etc/ndiswrapper, and the two directories were gone!  I could now load the new drivers per this tutorial:
```
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper
```

Finally, running "**ndiswrapper -l**" confirmed that they were installed and my WPC54G was working!

Once again, I'm VERY new to Linux, so if any of the above commands and/or directory paths are incorrect, I apologize.  You get the point though...  Before installing the drivers from this tutorial, I had to remove the two directories for the "old" drivers from the other tutorial.

Hope this helps! :)

---

### Post by dmizer on 2007-11-18
> **lmarr28 said:**
> Here's one problem I ran into that you may want to add to this article (for newbies to Linux like me)

thanks for the input.  included a link to your post in the howto. :)

---

### Post by blazerte on 2008-02-18
Thanks for this howto. Got it working with this and the WPA howto you mentioned earlier. 

Would just like to stress how important all those wpa parameters are for the wpa setup. There's a bunch of them that I've never had to use before (from the WPA howto):

wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"]

With a newer, WPA2 compatible wlan chipset, all I put in are the wpa-driver, ssid and psk lines. But the wpc54g v2 would NOT connect until every single one was in my network/interfaces file. Fussy, fussy; but at least it's working now.

---

### Post by dmizer on 2008-02-18
glad to know it helped. :)

---

### Post by irlandes on 2008-02-19
After going through this entire sequence very carefully, with no luck, and more work and study, I finally learned that Kubuntu 7.04 and 7.10 have native support for acx111 chips, including the Linksys WPC54G v. 2 card.

First, I removed all the modules and ndiswrapper.

Then I downloaded Wireless Assistant:

sudo apt-get install wlassistant <enter>

Then, I invoked it in a konsole terminal:

sudo wlassistant <enter>

When the wl window came up, it showed all local routers, and my son's was shown as connected, but wasn't.  I disconnected it, and when I connected again, it asked for WEP key, and I was on.

On the new 7.10 installation, I simply installed wlassistant and when I gave it the key, it was also on.

So, if anyone has Kubuntu, it has native support, but you may need to use wlassistant on some machines.

---

### Post by dmizer on 2008-02-19
this card has actually had native support since dapper.  problem is that the native support is buggy, as i mentioned in the howto.  i know that this howto works with kubuntu 7.10 as i tested it myself.  sorry you couldn't get it to work.

---

### Post by blazerte on 2008-02-22
Also the native acx111 drivers don't support the more advanced WPA encryption.
WEP works but isn't much.

But the acx111 driver's sourceforge site: [http://sourceforge.net/project/showfiles.php?group_id=75380]("http://sourceforge.net/project/showfiles.php?group_id=75380") does have some very new builds that are supposed to support WPA and the new kernel mac80211 stack. I tried them but couldn't even get them to compile, so they seem to be a work in progress. Maybe some day ...

---

### Post by dmizer on 2008-02-22
> **blazerte said:**
> Thanks for this howto. Got it working with this and the WPA howto you mentioned earlier. 

Would just like to stress how important all those wpa parameters are for the wpa setup. There's a bunch of them that I've never had to use before (from the WPA howto):

wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"]

With a newer, WPA2 compatible wlan chipset, all I put in are the wpa-driver, ssid and psk lines. But the wpc54g v2 would NOT connect until every single one was in my network/interfaces file. Fussy, fussy; but at least it's working now.

thanks blazerte, i just added your notes to the howto.

---

### Post by blazerte on 2008-03-05
ndiswrapper is currently not working with kernel V2.6.25 and there's some question as to whether it will be fixed:
[http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL]("http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL")

Another reason to in the future only buy wireless chipsets with free/open drivers built into the kernel. Luckily, they're becoming more common.

---

### Post by dmizer on 2008-03-05
a patch has been submitted.  at worst, the patch can be applied manually.

edit:
and linus just signed off on the change to allow continuing ndiswrapper functionality:
[http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.25-rc4](http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.25-rc4)

---

### Post by nihiilist on 2008-04-22
I cannot thank you enough.  I have been trying for 2 weeks to get my card to work in Ubuntu.  I had no luck at all until I found this post.  It's been working for a few days now.

Thank you


edit:  Whenever I reboot I have to run this command to get my internet working again  <sudo /etc/init.d/networking restart> I followed this totorial to load ndiswrapper at boot but i still need to restart.  I added the command to my sessions so it runs on bootup which solves the problem but is there a more "elegant" way to do this?

---

### Post by dmizer on 2008-04-26
> **nihiilist said:**
> edit:  Whenever I reboot I have to run this command to get my internet working again  <sudo /etc/init.d/networking restart> I followed this totorial to load ndiswrapper at boot but i still need to restart.  I added the command to my sessions so it runs on bootup which solves the problem but is there a more "elegant" way to do this?

most likely, all you need to do is disable NetworkManager.  take a look here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

---

### Post by nihiilist on 2008-04-26
OK my card worked great under Gutsy but after I installed Hardy it no longer works.  I tried an upgrade from a working system and a fresh install.  ndiswrapper -l looks fine but when I run the  sudo /etc/init.d/networking restart command I get this error


 * Reconfiguring network interfaces...                                          
ioctl[SIOCSIWPMKSA]: Invalid argument


any ideas on what I can check?  Let me know what you want to see the output of.

---

### Post by dmizer on 2008-04-26
i suspect that your /etc/modprobe.d/blacklist has been overwritten in the upgrade, and you'll merely need to reblacklist the acx module. but let's see what we can find.

post the output of:
```
sudo lshw -C Network
```
and this:
```
lsmod
```

---

### Post by nihiilist on 2008-04-26
I had the exact problem when I loaded Hardy from scratch so I don't think it is a problem from the upgrade.  I have gone back to Gutsy for the time being, I will load the live cd tomorrow and play around.

Does anyone have an ACX111 card working in Hardy?

---

### Post by dmizer on 2008-04-28
since i no longer have this card in my posession, i can't test it against hardy.  however, i do still intend to support this thread.

anyone else with hardy having trouble with this card?
anyone else able to get this card working in hardy?

---

### Post by Ciridan on 2008-04-29
Hello

First post from a newbie and my first complete install (not run CD this time).

I have this Linksys card but it did not work with Gutsy and now does not work with Hardy.

I have only tried to boot up but as this long thread of tears shows it does not work "out of the box".

If you folks want to walk me through it, I'm happy to give it a try.

Where to we start?

---

### Post by dmizer on 2008-04-29
Ciridan,
i have several machines running this card according to this howto under gutsy, so i'm not sure why it was not working for you.

please post the output of:
```
lshw -C network
```

---

### Post by Ciridan on 2008-04-29
Hi

Thanks for the offer.  I'm not at that machine at the minute.  I'll send the output as soon as I'm back to the machine.

About probably 8 hrs from now.

---

### Post by Ciridan on 2008-04-29
Hi

I think I did it correctly however when I open Network it still only shows the wired connection and modem.  Did I miss something?  There is no wireless shown.  The output of the command you sent is as follows:

 sudo lshw -C network
PCMCIA       
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:2c:57:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.106 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 3
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64

Also this is the result at ndiswrapper load


 ndiswrapper -l
lsbcmnds : driver installed
lstinds : driver installed
	device (104C:9066) present (alternate driver: acx)

---

### Post by dmizer on 2008-04-29
sorry it took so long to get back to you, i was too tired to wait up for your reply.

please post the output of:
```
cat /etc/modules
```
and
```
lsmod
```

---

### Post by Ciridan on 2008-04-29
Hi

Thanks for the help!  I really appreciate it!

First one:

```
-Ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
```

Second one (long)
```

Ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
snd_es1968             30592  2 
gameport               16008  1 snd_es1968
snd_ac97_codec        101028  1 snd_es1968
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_es1968,snd_pcm
snd_mpu401_uart         9728  1 snd_es1968
irtty_sir               9728  0 
sir_dev                17412  1 irtty_sir
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
irda                  203068  2 irtty_sir,sir_dev
crc_ccitt               3072  1 irda
evdev                  13056  5 
snd_seq_dummy           4868  0 
serio_raw               7940  0 
psmouse                40336  0 
container               5632  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
snd                    56996  16 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
button                  9232  0 
soundcore               8800  1 snd
pcspkr                  4224  0 
i2c_piix4               9612  0 
radio_maestro           8960  0 
videodev               29440  1 radio_maestro
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev
i2c_core               24832  1 i2c_piix4
yenta_socket           27276  3 
compat_ioctl32          2304  1 radio_maestro
shpchp                 34452  0 
rsrc_nonstatic         13696  1 yenta_socket
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  1 intel_agp
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  2 
floppy                 59588  0 
uhci_hcd               27024  0 
libata                159344  3 ata_generic,pata_acpi,ata_piix
e100                   37388  0 
mii                     6400  1 e100
usbcore               146028  3 ndiswrapper,uhci_hcd
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

---

### Post by dmizer on 2008-04-29
try this:

remove any usb peripherials you're making use of.  then run this command
```
sudo modprobe -r uhci_hcd
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

post any output, and see if that makes the card available in networking.

---

### Post by Ciridan on 2008-04-29
Hi

this notebook does not have anything plugged into any of its USB ports.

No output from any of the commands

Network still only shows Wired and Modem connections.

I was reading another post which seemed to indicate that if it said UNCLAIMED it indicated a problem with the driver.

When I followed the instructions, the only thing that was different was it could not find the version 1.8 and I had to use 1.9 because it could find it.  I don't know if this makes any difference.

Thanks  - I really appreciate the help!

The fact the card showed up on the list earlier I assume is a good sign and is a rough indication it is working?

Thanks

---

### Post by dmizer on 2008-04-29
try this ...

shut down the computer.
remove both the wired, and the wireless pcmcia adapters.
start the computer.
insert the linksys wireless adapter (do not insert the wired adapter).

see if that makes it become available.  there could be a conflict between the pcmcia adapters.

---

### Post by Ciridan on 2008-04-29
Hi

I know the list I sent you before, shows the wired ethernet as a PCMCIA type....but it is not - or not removeable anyway.  The machine is a compaq Armada E500.  The cat5 connector comes out the side of the machine case.

I'm trying a re-boot with the card out and then will insert it back in.  I don't know if it will help but it feels like I'm doing something constructive!

Just about to try it.

---

### Post by Ciridan on 2008-04-29
Hi

Didn't work - nothing is any different from previously reported.

Sorry but I have to call it a night - work in the morning.

I really appreciate all your help.

If there is anything else to try, I'm game but it will likely be about 20 hrs or so until I can get back to the machine itself.  I will be on line but just not at the machine.  

Again - Thanks for your assistance!  I don't know how / where to click the icon to send "thanks"  How do you do it so I can send back my appreciation!

---

### Post by Ciridan on 2008-04-29
Found the little medal icon!

---

### Post by dmizer on 2008-05-07
thanks for the thanks.  sorry, for the delay in my reply as i've been away on holiday.

i still really have no idea why this is not working.  sent you a pm.

---

### Post by jshuster on 2008-06-17
> **dmizer said:**
> since i no longer have this card in my posession, i can't test it against hardy.  however, i do still intend to support this thread.

anyone else with hardy having trouble with this card?
anyone else able to get this card working in hardy?

This worked like a charm under Hardy.  That's with a WPC54G v2 card, and using WPA.  Had to clear out the old drivers, and the LinkSys ftp URL has changed since the original post, but aside from that, it installed without trouble.

I got the latest drivers by manually navigating through the Linksys site.

I did have to set up the shell script to restart networking upon login.  

Thanks for writing up this post!  It saved me a bunch of time, and the cost of buying a different network card.

---

### Post by dmizer on 2008-06-17
> **jshuster said:**
> This worked like a charm under Hardy.  That's with a WPC54G v2 card, and using WPA.  Had to clear out the old drivers, and the LinkSys ftp URL has changed since the original post, but aside from that, it installed without trouble.

I got the latest drivers by manually navigating through the Linksys site.

I did have to set up the shell script to restart networking upon login.  

Thanks for writing up this post!  It saved me a bunch of time, and the cost of buying a different network card.

i'll go fix the ftp url now then.

thank you so much for your report, and glad you got it working!

edit:
humm, it seems to be working okay for me.  there ARE two driver versions available for this card, but both are still available on the linksys site at the url given in the howto ...

---

### Post by jshuster on 2008-06-17
Well, let's say I *think* it's working.  I rebooted at least once last night, and the network card connected to my router, no problem.  Shut things down, then turned in for the night.

This morning, I restarted the computer, and surprise ... no network.  Tried manually restarting the network, still no network.  Rebooted, still no network.  Started going back through forum posts for clues.  Rebooted again, just for the heck of it. Surprise -- now it works!

The system in generally configured as follows:
- Ubuntu Hardy Heron
- Using ndiswrapper
- Network Manager disabled per [this post]("https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5")
- Using WPA per [this thread]("http://ubuntuforums.org/showthread.php?t=202834")
- Using WPA1 & DHCP, ESSID broadcast enabled
- Shell script to restart networking on boot, per [same thread]("http://ubuntuforums.org/showthread.php?t=202834"), reply #2

On each reboot and network restart, I tested the network by trying to load a page in Firefox.  Checking ifconfig, the results suggested that wlan0 was present, but it wasn't able to connect to the router.  Unfortunately, I didn't have the presence of mind to save the output;  next time I will.

Can you suggest some things I can do to diagnose the problem, both when it's working and when it's not?  It may be a couple of days before I can get back to this, but I'd be happy to diagnose and post results.

dmizer, thanks again for all your help on this!  This is my daughter's computer, and she's delighted to be able to use it again!

---

### Post by dmizer on 2008-06-17
when the card does not work, please post the output of the following commands:
```
lsmod | grep acx
```
```
lsmod | grep ndiswrapper
```
```
lshw -C network
```
```
ndiswrapper -l
```
```
ifconfig
```
```
sudo iwlist wlan0 scan
```

---

### Post by jshuster on 2008-06-18
I started the computer, noted no connectivity, and started through your command sequence.  But by the time I got to the 3rd command, I noticed the machine had an IP address.  And it's worked since.

My assumption is it works fine, but sometimes is a little slow to make the connection.

I'll monitor this over the next few days to see how it behaves.  I'll report back in a week or so and let you know.

Again ... many, many thanks!

---

### Post by dmizer on 2008-06-18
> **jshuster said:**
> I started the computer, noted no connectivity, and started through your command sequence.  But by the time I got to the 3rd command, I noticed the machine had an IP address.  And it's worked since.

My assumption is it works fine, but sometimes is a little slow to make the connection.

I'll monitor this over the next few days to see how it behaves.  I'll report back in a week or so and let you know.

Again ... many, many thanks!
this is quite possible.  since you mentioned that you made use of a script in order to authenticate WPA.  could simply be a function of how long it takes your router to authenticate your WPA, which is also probably a function of network traffic as well as a variety of other things.

thanks for the update.

---

### Post by carterw65 on 2008-10-17
Hello,

I have Linksys WPC54GS Ver 2. Is this the same as the WPC54G your post is about?

Thanks!

---

### Post by dmizer on 2008-10-17
I don't think so, but to be sure, please post the output of

```
lshw -C network
```

---

### Post by poltr1 on 2009-02-12
Thank you, dmizer!  I had previously been unable to connect to any wireless network; after 60 seconds of trying, it would give up.  This happened with both Gutsy and Hardy.  After following your instructions, I was finally able to get my Linksys WPC54G v2 card to connect to a wireless network.

---

### Post by dmizer on 2009-02-12
That's fantastic! I'm glad to know that this method still works. I don't have the card in my posession anymore, but my Mom is using it on her Ubuntu laptop. Now that I know it works in Hardy, I can tell her to upgrade :)

---

### Post by golfmatchplayer on 2009-08-09
Dmizer:

thanks for the really helpful post explaning how to get this card setup. Yours is the only one that has gotten my card to work at all. 

iwlist wlan0 scan brings back positive results, however I still cant get Ubuntu 9.0.4 to connect. 

The ndiswrapper -l shows lsbcmnds and lstinds as installed. A warning is provided " All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

Same warning for the blacklist.

Any ideas?

---

### Post by dmizer on 2009-08-09
> **golfmatchplayer said:**
> Dmizer:

thanks for the really helpful post explaning how to get this card setup. Yours is the only one that has gotten my card to work at all. 

iwlist wlan0 scan brings back positive results, however I still cant get Ubuntu 9.0.4 to connect. 

The ndiswrapper -l shows lsbcmnds and lstinds as installed. A warning is provided " All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

Same warning for the blacklist.

Any ideas?

It may still be OK.

What's the output of:
```
lshw -C network
```

Does your access point have either WEP or WPA?

---

### Post by golfmatchplayer on 2009-08-10
Here;s what I get from: lshw -c network



 WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:07:a6:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:13:10:83:4b:fa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lstinds driverversion=1.53+Linksys,03/10/2004,6.0.0.18 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:4a:ef:5f:1f:f9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by golfmatchplayer on 2009-08-10
My network uses WEP 64.  FYI, with build in wireless hardware on another PC, I didn't have any trouble using the 40/128 setting and connecting

---

### Post by dmizer on 2009-08-14
Sorry, I've been in Korea on business for the last several days.

Please post the output of:
```
ndiswrapper -l
```
and 
```
sudo iwlist wlan0 scan
```

Have you tried disabling wireless security (temporarily) to see if you can get connected then?

---

### Post by golfmatchplayer on 2009-08-18
Dmizer:  sorry for the delay, here is the info you requested.

john@C840-laptop:~$ ndiswrapper -l
lsbcmnds : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
lstinds : driver installed
    device (104C:9066) present (alternate driver: acx)
john@C840-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for john: 
wlan0     Scan completed :
          Cell 01 - Address: 00:C0:49:EC:72:0C
                    ESSID:"fuzzy"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:01:F3:1C:35
                    ESSID:"fios1"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0C:41:19:58:E5
                    ESSID:"bullnet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

The last 2 entries are from my network.  Regardless of security, I can't get a connection.  The card is powered up, but link light is off.

Thanks for your help.  

Golfmatchplayer

---

### Post by dmizer on 2009-08-18
Try something like this:
```
sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 6 essid bullnet mode Managed&& sudo ifup wlan0
```
See if that gets you connected. (you may have to disable network-manager)

---

### Post by golfmatchplayer on 2009-08-19
Dmizer:

tried your code, still no go with networking turn off via Network manager.  Did you mean to uninstall Network mgr as well?

---

### Post by dmizer on 2009-08-19
You got no IP address with the above code? If I recally correctly (I no longer have this card), the link light never lit, but the card still worked.

If you're positive you're not getting connected, you might have more luck with wicd. Networking will work perfectly fine without network-manager, but it may not be as easy so if you're sincerely interested in making this card work, then by all means uninstall network-manager.

Also, are you sure the card works? Have you confirmed that it's functional in another machine?

---

### Post by golfmatchplayer on 2009-08-20
Dmizer:

1) Card working - Windows update in July 2009 stopped it from working, new updates Aug 2009, now working again. 

2) Still no go with Network Mgr.

3) Installed Wicd, and was able to get it to work, provided network was not using encryption.  I using WEP, I didn't try the others. 

Note: new users, make sure you have the linux wireless lan id; usually wlan0, as the wireless interface, not the SSID, which I did for a whlle.

4) I was able to get it to work with a most of WPA supplicant driver options, again provided there is no WEP encryption.

I can live with this, but look forward to having the security work, which I hope will get fixed in a near term update.  Hopefully someone will work on improving the "out of the box" experience for this important item. It should "just work" as they say.

Thanks for all your help.

---

### Post by jg123 on 2009-11-08
Got my D-link DWL-650+ (acx-100) to work in 9.10 using these directions, using this driver:
[ftp://ftp.dlink.com/Wireless/DWL650+/Driver/dwl650+_drivers_307.zip](ftp://ftp.dlink.com/Wireless/DWL650+/Driver/dwl650+_drivers_307.zip)

and using the AIRPLUS.INF file in the Drivers/WinXP directory.

---

### Post by sechole on 2009-11-09
I just opened a new thread explaining how to get work ACX 100/111 without ndiswrapper under kernel 2.6.31

[http://www.uluga.ubuntuforums.org/showthread.php?p=8283559#post8283559](http://www.uluga.ubuntuforums.org/showthread.php?p=8283559#post8283559)

---

### Post by savyboy24 on 2010-02-15
I can not get this to work when I go to load the driver I gett this error:

paula@dell-desktop:~/linksys$ sudo ndiswrapper -i lsbcmnds.inf
couldn't open lsbcmnds.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by dmizer on 2010-02-15
> **savyboy24 said:**
> I can not get this to work when I go to load the driver I gett this error:

paula@dell-desktop:~/linksys$ sudo ndiswrapper -i lsbcmnds.inf
couldn't open lsbcmnds.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

Please post the output of:
```
ls /home/paula/linksys
```

---

### Post by savyboy24 on 2010-02-16
Sorry, I could not seem to get this to work. I could not see what I had done or how to fix it since this was a new install I just reformatted to start from scratch. I am using version 8.04.1 LTS Dell iso updated to 8.04.4 LTS. I initially have all necessary drivers and my wpc54g ver2 card works fine, but with no WPA access. I am very new to Ubuntu. 

Do you think I can do this? 

Would this [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) link be a better fit?

I know I can get this to work with some help....there is no way I am going to switch my wireless security to WEP.  I did some work around to get my flash working on my 64 bit system so I can do some things I am just very new.

Thanks

---

### Post by dmizer on 2010-02-16
> **savyboy24 said:**
> on my 64 bit system

Unfortunately your card is quite old. What this means is that the Windows drivers for your card (the ones you use with ndiswrapper) are not compatible with 64bit systems. There are no 64bit drivers for your card in Windows (so you can't use Ndiswrapper), and the 64bit native Linux driver is not completely functional. If you want something that works with a 64bit system, you're better off doing some research and buying a new card. After all, they're not that expensive.

There is no way to get your card working with WEP in a 64bit Linux OS.

---

### Post by savyboy24 on 2010-02-16
i think I may have confused things. The wifi card in in my fiances 32  bit dell latitude. My 64 bit system is a hp and is running ok right now.  

Does this change my WPA options?

---

### Post by dmizer on 2010-02-16
> **savyboy24 said:**
> i think I may have confused things. The wifi card in in my fiances 32  bit dell latitude. My 64 bit system is a hp and is running ok right now.  

Does this change my WPA options?

The only way for you to get WPA working on this card is to use Ndiswrapper as described in this howto. Try following it again (you said you reinstalled?). If you run into problems, I'm more than happy to help.

---

### Post by savyboy24 on 2010-02-16
Ya, thanks for you support. I got frustrated and didn't know what I had or hadn't done so this was what I though was best. I am installing the medibuntu now so I can add skype and other fun stuff then tonight or tomorrow I will start working on the wpa again. I am sure I will get this working eventually. This is so mch more rewarding then just turning it on and having it work!!!!

---

### Post by savyboy24 on 2010-02-17
I am stuck!!! Also you say to download ver 2.02 so that is what i di then you say to uzip ver 2.0 so, I changed it to 2.02 so it would unzip. Was this wrong?

Here is what I did from the begining:

paula@dell-desktop:~$ sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for paula: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  linux-backports-modules-2.6.24-19-generic 
The following packages have been kept back:
  language-pack-gnome-kw language-pack-gnome-kw-base 
  language-pack-gnome-mai language-pack-gnome-mai-base 
  language-pack-gnome-pap language-pack-gnome-pap-base 
  language-pack-gnome-sa language-pack-gnome-sa-base 
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9 
0 packages upgraded, 2 newly installed, 1 to remove and 8 not upgraded.
Need to get 30.4kB of archives. After unpacking 1081kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [19.0kB]
Fetched 30.4kB in 1s (22.9kB/s)             
(Reading database ... 179411 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-19-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 179381 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ...
Setting up ndiswrapper-common (1.50-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
paula@dell-desktop:~$ cd
paula@dell-desktop:~$ mkdir linksys
paula@dell-desktop:~$ cd linksys
paula@dell-desktop:~/linksys$ wget [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip)
--12:35:36--  [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip)
           => `wpc54gv2_driver_utility_v2.02.zip'
Resolving downloads.linksysbycisco.com... 24.143.202.146, 24.143.202.162
Connecting to downloads.linksysbycisco.com|24.143.202.146|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19,045,881 (18M) [application/zip]

100%[====================================>] 19,045,881   713.31K/s    ETA 00:00

12:36:03 (710.64 KB/s) - `wpc54gv2_driver_utility_v2.02.zip' saved [19045881/19045881]

paula@dell-desktop:~/linksys$ unzip wpc54g_v2_driver_utility_v2.0.zip
unzip:  cannot find or open wpc54g_v2_driver_utility_v2.0.zip, wpc54g_v2_driver_utility_v2.0.zip.zip or wpc54g_v2_driver_utility_v2.0.zip.ZIP.
paula@dell-desktop:~/linksys$ unzip wpc54gv2_driver_utility_v2.02.zip
Archive:  wpc54gv2_driver_utility_v2.02.zip
   creating: WPC54Gv2_40826/AutoRun/
  inflating: WPC54Gv2_40826/AutoRun/borlndmm.dll  
  inflating: WPC54Gv2_40826/AutoRun/cc3250mt.dll  
  inflating: WPC54Gv2_40826/AutoRun/cc3260mt.dll  
  inflating: WPC54Gv2_40826/AutoRun/FBase.bin  
  inflating: WPC54Gv2_40826/AutoRun/LINKSYS.ICO  
  inflating: WPC54Gv2_40826/AutoRun/msvcp60.dll  
  inflating: WPC54Gv2_40826/AutoRun/PCANDIS3.VXD  
  inflating: WPC54Gv2_40826/AutoRun/PCANDIS4.SYS  
  inflating: WPC54Gv2_40826/AutoRun/PCANDIS5.SYS  
  inflating: WPC54Gv2_40826/AutoRun/SetupWizard.bin  
  inflating: WPC54Gv2_40826/AutoRun/SetupWizard.exe  
  inflating: WPC54Gv2_40826/AutoRun/SetupWizard.ini  
  inflating: WPC54Gv2_40826/AutoRun/W32N50.dll  
  inflating: WPC54Gv2_40826/AUTORUN.INF  
  inflating: WPC54Gv2_40826/bcmwl5.sys  
  inflating: WPC54Gv2_40826/Fw1130.bin  
  inflating: WPC54Gv2_40826/FwRad16.bin  
  inflating: WPC54Gv2_40826/FwRad17.bin  
  inflating: WPC54Gv2_40826/lsbcmnds.cat  
  inflating: WPC54Gv2_40826/lsbcmnds.inf  
  inflating: WPC54Gv2_40826/LSTINDS.cat  
  inflating: WPC54Gv2_40826/LSTINDS.INF  
  inflating: WPC54Gv2_40826/Lstinds4.sys  
  inflating: WPC54Gv2_40826/radio16.bin  
  inflating: WPC54Gv2_40826/radio17.bin  
  inflating: WPC54Gv2_40826/SETUP.EXE  
  inflating: WPC54Gv2_40826/tnet1130.sys  
  inflating: WPC54Gv2_40826/tnet1130x.sys  
   creating: WPC54Gv2_40826/Utility/
  inflating: WPC54Gv2_40826/Utility/data1.cab  
  inflating: WPC54Gv2_40826/Utility/data1.hdr  
  inflating: WPC54Gv2_40826/Utility/data2.cab  
  inflating: WPC54Gv2_40826/Utility/EULA.bin  
  inflating: WPC54Gv2_40826/Utility/ikernel.ex_  
  inflating: WPC54Gv2_40826/Utility/ISWizard.bin  
  inflating: WPC54Gv2_40826/Utility/ISWizard.exe  
  inflating: WPC54Gv2_40826/Utility/layout.bin  
  inflating: WPC54Gv2_40826/Utility/odService.dll  
  inflating: WPC54Gv2_40826/Utility/OdysseySDK.exe  
  inflating: WPC54Gv2_40826/Utility/Restart.exe  
  inflating: WPC54Gv2_40826/Utility/Setup.exe  
  inflating: WPC54Gv2_40826/Utility/Setup.ini  
  inflating: WPC54Gv2_40826/Utility/Setup.inx  
  inflating: WPC54Gv2_40826/Utility/setup.iss  
paula@dell-desktop:~/linksys$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
paula@dell-desktop:~/linksys$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
paula@dell-desktop:~/linksys$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
paula@dell-desktop:~/linksys$ sudo ndiswrapper -i lsbcmnds.inf
couldn't open lsbcmnds.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
paula@dell-desktop:~/linksys$

---

### Post by dmizer on 2010-02-17
It seems that linksys has their driver downloads messed up for this card. The driver for v3 is currently marked as the driver for v2.

I'll try to find a good copy and attach it, but I'm out of time at the moment. I'll try again later.

---

### Post by savyboy24 on 2010-02-18
Any luck?!?!?!!!!!

---

### Post by dmizer on 2010-02-18
> **savyboy24 said:**
> Any luck?!?!?!!!!!

Give me a few minutes. I've just woken up ;)

Haven't even had coffee yet ...

---

### Post by dmizer on 2010-02-18
Ok, try this:
```
cd ~/linksys/WPC54Gv2_40826
```
Then continue with step number 4.

---

### Post by savyboy24 on 2010-02-18
Cool thanks man. Its 6:46 in LA right now

---

### Post by savyboy24 on 2010-02-18
Pm

---

### Post by savyboy24 on 2010-02-18
Sorry, for the triple post. Do I need to remove the other one or the wrappe?

---

### Post by savyboy24 on 2010-02-18
Ok so the cards power lite is lit again!!! But I cannot figure out how to see the wireless networks in range and link to them. Here is the driver info thus far:

paula@dell-desktop:~$ ndiswrapper -l
lsbcmnds : driver installed
lstinds : driver installed
    device (104C:9066) present (alternate driver: acx)
What now.

---

### Post by dmizer on 2010-02-18
> **savyboy24 said:**
> Ok so the cards power lite is lit again!!! But I cannot figure out how to see the wireless networks in range and link to them. Here is the driver info thus far:

paula@dell-desktop:~$ ndiswrapper -l
lsbcmnds : driver installed
lstinds : driver installed
    device (104C:9066) present (alternate driver: acx)
What now.

You should now be able to use NetworkManager (the little networking icon in your task bar) to connect to wireless networks. Otherwise, you might consider installing wicd, which seems to work better with this card.

---

### Post by savyboy24 on 2010-02-18
Thank you so much you are a  genius!!!! I am an idiot I was right clicking and wondering why I copuld not find the networks. I am still a Windows user new to Ubuntu. Now that my fiance's computer is set up with Ubuntu properly I can get back to tweaking Karmic on mines.

Thanks Again

---

### Post by RR-GraphixGuy on 2010-02-19
> **savyboy24 said:**
> I am stuck!!! Also you say to download ver 2.02 so that is what i di then you say to uzip ver 2.0 so, I changed it to 2.02 so it would unzip. Was this wrong?

No, because I noticed the mismatch in file names as well in the how-to. I made sure I unzipped the file that was downloaded. (Make sure that the file name downloaded is the file name used in the unzip command... I think you got it right below...)

> **savyboy24 said:**
> Here is what I did from the begining:

<snip>

paula@dell-desktop:~$ sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
paula@dell-desktop:~/linksys$ unzip wpc54g_v2_driver_utility_v2.0.zip
unzip:  cannot find or open wpc54g_v2_driver_utility_v2.0.zip, wpc54g_v2_driver_utility_v2.0.zip.zip or wpc54g_v2_driver_utility_v2.0.zip.ZIP.
paula@dell-desktop:~/linksys$ unzip wpc54gv2_driver_utility_v2.02.zip
Archive:  wpc54gv2_driver_utility_v2.02.zip
   creating: WPC54Gv2_40826/AutoRun/
  inflating: WPC54Gv2_40826/AutoRun/borlndmm.dll  
  inflating: WPC54Gv2_40826/AutoRun/cc3250mt.dll  
  inflating: WPC54Gv2_40826/AutoRun/cc3260mt.dll  
  inflating: WPC54Gv2_40826/AutoRun/FBase.bin  
  inflating: WPC54Gv2_40826/AutoRun/LINKSYS.ICO  
  inflating: WPC54Gv2_40826/AutoRun/msvcp60.dll  
  inflating: WPC54Gv2_40826/AutoRun/PCANDIS3.VXD  
  inflating: WPC54Gv2_40826/AutoRun/PCANDIS4.SYS  
  inflating: WPC54Gv2_40826/AutoRun/PCANDIS5.SYS  
  inflating: WPC54Gv2_40826/AutoRun/SetupWizard.bin  
  inflating: WPC54Gv2_40826/AutoRun/SetupWizard.exe  
  inflating: WPC54Gv2_40826/AutoRun/SetupWizard.ini  
  inflating: WPC54Gv2_40826/AutoRun/W32N50.dll  
  inflating: WPC54Gv2_40826/AUTORUN.INF  
  inflating: WPC54Gv2_40826/bcmwl5.sys  
  inflating: WPC54Gv2_40826/Fw1130.bin  
  inflating: WPC54Gv2_40826/FwRad16.bin  
  inflating: WPC54Gv2_40826/FwRad17.bin  
  inflating: WPC54Gv2_40826/lsbcmnds.cat  
  inflating: WPC54Gv2_40826/lsbcmnds.inf  
  inflating: WPC54Gv2_40826/LSTINDS.cat  
  inflating: WPC54Gv2_40826/LSTINDS.INF  
  inflating: WPC54Gv2_40826/Lstinds4.sys  
  ...
..
<snip>

paula@dell-desktop:~/linksys$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
paula@dell-desktop:~/linksys$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
paula@dell-desktop:~/linksys$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
paula@dell-desktop:~/linksys$ sudo ndiswrapper -i lsbcmnds.inf
couldn't open lsbcmnds.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
paula@dell-desktop:~/linksys$

I also did the same thing. Notice that when the zip expanded, it created a new folder called WPC54Gv2_40826 and put a whole bunch of stuff inside of that. I was able to continue the couple of steps after unzipping by changing to that directory. 

```
cd WPC54Gv2_40826
```Then continue as normal. I just barely finished this how-to to get a WPC54Gv2 to work as a stand in on a Compaq Presario M2000. Works great and I am posting this now through it. 

I have been fighting issues in 32-bit Karmic with the internal wireless adapter, which is the good ol' Intel 2200BG Calexico2. This Linksys will stand in for now until I find a satisfactory answer to the ipw2200 issue on this machine.

---

### Post by dmizer on 2010-02-19
> **RR-GraphixGuy said:**
> No, because I noticed the mismatch in file names as well in the how-to. I made sure I unzipped the file that was downloaded. (Make sure that the file name downloaded is the file name used in the unzip command... I think you got it right below...)



I also did the same thing. Notice that when the zip expanded, it created a new folder called WPC54Gv2_40826 and put a whole bunch of stuff inside of that. I was able to continue the couple of steps after unzipping by changing to that directory. 

```
cd WPC54Gv2_40826
```Then continue as normal. I just barely finished this how-to to get a WPC54Gv2 to work as a stand in on a Compaq Presario M2000. Works great and I am posting this now through it. 

I have been fighting issues in 32-bit Karmic with the internal wireless adapter, which is the good ol' Intel 2200BG Calexico2. This Linksys will stand in for now until I find a satisfactory answer to the ipw2200 issue on this machine.

I've updated the howto with the correct file names and directories. Linksys keeps updating their driver for this card and it's difficult to keep track of sometimes. :)

---

### Post by savyboy24 on 2010-03-22
Things have been going good till as of recent. On that comp with Ubuntu 8.04LTS doing what we said the internet now keeps disconnecting by itself. Once you reconnect it is fine. Average internet use about 12-16 hrs a day (taking lots of practice tests). Any ideas?

THANKS!!!!!

---

### Post by dmizer on 2010-03-22
> **savyboy24 said:**
> Things have been going good till as of recent. On that comp with Ubuntu 8.04LTS doing what we said the internet now keeps disconnecting by itself. Once you reconnect it is fine. Average internet use about 12-16 hrs a day (taking lots of practice tests). Any ideas?

THANKS!!!!!

When was the last time you rebooted your router? If it's been a while, please reboot the router and see if that improves things.

---

### Post by savyboy24 on 2010-03-22
Ok will try that again. This only happens on the comp with the WPC card in it. My other comp running of the same comp has no problems. If using bit torrents could a high download speed block out other comps?

---

### Post by doubtful wisdom on 2010-04-14
Running Xbuntu Lucid on an old Dell C600 and am pleaded to report that the install went well and this thank you is posted via an operating w\WPC54Gv2 card.  Thank you for your efforts on our behalf.

---

### Post by HumN on 2010-05-04
I'm trying to get my wpc54g working with Lucid Lynx on an old Compaq Armada laptop. I tried the steps at the beginning of the thread, but it didn't work. Once I got to the point of loading the driver into ndiswrapper, I just got a prompt with no response indicating that anything was happening.

Anyone have any insights?

Thanks!

---

### Post by dmizer on 2010-05-05
> **HumN said:**
> I'm trying to get my wpc54g working with Lucid Lynx on an old Compaq Armada laptop. I tried the steps at the beginning of the thread, but it didn't work. Once I got to the point of loading the driver into ndiswrapper, I just got a prompt with no response indicating that anything was happening.

Anyone have any insights?

Thanks!

Please post the output of:
```
lshw -C network
```

---

### Post by poltr1 on 2010-05-05
Just a quick note that I tried this procedure as written on lucid, and it appears to work OK.  This was on a system that was upgraded from hardy.  I added the following steps to remove the old drivers before installing the new drivers with sudo ndiswrapper -i ...: 
```

sudo ndiswrapper -l
sudo ndiswrapper -r lsbcmds
sudo ndiswrapper -r lstinds

```

I also noticed that when I ran modprobe, I received the following warning messages on four files in /etc/modprobe.d:  WARNING: All config files need .conf: /etc/modprobe.d/...; it will be ignored in a future release.

---

### Post by HumN on 2010-05-12
> **dmizer said:**
> Please post the output of:
```
lshw -C network
```

Here it is:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:4a:b5:aa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:41280000-41280fff ioport:3400(size=64) memory:41100000-4111ffff memory:30100000-301fffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:24020000-24021fff memory:24000000-2401ffff
edwin@edwins-craptop:~$

---

### Post by poltr1 on 2010-10-01
Cisco changed the location of their drivers for this card.  It can now be downloaded at [http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip]("http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip").

---

### Post by dmizer on 2010-10-02
> **poltr1 said:**
> Cisco changed the location of their drivers for this card.  It can now be downloaded at [http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip]("http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip").
Thanks for the update. I will change the URL in the tutorial once I get home.

---

