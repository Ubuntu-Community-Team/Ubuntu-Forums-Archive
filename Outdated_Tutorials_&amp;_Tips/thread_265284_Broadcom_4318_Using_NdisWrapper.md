---
title: "Broadcom 4318 Using NdisWrapper"
date: 2006-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by brainwrecked-tech on 2006-09-25
First off, congratulations on owning one of the most notorious wireless chipsets in the Linux community.  :evil:   I take it the default bcm43xx drivers that shipped with Ubuntu didn't work for you.  Surprise.  There's tons articles written about this card on the Internet, and no one solution seems to work for everyone.  With that in mind, here's some links to other pages with solutions that did not work for me, but might for you:

[HOWTO: Broadcom 4318 Wireless Cards]("http://ubuntuforums.org/showthread.php?t=197102") - Describes how to get the card working with bcm43xx drivers.

[Stacks And Piles' Broadcom Wireless in Ubuntu Dapper 6.06]("http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/") - Uses ndiswrapper and a home-brewed script.

Those did not work for me, and after a day-and-a-half of fiddling, here's what did:

[LIST=1]
[*]Install ndisgtk and ndiswrapper-utils

```
sudo apt-get install ndisgtk ndiswrapper-utils
```

or

[INDENT]Go to System > Administration > Synaptic Package Manager, seach for *ndis*, right-click on the ndisgtk and ndiswrapper-utils packages, select Mark For Installation, and click Apply.[/INDENT]


[*]Install your wireless drivers in ndiswrapper.

```
sudo ndiswrapper -i [path-to-drivers]/bcmwl5.inf
```

or

[INDENT]The ndisgtk package is a GUI for installing Windows drivers for use in Linux using NdisWrapper.  Just go to System > Administration > Windows Wireless Drivers, click Install New Driver, click the button next to Location, and browse to the bcmwl5.inf file.  The utility will take care of installing the drivers.[/INDENT]

[*]Install ndiswrapper as module in modprobe.

```
sudo ndiswrapper -m
```

[*]Comment out eth[x] in /etc/iftab for your wireless card.

This right here was the biggest sticking point for me, and the reason my wireless card would not work.  Ubuntu recognized my wireless card, thus placing an entry in /etc/iftab for it's MAC address.  However, the drivers that ship with Ubuntu don't work for me, hence the need for NdisWrapper.    However, blacklisting the bcm43xx drivers (as described in the articles I linked to above) was not enough, because NdisWrapper insisted on using wlan0, even after changing the alias directive in /etc/modprobe.d/ndiswrapper from wlan0 to eth1.  ](*,)  The solution?

```
sudo nano /etc/iftab
```

Simply add a # at the beginning of the line that assigns a persistent name to your wireless network card.


[*]Reboot

You'll have to reboot in order for your system to drop the eth[x] interface and pick up on wlan0.


[*]Use the Network Manager in System > Administration to set up wlan0.

Now you can set up your wireless network normally with the Network Manger.
[/LIST]

I hope this helps.

---

### Post by bourne- on 2006-10-11
Do you have links to the drivers that you used?

---

### Post by brainwrecked-tech on 2006-10-15
I simply used the Windows drivers that I shipped with the laptop.  I can use either bcmwl5.inf or bcmwl5a.inf -- there doesn't seem to be an operational difference to me.

On the flip side, I've tried everu driver listed on the ndiswrapper wiki to no avail.

Now, I have yet to see any links to any Broadcom driver that specified a difference between PCI and mini-PCI.  Maybe there's a difference -- or maybe I'm barking up the wrong tree.  But there's nothing wrong with using a driver other than the ones you find linked to in the ndiswrapper wiki or in these forums.  It's just that you'll have nothing to compare to if you do.

---

### Post by bettermentflux on 2006-11-15
Thank you, this was driving me nuts. I was ping-ponging back and forth between eth1 and wlan0 without any apparent reason.

Sometimes I would boot and it would be working without any intervention. Sometimes I would boot and have to switch from eth1 to wlan0 and it would work. Sometimes the other way around.

Now everything is consistent: /etc/iftab now has a MAC entry for wlan0, and /etc/modprobe.d/ndiswrapper contains the line "alias wlan0 ndiswrapper".

One note: rather than comment out the eth1 line in /etc/iftab I changed it to reference wlan0 instead.

Thanks again.

Tags (for searches): bcm4318, ndiswrapper, eth1, wlan0, iftab, alias, modprobe.d

---

### Post by teddybairs on 2007-01-03
I know I'm late to this thread, but so far I've been pulling out all my hair. I have one of the dreaded bcm4318 cards on a Dell B130 laptop. Through a combination of machinations involving everybody's suggestions, I have finally gotten the card to recognize that the network is in fact there, but I can't seem to connect with it. I used the ndiswrapper, bcm43xx-fwcutter, blacklisting, unblacklisting, modifying iftab and interfaces by hand, and doing a lot of wishful thinking. I still can't get the kwifimanager to acknowledge that any networks are present or to tell me about the transmission strength, although the light for the card does come on and the kwifimanager does recognize that the card is present and is functional. ndiswrapper also tells me that the hardware is present for the driver.](*,) ](*,) ](*,) :confused: 

any ideas?

---

### Post by shat on 2007-01-04
That little hack did the trick for me, and I've been working on it for a good 3-4 days now myself, so thanks a bunch!  Somebody needs to roll this little tidbit into the other threads that are going about our little devil of a wireless chipset :evil:

---

### Post by teddybairs on 2007-01-05
I finally got it working! as I am writing this, I am connected wirelessly! On a BCM4318!

I figured out that for some reason ndiswrapper wasn't loading into the kernal, so I had to uninstall it, and then reinstall it again using synaptic, but just the ndiswrapper-common and ndiswrapper-utils-1.8 packages. for some reason when I upgraded from dapper to edgy, it must have caused a conflict somewhere; but when I corrected it and then manually went through the ndiswrapper_setup script (found on one of the links at the beginning of this thread) through konsole (because it wouldn't run right for some reason by itself) and rebooted, everything came up and worked.

Also, I went back to the home page for the bcm43xx driver, the reason why it doesn't work is because it has transmission power issues with bcm4318 chipset. It says it right on the website. It really only supports two of the 43xx chipsets correctly.

Oh, also I found that changing the iftab designation from eth1 to wlan0 is a necessity as well.

---

### Post by toxicfeet on 2007-01-05
Worked for me

---

### Post by VnsTech on 2010-02-14
Thanks so much! I've been working on this for two days now! :KS

---

### Post by Rekwan on 2010-03-04
I have a Broadcom 4328, so please direct me to a more appropriate thread if applicable.

The wireless card was working great in 2.6.31-19 using ndiswrapper and instructions similar to those above, however when I upgraded to 2.6.31-20 the card no longer works.  I have tried removing/reinstalling the driver, removing/reinstalling ndiswrapper common and utils-1.9, and several other things to no avail.

Also, I looked for /etc/iftab but could not find it on my system.  Perhaps this is shows part of the problem?

It seems the ndiswrapper will simply not load even though it is called as an alias for wlan0 and eth0 in the ndiswrapper.conf.  I also have ndiswrapper called in /etc/modules hoping that would help, but it doesn't.

Of note: When I upgraded, the Broadcom STA driver decided to add itself and I had to remove it in "Hardware Drivers" since it did not work either.

Any help would be greatly appreciated.

::Edit::
Never mind.  The instructions at [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) worked like a charm.  I have left this post in case someone else has my problem and the instructions may be helpful to them as well.

---

