---
title: "Install/Uninstall Drivers?"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by kenizl86 on 2012-11-16
How do you install and uninstall drivers? And where can you get hardware drivers for Xubuntu/Ubuntu?

---

### Post by Mr_JMM on 2012-11-16
Most hardware drivers are supplied with Ubuntu, it's rare you'd need to download any.

Only ones I can think of (that it is sometimes necessary to obtain directly from manufacturer) are Nvidia, ATI, HP and wireless card. Normally the ones supplied (from repos) work perfectly well but as I say, occassionally it is required to obtain cosed-source versions from manufacturer / 3rd parties. Most recent in my case was an AMD Radeon fix to use priro version to get catalyst to work on 12.10.

What is it you need?

Ubuntu's software sources will let you know if there's an updated (if you have all repos checked) driver available.

---

### Post by audiomick on 2012-11-16
> **Mr_JMM said:**
> 
Only ones I can think of are Nvidia, ATI and wireless card.

Those ones are available via the Additional Drivers application. I think that can be found by clicking on the cog wheel icon to the right of the search box in the dash on a Unity desktop. Can't check that right now, as I am on 10.04. On pre-unity desktops, it is in system> administration

---

### Post by Mr_JMM on 2012-11-16
> **audiomick said:**
> Those ones are available via the Additional Drivers application. I think that can be found by clicking on the cog wheel icon to the right of the search box in the dash on a Unity desktop. Can't check that right now, as I am on 10.04. On pre-unity desktops, it is in system> administration

Yes, I'm well aware of that. I meant that they are the only 'common' items I could think of were a linux driver can be sourced from a manufacturer.

I'll edit my previous post to make this clearer.

---

### Post by offgridguy on 2012-11-16
> **kenizl86 said:**
> How do you install and uninstall drivers? And where can you get hardware drivers for Xubuntu/Ubuntu?

Just curious, what driver in particular you need?

---

### Post by newb85 on 2012-11-16
Drivers for peripherals, perhaps?

---

### Post by audiomick on 2012-11-17
> **Mr_JMM said:**
> Yes, I'm well aware of that...

Yes, the comment was more intended for the OP. ;)

---

### Post by El Tito on 2012-11-17
Hi. 
Prior to start, let me say I did this with modules installed in the system, but I suppose it's analogous for external ones.

*$sudo modprobe module_name* 

you can check it out with 
*$lsmod | grep module_name*

maybe this web throws light into the matter.
[http://www.thegeekstuff.com/2010/11/modprobe-command-examples/](http://www.thegeekstuff.com/2010/11/modprobe-command-examples/)

also, the nvidia/ati drivers usually come with detailed info to install (present in the description or the page).

Good luck.

---

### Post by Kevin McCready on 2012-11-17
I think I need driver (.inf?) for the wireless. I have Lubuntu 11.10 on a USB stick and when I boot into RAM onto a laptop Acer Aspire 5315 series, model ICL50 (it might have a winmodem?) the wireless doesn't work. I also tried TinyCore and Damn Small Linux and the wireless also didn't work.

---

### Post by Paqman on 2012-11-17
You won't be able to install drivers on a USB stick if it's a Live session, only if you've actually done a full install to the USB stick. If that's the case open up the tool called Software Sources and click on the tab for hardware drivers, you may find that there's a driver for your wifi available there.

---

### Post by El Tito on 2012-11-17
(@Kevin McCready) The problem is the wifi, correct?, LAN connectivity operational?
If so, let's try if [this]("http://ubuntuforums.org/showthread.php?t=2032681") works. If not we can try installing a windows driver in ubuntu ([here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")).

Give us feedback.

---

### Post by Kevin McCready on 2012-11-17
I can't find a menu item Software Sources. But under Menu, System Tools there is an option for "Windows Wireless Drivers". When I mouse hover on that it says "Ndiswrapper driver installation tool". When I click on it I get the option to install a Wireless Network Driver. A box comes up listing "Currently installed windows drivers" but nothing comes up in the listing. I can use another USB stick perhaps to put the driver on. I also noticed there is no wireless on another computer.

Perhaps the USB installation of 11.10 is not meant to support wireless?

---

### Post by El Tito on 2012-11-17
In lxde menu, preferences and then software sources.

---

### Post by Kevin McCready on 2012-11-17
Still no luck.

It looks like the Software Sources is a way of telling your current system where to get software from. I couldn't see a way of getting a specfic wireless driver and then being able to use it with another temporary USB install.

The other links for the broadcom wireless driver all assumed a permanent install. On one of the machines I'm trying to do a temporary install to (, it's a Atheros AR9285 Wireless Network Adapter (PCI Express) (rev 01)

---

### Post by Paqman on 2012-11-17
> **Kevin McCready said:**
> I couldn't see a way of getting a specfic wireless driver

What version of Xubuntu are you using? The driver tool only moved into Software Sources in 12.10. Prior to that it went by the name of Hardware Drivers or Additional Drivers.

---

### Post by Kevin McCready on 2012-11-17
Lubuntu 11.10

---

