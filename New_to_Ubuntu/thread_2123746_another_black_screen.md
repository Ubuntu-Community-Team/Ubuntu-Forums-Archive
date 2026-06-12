---
title: "another black screen"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by aussielinuxguy on 2013-03-08
Hello,

I installed Ubuntu 12.10 on my Dell Latitude D531 and when the desktop loads all it is the cursor and background. 

Have searched the threads but i`m new to all this Ubuntu. I have seen another user with the same laptop and it works for them.

Graphics Card is: ATI RS690M [ Radeon X1200 Series ] - if that is any help !

Any help appreciated.

EDITED: I found Ubuntu 10.04 LTS disk i have and installed it on a spare hard drive, and the desktop is working. ( strange )

---

### Post by Bashing-om on 2013-03-09
aussielinuxguy; Hi !
Let us presume that for what ever reason the 12.10 install is not picking up a graphics driver. Try this and advise:
As you have 2 operating systems installed when you boot you get the grub menu, ensure the 12.10 kernel is highlighted and press the "e" key for "edit"-> boot parameters, arrow down to the line similar to this; "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"; arrow across to the term "quiet splash" and insert the term "nomodeset"; ctl+x to continue to boot.
Do you now boot to the GUI login and after you authenticate do you boot to the desk top ?

Yes ? -> in software sources ensure "3rd party sources" is ticked then :
Launcher -> ubuntu Software Center -> Software sources (task bar menu option) ->Additional Drivers (tab) and install the recommended driver.[INDENT=4]
hope this helps

[/INDENT]

---

### Post by aussielinuxguy on 2013-03-09
Bashing-om,

 Thanks for the reply. I did what you said and edited the boot parameters line to nomodeset and pressed ctrl+x and continued to boot. And it did boot into the desktop and i see the icons down the left side and the taskbar/panel up the top.

Then i went into Software Center - edit - Software Sources, but can`t see 3rd party sources to tick. And there is no additional drivers to install.

Edited: i rebooted and the desktop works properly now.

---

### Post by LuisGMarine on 2013-03-09
> **aussielinuxguy said:**
> Bashing-om,

 Thanks for the reply. I did what you said and edited the boot parameters line to nomodeset and pressed ctrl+x and continued to boot. And it did boot into the desktop and i see the icons down the left side and the taskbar/panel up the top.

Then i went into Software Center - edit - Software Sources, but can`t see 3rd party sources to tick. And there is no additional drivers to install.

Edited: i rebooted and the desktop works properly now.

If you were able to boot up into a working desktop, you can alternatively install the proper drivers through the command line.  I dont' have an ATI card, but I was able to find this tutorial on how to install the proper drivers through the command line.  I hope thi helps and post back if you run into any trouble. 

[http://http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200]("http://http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200")

---

### Post by aussielinuxguy on 2013-03-10
LuisGMarine, 

Thanks for the link, but i can`t download the driver as i`m not connected to the net with that laptop yet.

So i`ll do that if i get connected with my laptop.

---

### Post by Bashing-om on 2013-03-10
aussielinuxguy;
Not sure where you presently stand. When you have 'net connectivity we will continue. Be advised that "nomodeset" option is just a temporary work-a-round as kernel mode setting is disabled. There exist the need to get you up on a decent graphics driver.[INDENT=2]standing by to assist

[/INDENT]

---

