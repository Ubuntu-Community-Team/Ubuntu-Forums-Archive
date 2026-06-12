---
title: "Installing Ubuntu without being connected to the internet"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by socaldrum on 2008-05-21
Is there any way I can install Ubuntu without being connected to the internet? I'm a complete Linux noob, so I could use some help.

Thanks!

---

### Post by Promaster91 on 2008-05-21
Yes, download the .iso from Ubuntu.com. If your internet connection is really slow, you can buy or request a CD online. Once you have the CD, reboot the computer you want to install ubuntu in and at the BIOS select your cd drive, then follow the instructions from there.

---

### Post by socaldrum on 2008-05-21
What do you mean by BIOS?

Sorry for the stupid question :)

Thanks!

---

### Post by SunnyRabbiera on 2008-05-21
> **socaldrum said:**
> What do you mean by BIOS?

Sorry for the stupid question :)

Thanks!

Its not really a stupid question actually.
The BIOS is that first screen that pops up before loading your OS, it usually says "press F11" or something of that extent for booting options.

---

### Post by socaldrum on 2008-05-21
Alright, I'm at the booting option screen on my other computer (a Dell Dimension 2400 with XP) and I'm not really sure what to do. It would be great if someone could walk me through this, thanks :)

---

### Post by neurostu on 2008-05-21
I believe that most bios's are set to boot from the CD before the HDD by default so you shouldn't have to worry about that.

And really there aren't any stupid questions here, this is a forum for Absolute Beginners!

---

### Post by neurostu on 2008-05-21
> **socaldrum said:**
> Alright, I'm at the booting option screen on my other computer (a Dell Dimension 2400 with XP) and I'm not really sure what to do. It would be great if someone could walk me through this, thanks :)
Just try booting normally with the CD in. Don't start messing with the bios until you have to.

---

### Post by SunnyRabbiera on 2008-05-21
I am not entirely sure as the BIOS though simular on each computer is laid out differently..
In the BIOS menu is there at least a boot up selection or something along those like that?

---

### Post by socaldrum on 2008-05-21
Well, for some reason my computer doesn't seem to boot from the CD when I restart the computer. When I go to My Computer, the CD shows up, though - can I start the installation process from the CD directly?

---

### Post by SunnyRabbiera on 2008-05-21
> **socaldrum said:**
> Well, for some reason my computer doesn't seem to boot from the CD when I restart the computer. When I go to My Computer, the CD shows up, though - can I start the installation process from the CD directly?

you can, you may want to try an alternate installation disk too.

---

### Post by socaldrum on 2008-05-21
So, I opened the wubi.exe file from the CD, and the installation started. About 2 minutes in, though, a box came up saying "Please connect to the internet" and didn't let me continue the installation.

I'm not sure if that was what I was supposed to do, but I could definitely use some help. Thanks.

---

### Post by neurostu on 2008-05-21
Ok so it looks like your computer is not configured to boot from the CD if there is one present. 

I would recommend against the WUBI installer, its new and hasn't been proven 100% yet.  

So reboot your machine, open your BIOS and look for a setting like boot order, boot settings, and look for a way to make it boot CDRom before HDD.  

If you have two machines use the second in this forum and post what options are available and we can try to talk you through it.

---

### Post by socaldrum on 2008-05-21
Yes!!!

finally got the installer up and running, thank you guys!

---

### Post by neurostu on 2008-05-21
Did you do it by changing the bios boot order? or did you get wubi working? For future reference (I'm telling this b/c I guess your new her) you can publically thank people by clicking the little star on the bottom right of one of their posts.

---

