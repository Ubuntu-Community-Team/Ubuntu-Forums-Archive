---
title: "[lubuntu] LXDE won't start on old laptop"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by mooklepticon on 2014-02-28
I installed Lubuntu 13.10 from a USB drive on my old Acer Aspire laptop. First, I booted to play around with it.  I liked it.  It didn't find the wifi (another issue for another day) and there were some function keys that didn't work quite right, but LXDE was nice and I could tell that the laptop was handling it well.  (Vista made the cooling fan whine like crazy and Lubuntu barely turned it on.) 
 
So I went ahead and did the full install, wiping out Vista.  I got through everything fine and then it rebooted.  I had left the USB drive in, so I selected the "Boot from first hard disk" option.  It booted straight to command line. 
 
From what I expected by using the USB drive and from what I've read, it should boot straight into LXDE.  Is that correct?  If that's what it should have done, how can I fix this? If it's supposed to boot to command line, how can I get it to boot to LXDE instead?

---

### Post by sudodus on 2014-02-28
Welcome to the Ubuntu Forums :-)

You are right, you should get the same graphics after installation as during the live session.

What graphics chip/card is it?
And what wifi chip/card is it?
Can you switch off the wifi (a mechanical switch or a setting in the BIOS menus)?

You may have problems with the graphics driver. Did you choose to install restricted drivers during the installation? Maybe if you avoid that (it can be done afterwards if you wish) and try again. If still no go, try the boot option nomodeset (after installation).

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by lykwydchykyn on 2014-02-28
If you log in at the command line and type "startx", does LXDE start up then?

---

### Post by mooklepticon on 2014-03-01
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

You are right, you should get the same graphics after installation as during the live session.

What graphics chip/card is it?
And what wifi chip/card is it?
Can you switch off the wifi (a mechanical switch or a setting in the BIOS menus)?

You may have problems with the graphics driver. Did you choose to install restricted drivers during the installation? Maybe if you avoid that (it can be done afterwards if you wish) and try again. If still no go, try the boot option nomodeset (after installation).

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
It's an Acer Aspire 4720
Graphics:
[COLOR=#000000][FONT=Verdana]Intel Graphics Media Accelerator X3100[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]8MB of dedicated system RAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Up to 350MB of shared system RAM

Wifi:
[/FONT][/COLOR]802.11b/g [1]
Acer InviLink

Can I switch off? Never tried. There's a button that looks like a radio, so I assume so.  It's on, because it'll connect to wifi in Vista.

Restricted drivers? I don't recall an option for that during installation. I would have chosen the default, I assume.

I'll try the boot option, thanks.

---

### Post by mooklepticon on 2014-03-01
Well, nevermind. It went into LXDE this time.  *scratches head* Thanks!

---

