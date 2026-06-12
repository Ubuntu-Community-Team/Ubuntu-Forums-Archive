---
title: "Wireless and touchpad problems after update"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by LuckyDingo on 2012-10-05
Hi,

I'm trying to learn to use Kubuntu on my own after leaving my mate to be honorary IT guy for far too long. It's not going so well though...

I'm using Kubuntu version 12.04, and KDE platform version 4.8.5. I'm apparently using version 0.97-29ubuntu66 of grub - not that I know what that means. The eeepc has a 32-bit intel CPU. 

I tried to run a standard software update, by clicking on the "software updates are available" icon, and clicking on install updates. I put in my password when prompted and let it run. Nothing obvious went wrong. When I returned to it it worked ok, but when I played a clip on youtube the sound was a bit alien-esque and jumpy so I restarted it to see if that would help. When it reloaded the touchpad was totally unresponsive. I attached a wireless mouse and that worked ok, but the touchpad still seems dead. The wireless also seems unresponsive - it's not even picking up which networks are available - but the eeepc works fine with a wired connection. There seem to be more updates to install (not that the first lot went well!) but when I have tried to install them (who knows, maybe it will help?) it flicks past the prompt for a password and then flashes up an Authentication error. 

I've posted on [http://www.kubuntuforums.net](http://www.kubuntuforums.net) and a very helpful guy guided me towards finding out what upgrade I ran (I'd just clicked on the updates available icon and agreed to everything), and found out that it hasn't performed a distribution upgrade and I haven't got the beta version of 12.10. He thought there was a driver issue with regards to the wifi network card and touchpad, and guided me to check for proprietery drivers for these devices... according to my computer, though, "No proprietary drivers are in use on this system". He also suggested I come here.
 
I'm a bit lost and would appreciate any help.
 
Cheers,
lisa

---

### Post by bra|10n on 2012-10-05
By chance do you have a yellow-light-globe icon showing in your system tray soon after start-up?

Also could you open a konsole and post the output of, 
*kdesudo kate /etc/apt/sources.list*

