---
title: "Best WiFi USB Dongle"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by grish on 2012-12-30
I wonder what the best wifi usb dongle for ubuntu is.

I have the [Edimax 7811un]("http://www.edimax.com/en/produce_detail.php?pd_id=347") and now finally got it to work, had a lot of problems with it and I needed some hours of help from a friend who is a really experienced linux user.

Which WiFi USB Dongle do you guys use?

Any recommendations for the future?

---

### Post by The Spectre on 2012-12-30
> **grish said:**
> I wonder what the best wifi usb dongle for ubuntu is.

I have the [Edimax 7811un]("http://www.edimax.com/en/produce_detail.php?pd_id=347") and now finally got it to work, had a lot of problems with it and I needed some hours of help from a friend who is a really experienced linux user.

Which WiFi USB Dongle do you guys use?

Any recommendations for the future?

I am actually using that very same one.

But I didn't have any problems at all with it, I just plugged it in and it worked.

What version of Ubuntu are you running?

---

### Post by grish on 2012-12-30
> **The Spectre said:**
> I am actually using that very same one.

But I didn't have any problems at all with it, I just plugged it in and it worked.

What version of Ubuntu are you running?

Running 12.04.1 LTS.

I just could never really connect to the router, ubuntu kept on asking me for a PSK.

Now it works though, thanks to a friend who helped me through IRC.

Which version are you using?
EDIT: Ah, 12.10, had that before, didn't work either.

---

### Post by The Spectre on 2012-12-30
> **grish said:**
> Running 12.04.1 LTS.

I just could never really connect to the router, ubuntu kept on asking me for a PSK.

Now it works though, thanks to a friend who helped me through IRC.

Which version are you using?
EDIT: Ah, 12.10, had that before, didn't work either.

I am Running Ubuntu 12.10 but I have also updated the Linux Kernel whenever there is a new release.

A lot of hardware is supported by the Linux Kernel and eliminates the need to install Drivers...  

