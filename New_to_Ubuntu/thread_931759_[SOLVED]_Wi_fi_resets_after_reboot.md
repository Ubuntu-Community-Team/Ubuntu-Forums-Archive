---
title: "[SOLVED] Wi fi resets after reboot"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by talsemgeest on 2008-09-27
Sorry if this is a stupid question, but I have never had to use wi-fi under ubuntu before, so I am extremely new to this.

I set everything up on my router, with wpa personal security and a nice secure password. Then I went to set it up in ubuntu, going to Administration>Network, unlocking, going to the wireless and typing in all of my stuff, and told it to use dhcp. I closed it, it did its thing and then I opened fierfox and up came google, so the wi-fi connection dows work.

However, after a reboot it changes the settings, and I cant access the internet. I have tried quite a lot of things, most of them in the ubuntu help wiki, but to absolutely no avail.

The wi-fi card is an Airlive WT-2000PCI, and when I type lspci it gives me RaLink RT2561/RT61 802.11g PCI.

All help is very much appreciated, thanks in advance. :)

---

### Post by talsemgeest on 2008-09-28
Bump

---

### Post by jualin on 2008-09-28
When you click on the "Network Applet" (next to the clock), can you see your wireless network?

---

### Post by talsemgeest on 2008-09-28
> **jualin said:**
> When you click on the "Network Applet" (next to the clock), can you see your wireless network?
No, there is only wired and manual.

---

### Post by jualin on 2008-09-28
In that case the wireless card driver is not installed, or not being loaded. I suggest you to install it using Ndiswrapper. There is a link on my signature with a good tutorial. Also there is [this thread]("http://ubuntuforums.org/showthread.php?t=564419"). Hope this helps!

---

### Post by talsemgeest on 2008-09-28
But if there was no driver, wouldn't I be unable to use wi-fi altogether? It works when I put the password and all that in there, but then after a reboot it forgets my settings.

---

### Post by ugm6hr on 2008-09-28
Habe you tried using roaming enabled?

That allows Network Manager (the applet) to control the wifi card.

That saves all your settings in the Gnome passwords.

---

### Post by talsemgeest on 2008-09-28
> **ugm6hr said:**
> Habe you tried using roaming enabled?

That allows Network Manager (the applet) to control the wifi card.

That saves all your settings in the Gnome passwords.
Yeah, I tried leaving it at that, but it gave me nothing.

---

### Post by jualin on 2008-09-28
Did you have the ethernet cord connected when you did the test of the wireless?

---

### Post by shifty_powers on 2008-09-28
could always try replacing gnome network manager with wicd...

(use it myself)

---

### Post by talsemgeest on 2008-09-28
No, I have left that unplugged the whole time, because if it wasn't I couldn't be sure that it was actually the wi-fi that was letting me access the internet.

---

### Post by james_vanb on 2008-09-28
Had similar problem.  Loaded WiFi Radar through Synaptic.  Combination of WiFi Radar and Network Manager seemed to work things out.

---

### Post by talsemgeest on 2008-09-28
> **shifty_powers said:**
> could always try replacing gnome network manager with wicd...

(use it myself)
Ok, I will give it a go.

---

### Post by shifty_powers on 2008-09-28
you will have to add the repo's to it to your sources list.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

will give you instructions how. very easy :D

---

### Post by Tom--d on 2008-09-28
This is an easy one to fix. No need for Ndiswrapper.

The problem your having is just the module (driver) is not being loaded at boot. Very simple to fix.

First thing, you need to know your wireless module's name.
Do this command in the terminal:
```
sudo modprobe rt61
```
Post the outcome (If there is any).
I think the module is rt61. or maybe rt25x0 try both. and see if wireless is working.

Then, in terminal again do this command,
```
gksu gedit /etc/modprobe.conf
```
and add your module name at the bottom on a new line. This will load it at boot.

---

### Post by talsemgeest on 2008-09-28
> **shifty_powers said:**
> you will have to add the repo's to it to your sources list.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

will give you instructions how. very easy :D
Yeah, done, and I'm trying it now.

---

### Post by talsemgeest on 2008-09-28
> **Tom--d said:**
> This is an easy one to fix. No need for Ndiswrapper.

The problem your having is just the module (driver) is not being loaded at boot. Very simple to fix.

First thing, you need to know your wireless module's name.
Do this command in the terminal:
```
sudo modprobe rt61
```
Post the outcome (If there is any).
I think the module is rt61. or maybe rt25x0 try both. and see if wireless is working.

Then, in terminal again do this command,
```
gksu gedit /etc/modprobe.conf
```
and add your module name at the bottom on a new line. This will load it at boot.
Awesome, thanks for that. I will try that, right after a quick reinstall.

---

### Post by shifty_powers on 2008-09-28
did wicd not work then?

---

### Post by Tom--d on 2008-09-28
> **talsemgeest said:**
> Awesome, thanks for that. I will try that, right after a quick reinstall.

REinstall? 
Why? There is no need!

---

### Post by talsemgeest on 2008-09-28
Well I am amazed. I just reinstalled, and everything worked. It picked up all wireless networks, and after clicking on my one and entering the password, it connected and worked.After a reboot, everything still worked. The only thing I can think of is that this time, during installation, the wired LAN was plugged in. So I'm guessing i might have downloaded another driver for the wi-fi?

Anyway, thank you all for your help. It is very much appreciated.

---

### Post by jualin on 2008-09-28
Well glad the reinstall solved your problem.

---

### Post by Tom--d on 2008-09-29
> **talsemgeest said:**
> Well I am amazed. I just reinstalled, and everything worked. It picked up all wireless networks, and after clicking on my one and entering the password, it connected and worked.After a reboot, everything still worked. The only thing I can think of is that this time, during installation, the wired LAN was plugged in. So I'm guessing i might have downloaded another driver for the wi-fi?

Anyway, thank you all for your help. It is very much appreciated.

Ah, The update broke your wireless. Probably a kernel update.

---

### Post by talsemgeest on 2008-09-29
No, I tried it from a clean install before, but no go. Now I do the install WITH internet access and then the wi-fi works, so I guess it got the stuff it needed of the internet during installation.

---

### Post by Tom--d on 2008-09-29
> **talsemgeest said:**
> No, I tried it from a clean install before, but no go. Now I do the install WITH internet access and then the wi-fi works, so I guess it got the stuff it needed of the internet during installation.

Ok.
When connected to your Wireless, right click the wireless icon and go to connection information and then go to driver: your_driver and ppost it here.

---

### Post by talsemgeest on 2008-09-29
Ok, I will do that tomorrow.

---

### Post by talsemgeest on 2008-09-29
Ok the driver listed in connection information is: RT61PCI

---

### Post by Tom--d on 2008-10-03
> **talsemgeest said:**
> Ok the driver listed in connection information is: RT61PCI

Just do this then to make sure it always loads on boot.

Press ALT+F2 and then type this in
```
gksu gedit /etc/modprobe.conf
```

and on a new line (if there is one) put rt61pci

---

### Post by talsemgeest on 2008-10-03
Ok, I will do that if I ever have any more problems like that.

Thank you for your help!

---