Enter your password into the popup and paste the entire contents of the file.
(Please use the code-tags (#) above as this will be quite a lengthy paste).

---

### Post by Bucky Ball on 2012-10-05
Welcome.

You do not want to go to 12.10. That would not be stable. Stick with 12.04. 

You seem to have a lot of issues going on here. Is there any chance you could stick them in point form or post a thread about each?

* Sound alien-esque (I like that word!)
* Touchpad unresponsive
* Wireless dead

... etc. 

Did you try to perform an upgrade to 12.10? Not sure that's possible without the disk. ;)

---

### Post by LuckyDingo on 2012-10-05
Hey
Thanks for the replies.

> **Bucky Ball said:**
> 
Did you try to perform an upgrade to 12.10? Not sure that's possible without the disk. ;)

I'm not trying to upgrade to 12.10 - I only mentioned it because the guy on the other forum had wondered whether the problem was because I was using the unstable beta version. I should have phrased it a bit clearer!

---

### Post by LuckyDingo on 2012-10-05
> **bra|10n said:**
> By chance do you have a yellow-light-globe icon showing in your system tray soon after start-up?

Also could you open a konsole and post the output of, 
*kdesudo kate /etc/apt/sources.list*

Enter your password into the popup and paste the entire contents of the file.
(Please use the code-tags (#) above as this will be quite a lengthy paste).

I did have. It's not there now though. 
I've done what I think you suggested and this is what it says:
```
# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://gb.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe
deb http://repository.spotify.com stable non-free
deb-src http://repository.spotify.com stable non-free

```

Not sure what any of that means though! 
Cheers

---

### Post by Bucky Ball on 2012-10-05
As for wireless, open a terminal by Applications>Accessories>Terminal (could be slightly different in Kubuntu) and paste this in:

```
sudo lshw -C network
```... hit enter and post the result back here, please. ;)

---

### Post by bra|10n on 2012-10-05
> **LuckyDingo said:**
> Hi,

I'm trying to learn to use Kubuntu on my own after leaving my mate to be honorary IT guy for far too long. It's not going so well though...

So far I think your doing better than you give yourself credit for...

Your pasted list of repositories looks fine. These are the addresses of the archives that hold all of the software required. The only thing I would suggest is making the following changes,
```
#deb http://repository.spotify.com stable non-free
#deb-src http://repository.spotify.com stable non-free
```
Make those changes and close the file.

After you have done the above you can try the following in a konsole,
```
sudo apt-get update && sudo apt-get dist-upgrade
```

You might get this far and post back any results. Keep an eye open for any errors  that output at the end.
I *expect* you will still meet with some issues however...

---

### Post by LuckyDingo on 2012-10-05
Cheers, Bucky Ball. I got the following:
  ```
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:27:6d:89
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.64 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: RT2790 Wireless 802.11n 1T/2R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fbef0000-fbefffff

```


And I'm sorry to chuck more issues into the same post again, but just in case this is useful...When looking through applications, I found a touchpad management thingummyjig. Anyway, clicking on it gave an error message: 
No touchpad found 
No Touchpad was found in this system. If the system has a Touchpad, please make sure that the Synaptics driver is properly installed and configured. 
If your Touchpad is not found, though the driver is installed and configured correctly, please compile detailed information about your Touchpad hardware and report this issue to the issue tracker.

---

### Post by LuckyDingo on 2012-10-05
> **bra|10n said:**
> 
Make those changes and close the file.


Aaah, this is where my novice-ness comes out! How do I make those changes?

---

### Post by bra|10n on 2012-10-05
> **LuckyDingo said:**
> 
On my way to following that, I found a touchpad management thingummyjig. Anyway, clicking on it gave an error message: 
No touchpad found 
No Touchpad was found in this system. If the system has a Touchpad, please make sure that the Synaptics driver is properly installed and configured. 
If your Touchpad is not found, though the driver is installed and configured correctly, please compile detailed information about your Touchpad hardware and report this issue to the issue tracker.

You will notice other system settings options have also disappeared due to the updates not completing.

All you need to do is edit the file as necessary placing the # in front of the lines I indicated. 
Save the file and then close.

---

### Post by LuckyDingo on 2012-10-05
Thanks. I've done that and... nothing's happened! What do I do next?

---

### Post by bra|10n on 2012-10-05
Did you run the konsole command after editing sources.list file?

---

### Post by bra|10n on 2012-10-05
Update?

---

### Post by LuckyDingo on 2012-10-05
Ooops, sorry, I thought I'd deleted that comment as soon as I'd realised that I'd not done it properly the first time. I did it properly, a million lines of code ran, I restarted the computer and now my touchpad is back! Fantastic, thank you.

I still can't get the wireless to work though. Any thoughts?

Thanks again

---

### Post by bra|10n on 2012-10-05
Ok first I need to get a better picture ;)

1. Are you set to autologin?
2. Please confirm Kubuntu and KDE versions.
3. Did the yellow light-globe icon make another appearance?

---

### Post by LuckyDingo on 2012-10-05
Set to autologin for the wireless? Yes - it should connect automatically. Confusingly, the laptop can now detect which networks are around, it just won't connect. I'm using Kubuntu version 12.04, and KDE platform version 4.8.5. 
I'm not sure if the icon I'm looking at is the one you mean - there's a system notification helper, which looks like a spiky yellow cartoon pow! shape, with an exclamation mark inside and is letting me know that an application has crashed on my system at some point. There's also a system notifier, which looks to me like a white cog with a padlock on top, which is letting me know that more software updates are available.

---

### Post by bra|10n on 2012-10-05
Please confirm the following;
1. You have kubuntu-restricted-extras installed.
2. You *have* ttf-mscorefonts installed.

Autologin meaning a passwordless login, i.e straight to desktop from boot.

It is good you can now see surrounding networks. We will get to that...

---

### Post by LuckyDingo on 2012-10-05
Aaah. I don't know the first two - how would I find that out? 
And no, I have a password login.

---

### Post by bra|10n on 2012-10-05
Ok. Startmenu > Applications > System > Muon package manager.
Just search the terms ttf-mscorefonts and kubuntu-restricted-extras (separately!).
You will see on the right if they are supposedly installed or not...

---

### Post by LuckyDingo on 2012-10-05
Cheers. It says they are both installed.

---

### Post by bra|10n on 2012-10-05
It says they are, but really they're not. 
Hence the cog and light-globe warning mscorefonts crashed, and your initial complaint re video rendering...

In a konsole,
```
sudo apt-get purge flashplugin-installer
```
You should notice after this is removed, mscorefonts will install automatically. After this has finished you can then run,
```
sudo apt-get install flashplugin-installer
```

Report back at this point...

---

### Post by LuckyDingo on 2012-10-05
Ooooh, I've just seen the time - I need to run for my train. I'll have to come back to this on Sunday. Thanks so much for your help! Have a great weekend.

---

### Post by LuckyDingo on 2012-10-05
Well, there was just enough time to try that... it seems to have run smoothly.
... but the train probably won't wait for me. Thanks again!

---

### Post by bra|10n on 2012-10-05
Your welcome.

After running the commands above, you will need to re-create your wireless connection. Go to manage connections, Wireless tab and click Add > Wireless.
Enter your connection details, name etc, Goto  Wireless security tab and choose WPA/WPA2 Personal. That should be it. If KWallet pops up make sure you enable its use. 
Oh, and don't forget to go back to /etc/apt/sources.list and undo your changes, save and close.

Enjoy.

Apologies, I didn't see your last post. I hope you made your train.

---

### Post by Bucky Ball on 2012-10-05
Failing that, and you may have mentioned this, have you tried the Linux driver from their website?

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

There's a couple. You might experiment.

---

### Post by LuckyDingo on 2012-10-07
Thank you so much - it's all working perfectly now. I'm stunned at how incredibly helpful and supportive you are here. Faith in humanity restored... thanks again!

(oooh, and yes, I did get my train! Cheers!)

---

### Post by bra|10n on 2012-10-07
Hey, good news all round.
Wireless working also?

---

### Post by Bucky Ball on 2012-10-07
> **LuckyDingo said:**
> Thank you so much - it's all working perfectly now.

Good news about both things. Please mark thread a solved from 'Thread Tools' to help others when/if you think it is. ;)

---

### Post by hantms on 2012-10-07
> **Bucky Ball said:**
> Good news about both things.

Excellent news; this helped me too fix the exact same problem I had after an update.  I have no idea WHY it worked though..

Note that I'm not on 12.04 but on 12.10 Beta, and not Kubuntu but regular Ubuntu.  And yet the symptoms were exactly the same after running an update late last week:  Touchpad stopped working, trackpoint mouse stopped working, Wifi stopped working too.

And yet after removing flashplugin-installer and updating and upgrading it seemed to correct itself, reconfiguring loads of packages (incl. the kernel, grub and so on) and after that it just worked.

Thing is I can't tell why.. What's the magic related to flashplugin-installer? (Which I may leave uninstalled as I mostly use Chrome)

---

### Post by bra|10n on 2012-10-08
> **hantms said:**
> 
Thing is I can't tell why.. What's the magic related to flashplugin-installer? (Which I may leave uninstalled as I mostly use Chrome)

There is no magic as you call it related to flashplugin-installer. The OP's problem arose when system-updates failed to call (or hook) the license acceptance for the ttf-mscorefonts package. And as a consequence the flash package that is installed can be rather flaky. Simply uninstalling flash then allows the remaining updates to continue, with the final step being to reinstall flash.
The problem existed in Kubuntu 12.04 due to the install-scripts calling for GTK related lib's, and not the KDE lib's. So as an Ubuntu user I have no explanation as to why you suffered the *same* issue.
Good to hear that your problems are solved though.
Cheers

---

### Post by LuckyDingo on 2012-10-08
> **bra|10n said:**
> Hey, good news all round.
Wireless working also?

Yep, wireless working. Thanks!

---

### Post by Bucky Ball on 2012-10-08
> **hantms said:**
> Excellent news; this helped me too fix the exact same problem I had after an update.  I have no idea WHY it worked though..

Note that I'm not on 12.04 but on 12.10 Beta, and not Kubuntu but regular Ubuntu.  And yet the symptoms were exactly the same after running an update late last week:  Touchpad stopped working, trackpoint mouse stopped working, Wifi stopped working too.

And yet after removing flashplugin-installer and updating and upgrading it seemed to correct itself, reconfiguring loads of packages (incl. the kernel, grub and so on) and after that it just worked.

Thing is I can't tell why.. What's the magic related to flashplugin-installer? (Which I may leave uninstalled as I mostly use Chrome)

It would be helpful if you could post a new thread with this information in the [URL="http://ubuntuforums.org/forumdisplay.php?f=416"]Ubuntu +1 Sub-Forum. ;)
[/URL]

---