[http://kernelnewbies.org/Linux_3.5_DriverArch](http://kernelnewbies.org/Linux_3.5_DriverArch)

[http://kernelnewbies.org/Linux_3.6_DriverArch](http://kernelnewbies.org/Linux_3.6_DriverArch)

[http://kernelnewbies.org/Linux_3.7_DriverArch](http://kernelnewbies.org/Linux_3.7_DriverArch)

Also make sure you have the latest Firmware for you router installed.

---

### Post by Lila7714 on 2012-12-30
I have the trendnet tew-424ub and it works great. I just plugged it in and it was good to go:p.

---

### Post by grish on 2012-12-30
Router firmware is the latest.

Which kernel would you recommend me to install?

I have 3.2.0-35-generic-pae at the moment.

---

### Post by lancest on 2012-12-30
What a coincidence.
On it now.

 TP-Link TL-WN322G v3 / TL-WN422G v2 802.11g [Atheros AR9271]

Works OFTB on 12.10 Ubuntu/Mint 14 (or even Fedora 18).
A pleasure on Linux.

---

### Post by grish on 2012-12-30
> **lancest said:**
> What a coincidence.
On it now.

 TP-Link TL-WN322G v3 / TL-WN422G v2 802.11g [Atheros AR9271]

Works OFTB on 12.10 Ubuntu/Mint 14 (or even Fedora 18).
A pleasure on Linux.

Might order that one if mine keeps causing problems.

I already had the windows DVD in my hand earlier, but I thought "nah, this can't be it." so I kept on rebooting until it worked.

My netbook, running ubuntu 12.04 as well has an atheros wlan chip too, never caused problems.

---

### Post by The Spectre on 2012-12-30
> **grish said:**
> Router firmware is the latest.

Which kernel would you recommend me to install?

I have 3.2.0-35-generic-pae at the moment.

If you got everything working now I wouldn't worry about upgrading the Linux Kernel and just leave well enough alone.

---

### Post by The Spectre on 2012-12-30
> **grish said:**
> Might order that one if mine keeps causing problems.

I already had the windows DVD in my hand earlier, but I thought "nah, this can't be it." so I kept on rebooting until it worked.

My netbook, running ubuntu 12.04 as well has an atheros wlan chip too, never caused problems.

I guess you are still having problems?

This is how I updated to the latest Linux Kernel...
[http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html](http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html)

Have you installed any Proprietary ATI or NVIDIA Drivers?

Sometimes the Kernel Updates don't get along with Proprietary Video Card Drivers.

---

### Post by grish on 2012-12-30
> **The Spectre said:**
> I guess you are still having problems?

This is how I updated to the latest Linux Kernel...
[http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html](http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html)

Have you installed any Proprietary ATI or NVIDIA Drivers?

Sometimes the Kernel Updates don't get along with Proprietary Video Card Drivers.

I am not having problems right now, using it for 5 and a half hours now and it works fine.

A little bit afraid to reboot though but I think I will do it soon.

And if I have problems then, I let it be for tonight and chill in bed with my netbook.

I have the 'current' nvidia driver installed.

---

### Post by The Spectre on 2012-12-31
> **grish said:**
> I am not having problems right now, using it for 5 and a half hours now and it works fine.

A little bit afraid to reboot though but I think I will do it soon.

And if I have problems then, I let it be for tonight and chill in bed with my netbook.

I have the 'current' nvidia driver installed.

Hopefully everything will continue to work properly.

If not and you decide to Update your Linux Kernel you might want to uninstall the NVIDIA Proprietary Driver to play it safe.

I used to have the ATI Proprietary Video Card Driver installed and when I first did the Linux Kernel update it booted to a Black Screen and when I uninstalled the ATI Proprietary Video Card Driver everything worked properly.

Since then I have never bothered with the ATI Proprietary Video Card Drivers again and have done many Linux Kernel Updates without any problems.

Unless you need some advanced Settings or Options that are in the NVIDIA Proprietary Video Card Driver you might be better of using the Native Linux Kernel Driver.

If for some reason your computer has problems after the Linux Kernel Update all you have to do is power on your Computer and hold down the SHIFT key to bring up the Grub boot menu then select the previous Linux Kernel to boot from then you can Purge the Linux Kernel so it wont try to Boot from it again.

---

### Post by grish on 2013-01-01
> **The Spectre said:**
> Hopefully everything will continue to work properly.

If not and you decide to Update your Linux Kernel you might want to uninstall the NVIDIA Proprietary Driver to play it safe.

I used to have the ATI Proprietary Video Card Driver installed and when I first did the Linux Kernel update it booted to a Black Screen and when I uninstalled the ATI Proprietary Video Card Driver everything worked properly.

Since then I have never bothered with the ATI Proprietary Video Card Drivers again and have done many Linux Kernel Updates without any problems.

Unless you need some advanced Settings or Options that are in the NVIDIA Proprietary Video Card Driver you might be better of using the Native Linux Kernel Driver.

If for some reason your computer has problems after the Linux Kernel Update all you have to do is power on your Computer and hold down the SHIFT key to bring up the Grub boot menu then select the previous Linux Kernel to boot from then you can Purge the Linux Kernel so it wont try to Boot from it again.

Installed the new kernel, didnt do anything for me, how do I make GRUB boot my old kernel automatically/remove the new one?

---

### Post by davidtrounce on 2013-01-01
USB is always going to be slower and perhaps less reliable because it  simply can't contain all the technology it needs to for a good all round  experience. If you are just wanting something to get a few tasks done,  its a good option and runs well with Ubuntu.

---

### Post by CaptainMark on 2013-01-01
The title implies you are looking for a new wifi dongle correct? If you are I recommend the [_Alfa awus036n series here_]("http://www.ebay.com/itm/ALFA-AWUS036NEH-1W-WIRELESS-802-11n-WiFi-USB-Adapter-/290514651375?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item43a405c8ef"), I bought one on the recommendation of a friend apparently they have a reputations as the hackers wifi dongle, I don't know about that but its the best wifi dongle i have ever used. Its very inexpensive compared to some OTT dongles you can get out there. It has worked with "out of the box" behaviour since I got it a few years ago, I've not yet found a linux distro that it doesn't just plug in and work on and it seems to have a huge range, I can pick up 48 networks on it compared to six on an equivilent priced netgear dongle,

---

### Post by The Spectre on 2013-01-01
> **grish said:**
> Installed the new kernel, didnt do anything for me, how do I make GRUB boot my old kernel automatically/remove the new one?

If you are not having any problems with the new Linux Kernel you are better off staying with it because of the many improvements and changes that where made.

Linux Kernel 3.7 Changes...
[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

The Kernel driver probably isn't taking over because of the Driver that you previously installed for the Edimax 7811un.

It's a bummer that you are having problems with it, all I had to do was plug it in to the USB Port and connect to my network.

Here is some additional info that I found online that might help...
[https://www.cianmcgovern.com/getting-the-edimax-ew-7811un-working-on-linux/](https://www.cianmcgovern.com/getting-the-edimax-ew-7811un-working-on-linux/)

---

### Post by grish on 2013-01-01
> **The Spectre said:**
> If you are not having any problems with the new Linux Kernel you are better off staying with it because of the many improvements and changes that where made.

Linux Kernel 3.7 Changes...
[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

The Kernel driver probably isn't taking over because of the Driver that you previously installed for the Edimax 7811un.

It's a bummer that you are having problems with it, all I had to do was plug it in to the USB Port and connect to my network.

Here is some additional info that I found online that might help...
[https://www.cianmcgovern.com/getting-the-edimax-ew-7811un-working-on-linux/](https://www.cianmcgovern.com/getting-the-edimax-ew-7811un-working-on-linux/)

Thank you a lot. And Happy New Year!!!

---

