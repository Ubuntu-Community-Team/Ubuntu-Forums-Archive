---
title: "Is there a way to dual boot Xubuntu and Ubuntu but both distros share the same data?"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by Benjamin5th on 2014-11-09
I would like to dual boot Xubuntu (14.04, which is already installed) and Ubuntu on my laptop. Is there a way to set it up so they share the same data? (for instance, if I download a application in Xubuntu, it is accessible in Ubuntu.)

---

### Post by coldcritter64 on 2014-11-09
> (for instance, if I download a application in Xubuntu, it is accessible in Ubuntu.)                 

Not applications installed in the other with a full dual boot. 

But you could install a full ubuntu set up and add the xubuntu-desktop package as well. Ubuntu is the main engine, so to speak, but the full xubuntu desktop experience can be selected from the light-dm log in screen. Clicking on the cog icon in the ubuntu light-dm log in screen will have an entry for xubuntu. In this case applications installed in either are available in the other DE.

In a terminal from within ubuntu,
```
 sudo apt-get install xubuntu-desktop
```
when the installation finishes, log out and click on the cog icon at the log in screen. From the drop down menu select xubuntu. Note whatever you select will remain  for future boots, use the cog icon to reset to what you want later on if your DE needs changed. You can add many different DEs to an ubuntu base install. Good luck.

Edit: just noted I'm in "New to Ubuntu", you could search for xubuntu-desktop in the software center for easier installation. The rest of the instructions above are the same though, re logging out to select the desktop environment (DE).

Edit 2: reread your opening post OP, you already have xubuntu installed, you could try opposite to what I suggested above and install ubuntu-desktop instead. Sorry for missing that.

---

### Post by Benjamin5th on 2014-11-09
I installed unity onto Xubuntu, but it's kinda glitchy. My desktop froze once, rebooted, and compiz wouldn't work, rebooted, and a couple of other minor applications wouldn't work either. I'm thinking it would be more stable to have them separated.

---

### Post by coldcritter64 on 2014-11-09
With 2 installs side by side dualbooted, running applications from the other could in theory be done with chrooting; maybe, but could get quite technical particularly if you run graphical apps. 

I've had good experiences running xubuntu on top of a unity base in the past. I could expect what you describe with instability going the other way with unity desktop on top of xubuntu, not a surprise to hear that really.

You may want to research "ubuntu chroot" and if you try chrooting between parallel installs how to use X for graphical applications.

---

### Post by vasa1 on 2014-11-09
> **Benjamin5th said:**
> I installed unity onto Xubuntu, but it's kinda glitchy. My desktop froze once, rebooted, and compiz wouldn't work, rebooted, and a couple of other minor applications wouldn't work either. I'm thinking it would be more stable to have them separated.
From [http://ubuntuforums.org/showthread.php?t=2251816&p=13163311#post13163311](http://ubuntuforums.org/showthread.php?t=2251816&p=13163311#post13163311)

---

### Post by flaymond on 2014-11-09
Yes, you can. But you cannot access the Ubuntu apps or files when you in  Xubuntu. and either. Having dual kernel on a pc is 'heavy-duty' if you  got an old pc with 2-3gb RAM and below. I'm using Lubuntu because its  lightweight and fast processing for an old PC (especially laptops and  netbooks). Having both OS will slow down your pc. Back to you question, you can do it in two ways... 'whole' dekstop method or just the desktop environment.

1. Whole method - with the Xubuntu packages
```
sudo apt-get install xubuntu-desktop
```

2. Just the Dekstop environment - without Xubuntu packages

```
sudo apt-get install xfce4
```

PS: Any mistake i done, forgive me..im a newbie..but these two codes work well if you want install it using Terminal

---

### Post by HermanAB on 2014-11-09
The trouble starts when you suspend one machine, then reboot into the other...

It would be best to use different desktops on the same machine and just make sure that the display manager is configured right.  I.e. don't run XFCE with the Gnome DM.  You may need to make a launcher script of your own for that, then file a bug report once you figured it out.

---

### Post by Mike_Walsh on 2014-11-09
Hallo, Benjamin. 

I can endorse what most of the other replies have stated, because I'm doing what they are telling you at this very moment. I have a full install of Ubuntu 14.04 on my desktop, with the Xubuntu desktop package installed on top of it. I'm typing this post from within the Xubuntu DE as I speak; I can click on the Whisker menu, and see both Ubuntu AND Xubuntu applications all in the same list. This is, I believe, what you are trying to achieve...

Regards,

Mike.

---

### Post by Benjamin5th on 2014-11-09
Okay, then it sounds like i'll just hope onto the Ubuntu wagon. Can I just stick a LiveUSB in and install Ubuntu 14.04 right over Xubuntu? Or is there something I need to do first?

---

### Post by Mike_Walsh on 2014-11-09
To be perfectly fair to you, I, personally, have found from experience that if you attempt to 'overwrite' one OS with another one, it invariably ends in tears. You really HAVE to re-format your disk with a full format (the SLOW one, I'm afraid), since the old one never seems to get overwritten properly; whether it's due to corrupted boot-loaders, or corrupted kernel modules, or whatever, I wouldn't like to say.

But if you WANT it to work properly, first time around, then there's no substitute for some initial preparation work first; it might seem like a lot of 'messing about', but it pays off, in the long run.....believe me. Just be methodical about it; do yourself a checklist, or something similar, and 'tick the boxes' as you complete each step. It DOES work.

Good luck.


Regards,

Mike. ;)

---

### Post by Benjamin5th on 2014-11-09
Oh dear....I have no idea how to do that. Can you tell me how?

---

### Post by Mike_Walsh on 2014-11-10
Well, we also need to know what machine you're running, and what it's specs are. A machine that will run Xubuntu, with it's 2D desktop, won't necessarily run Unity very efficiently, since Ubuntu now requires capability for 3D rendering by default. I'm lucky in that my 10 yr-old machine is still powerful enough to handle Unity...

Regards,

Mike.

---

### Post by flaymond on 2014-11-13
You can try the Xubuntu Desktop without installing. By the way, Ubuntu's Flavours (LTS version) get you pre-installed Disk Image Writer on it. It not so hard to reformat and rewrite the disk because the Apps make it easy to use. You dont need to reformat your USB after you boot using it, you easily can just change the partition. 

My advice is-

- Try the Xubuntu without installing it. ( To check if the environment running fine on your pc)
- I dont prefer you to have 2 Ubuntu flavours on an old PC because it will slowing your processing task or lagging.
- From what I had told by seniors, (Bucky Ball and others), that Xubuntu engine is same as Ubuntu.....so you should use Xubuntu (not too heavy and too light, elegant environment)              because its 'middle' level between Ubuntu (Heavy and nice features,based on Gnome unity), and the lightweight Lubuntu (really light, fast and desktop similar to Windows 7 but lesser       features than Xubuntu and Ubuntu).
- Ubuntu applications is same as other flavours.
-Use only ONE, like i said, its similar and only the environment is the main different.
- You can use both if you have new and fast pc (not every pc working good with it)
- Installing Xubuntu (XFCE) on Ubuntu just adding memories

Thanks :p


(Sorry seniors, if i make a mistake, forgive me and im sorry with my totally horrible grammar)

---

