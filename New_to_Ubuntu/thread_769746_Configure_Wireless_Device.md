---
title: "Configure Wireless Device"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-04-26
I have a Trendnet USB wireless dongle.  I plugged it in (using 7.10) and, impressively, it was detected and picked up the network.  I thought I would have to load stuff to get it to work, but it seems to be working fine.

However...

I need to have this device have a static IP number.  When I bring up System> Administration> Network, the wireless settings are grayed out.  When I turn roaming off (what is that, anyway?), I can configure settings, but it doesn't have an option to run on an unsecured network (long story, but it will be secured in the future, but for right now it has to be unsecured).

I tried editing /etc/network/interfaces as was indicated on several "hits" from Google.  The device shows up as eth1 (the internal card is eth0, but nothing attached to it), but putting in what seems to be proper settings and restarting actually seems to disable the device.

I can't static IP from the DHCP server (linksys box), so I need to do it on the machine.

Any suggestions?

Oh yeah, in case you can't tell, I am a Linux newbie.  I have a lot of experience with Windows and networking in general, so I understand the concepts, but I need to have it spelled out explicitly when it comes to Ubuntu.

Thanks in advance!

Harry

---

### Post by henrismail on 2008-04-26
Just turn off roaming and when going to the network settings leave the password blank.

---

### Post by dokdoom on 2008-04-26
Can you post your /etc/network/interfaces for me please. If you set it up correctly, everytime you wish to connect wirelessly you would just have to 

sudo /etc/init.d/networking restart

Just in case I pass out and you don't have this set up correctly enter

auto eth1
iface eth1 inet dhcp

into /etc/network/interfaces

and again, when this is done run 

sudo /etc/init.d/networking restart

---

### Post by H.Callahan on 2008-04-27
Ok, this may be my ignorance.  

When I first plugged in the dongle, it started working immediately (well after a few moment, actually) and it showed a nice little bar graph display with the signal strength in the task bar (does Ubnutu call it a task bar?).  When I opened it, I got a list of available networks that I could attach to.  Mousing over it would give a tooltip showing the strength of the currently attached AP.

When I comfigure it manaully through the System> Administration> Network dialog, all that seems to go away.  The actual connection seems to work ok.  I may have been assuming that it didn't because the icon never showed up.  Is this normal behavior?  How does one check signal strength/quality if it is normal?

Harry

---

### Post by H.Callahan on 2008-04-28
> **henrismail said:**
> Just turn off roaming and when going to the network settings leave the password blank.

That seems to have worked best.  Thanks!

Interesting sidelight to this.  Prior to doing the above, when I manually checked for updates, it said that my system was totally up-to-date.  As it was a fresh install, and 7.10 at that, I was kind of surprised, but I am a newbie, so what do I know.

Shortly after setting it up with System> Administration> Network, I got an icon telling me that there were updates available.  Opening it, there were a ton of security and other updates.  It was like the wireless connection was not really part of the system until then.  Strange...    But it seems to be working now.

---

