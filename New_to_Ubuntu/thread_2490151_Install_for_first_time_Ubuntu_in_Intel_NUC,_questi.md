---
title: "Install for first time Ubuntu in Intel NUC, question for accessibility magnifier"
date: 2023-08-24
forum: New to Ubuntu
---

### Post by goldfran on 2023-08-24
Hello experts of the world!!

I hace an Intel NUC 11 Esential NUC11ATKPE with 16Gb DDR4-3200 and SSD 512Gb PCIe 3

I want to install Ubunto (or an other version... XU, KU...) for create a little home server (minecraft, antivirus, file...)

Well, I have a visual problem and need magnifier or similar app from first time. In windows use magnifier app, start with windows system and your usability is more easy (wheel mouse and press / hold alt or cntr)

Where can I use magnifier in Linux? 
Can It use similar option than windows magnifier?

Thanks!!

---

### Post by tea for one on 2023-08-24
First, make a bootable USB device to "Try Ubuntu"
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

After booting into a live session:- 
Open Settings > Accessibility
There are some options there, which should help.

---

### Post by goldfran on 2023-08-24
Ok and... Any key shortcut to activate magnifier because I don´t know that I can select this option (remember several visual problem)

---

### Post by tea for one on 2023-08-24
Super (Windows) key + Alt + 8
More info here [https://ubuntuhandbook.org/index.php/2022/06/zoom-in-out-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/06/zoom-in-out-ubuntu-2204/)

---

### Post by Holger_Gehrke on 2023-08-24
Desktop magnification  - and accessibility options in general - are different from one desktop environment to the other. The option described by tea for one is for standard Ubuntu (Gnome). In XUbuntu - which uses XFCE as it's desktop - you can hold the alt key and turn the mousewheel to zoom in and out. This is always available on XUbuntu, there isn't even an option to turn it off (well, there is a setting 'zoom_desktop' in xfconf, channel xfwm4, but not in any settings app).

Holger

---

### Post by goldfran on 2023-08-24
> **tea for one said:**
> Super (Windows) key + Alt + 8
More info here [https://ubuntuhandbook.org/index.php/2022/06/zoom-in-out-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/06/zoom-in-out-ubuntu-2204/)

Thanks I see this when install my Intel NUC server

> **Holger_Gehrke said:**
> Desktop magnification  - and accessibility options in general - are different from one desktop environment to the other. The option described by tea for one is for standard Ubuntu (Gnome). In XUbuntu - which uses XFCE as it's desktop - you can hold the alt key and turn the mousewheel to zoom in and out. This is always available on XUbuntu, there isn't even an option to turn it off (well, there is a setting 'zoom_desktop' in xfconf, channel xfwm4, but not in any settings app).

Holger

Yes I suppose, One off-topic question. for create server (using ubuntu base) how is the best desktop option? Maybe ummm Xubuntu with XFCE? I think that is more intuitive from services... and, how is the desktop similar to windows 11?

When install server, talk about it

---

### Post by Holger_Gehrke on 2023-08-24
For servers there is a special Ubuntu Server image. This has only the things a server needs, so **NO** GUI. Bugs in things that aren't even there won't bother you and can't be exploited by somebody. Why waste processor cycles, memory and storage on a GUI for a system that just sits in the corner quietly serving files, delivering answers to database queries or storing game worlds ? Of course this raises the barrier to entry a bit since administration is done from the command line and you have to learn quite a bit to get proficient in its use.

XFCE doesn't look and behave like Windows 11. I'd say it can best be compared to the Windows 7 desktop. You can find some screenshots at [xfce.org]("https://xfce.org/about/screenshots") and [xubuntu.org]("https://xubuntu.org/screenshots/"). Be advised that XFCE is **very** configurable. You can have multiple panels (I currently have three, but one is only visible if I have both display active since it only holds two shortcuts for controlling the other display through DDC/CI) and there are many plugins you can put on those.

Holger

---

### Post by goldfran on 2023-08-25
> **Holger_Gehrke said:**
> For servers there is a special Ubuntu Server image. This has only the things a server needs, so **NO** GUI. Bugs in things that aren't even there won't bother you and can't be exploited by somebody. Why waste processor cycles, memory and storage on a GUI for a system that just sits in the corner quietly serving files, delivering answers to database queries or storing game worlds ? Of course this raises the barrier to entry a bit since administration is done from the command line and you have to learn quite a bit to get proficient in its use.

XFCE doesn't look and behave like Windows 11. I'd say it can best be compared to the Windows 7 desktop. You can find some screenshots at [xfce.org]("https://xfce.org/about/screenshots") and [xubuntu.org]("https://xubuntu.org/screenshots/"). Be advised that XFCE is **very** configurable. You can have multiple panels (I currently have three, but one is only visible if I have both display active since it only holds two shortcuts for controlling the other display through DDC/CI) and there are many plugins you can put on those.

Holgero I need an amigable GUI 

Ok but you think that along time ago, don´t use any linux distribution so I install ubuntu_seraver but recommending me one amigable GUI (XCFE?)

---

### Post by Holger_Gehrke on 2023-08-25
Starting from an Ubuntu flavour with a GUI to set up a server is IMO a bit of a waste. But it certainly can be done. You still won't get around learning quite a bit about the command line since server software mostly can't be administered graphically and you'd have to get used to synaptic for installations since the 'normal' installer (Gnome Software) doesn't show most server programs. So the only use you'd get out of the GUI is mostly file management and you can do that without a GUI with the Midnight Commander (a text-mode two panel file manager; the lazy server admins best friend ;-) ).

Holger

---

### Post by goldfran on 2023-09-02
Well, I´m check Kubuntu with KDE... in preference / desktop effect, see magnifier option but.. only can config key mapping but can´t configure mouse wheel

---

### Post by oldfred on 2023-09-02
I use Kubuntu and control + changes sizes over default System Settings. 
In Kubuntu are multiple settings like zoom, track mouse  in Workplace behavior. And in Appearance is default fonts, so you can make things bigger by default if desired. Other settings to experiment with. It shows screen reader and says I do not have it installed.

---

### Post by goldfran on 2023-09-13
> **oldfred said:**
> I use Kubuntu and control + changes sizes over default System Settings. 
In Kubuntu are multiple settings like zoom, track mouse  in Workplace behavior. And in Appearance is default fonts, so you can make things bigger by default if desired. Other settings to experiment with. It shows screen reader and says I do not have it installed.

Ok, thanks for your reply.

I have tried several versions of "ubuntu" to see which one I could use with accessibility from the beginning... And I think that the best is Kubuntu because is posible to zoom in/out in "try kubuntu"... but I don´t know can use or configure mouse wheel up/down with and other key (win key for example or alt...)

I have a several visual problem and is very important to me

---

### Post by oldfred on 2023-09-13
I do not think I have used "Windows" key.
In Kubuntu:
Just tried holding control key & mouse wheel & that changes size.

---

### Post by goldfran on 2023-09-13
> **oldfred said:**
> I do not think I have used "Windows" key.
In Kubuntu:
Just tried holding control key & mouse wheel & that changes size.

Ok, I think we are not talking about the same thing...

When you press cntr + mouse wheel, only zoom in any windows for example in browsers... but I want to magnifier all the system... if I change options on "desktop enviroment" from Plasma, is magnifier option but... I dont´modifiy to use mouse wheel... only can key map, but not map mouse wheel

[IMG]https://forum.manjaro.org/uploads/default/original/3X/f/e/fe061ce3a72de5ee6d42fed913f3c3adf728696f.png[/IMG]

---

### Post by goldfran on 2023-09-19
Finally, an interesting option is this -- [https://forum.manjaro.org/t/how-to-zoom-in-out-with-key-mouse-in-kde/75525/6](https://forum.manjaro.org/t/how-to-zoom-in-out-with-key-mouse-in-kde/75525/6)

Using xbindkeys, and map + / - to wheel mouse and work with meta key (key windows)

---

