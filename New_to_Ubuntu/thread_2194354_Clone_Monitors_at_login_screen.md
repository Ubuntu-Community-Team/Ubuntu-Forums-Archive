---
title: "Clone Monitors at login screen"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by david.r.maskell on 2013-12-18
So, I've installed Ubuntu 12.04 LTS now on the computer I'm intending on using as my server, unfortunately Its got a broken Internal display (Laptop) and therefore I can't see the login screen which is insisting on appearing on the laptop display only and not the external monitor. (unless its turning both of them off). Does anyone have any suggestions how to fix it?

---

### Post by ian-weisser on 2013-12-20
If it's a server, can you ssh into it?
If so, it will make fixing the problem a *lot* easier.

Hmmm. When I boot my Xubuntu laptop, with external monitor set to mirror, I get the boot experience on both displays. So perhaps your display settings just need to be tweaked a bit...once you can get in.

---

### Post by DuckHook on 2013-12-20
If you were able to install the first time, this means that an external monitor worked at least during the install process. Therefore, I suggest that you go into your BIOS and switch off the laptop monitor entirely. On laptop BIOSes, this is often a variation of: "turn off laptop monitor if external monitor is detected/connected".

If no such setting (which would be hard to believe—please look carefully through your whole BIOS), then install using either mini.iso or alternate.iso and *make sure* you choose "expert install". When install process gets to the part where you choose server packages, *make sure* you choose (in addition to your desired server pkgs) "ssh server". Upon reboot, you should be able to ssh into your server machine with the userid/passwd defined during the install.

Many servers run headless, so this workaround is common and well tested. You will likely want to change your ssh config to allow only RSA key or certificate access and to disable passwords, but this can be done after everything is running properly.

---

### Post by david.r.maskell on 2013-12-20
> **ian-weisser said:**
> If it's a server, can you ssh into it? If so, it will make fixing the problem a *lot* easier.  Hmmm. When I boot my Xubuntu laptop, with external monitor set to mirror, I get the boot experience on both displays. So perhaps your display settings just need to be tweaked a bit...once you can get in.

Thanks Ian, unfortunately Whilst it is a server, I am running ubuntu Desktop and hoping to setup some virtual machines to run the servers themselves and haven't installed anything on the computer yet (like ssh), so I can't ssh into it :/. 

Interesting, I get the ubuntu loading screen thingo on both displays (hard to tell whether its on the laptop display though as the backlight has died, but I vaguely remember vaguely seeing the dots changing colour on it one time that it was booting), but when it gets to the login screen I get nothing, I'm not sure if its only on the laptop display and I can't see it or if its shut both displays off (as seems to have been the case for some other people). 

I tried to setup an auto-login (I figure the servers will still be password protected under the virtual machine), but when I tried to save lightdm.conf it said "read only file system, failed to save" or something along those lines, and I was thinking "come-on, I'm logged in under recovery command line and it appears to be logged in as root, which has all privileges right?". 

Any other ideas how I might be able to bypass or fix the problem would be greatly appreciated :)!

Thankyou

David

---

### Post by david.r.maskell on 2013-12-20
> **DuckHook said:**
> If you were able to install the first time, this means that an external monitor worked at least during the install process. Therefore, I suggest that you go into your BIOS and switch off the laptop monitor entirely. On laptop BIOSes, this is often a variation of: "turn off laptop monitor if external monitor is detected/connected".

If no such setting (which would be hard to believe—please look carefully through your whole BIOS), then install using either mini.iso or alternate.iso and *make sure* you choose "expert install". When install process gets to the part where you choose server packages, *make sure* you choose (in addition to your desired server pkgs) "ssh server". Upon reboot, you should be able to ssh into your server machine with the userid/passwd defined during the install.

Many servers run headless, so this workaround is common and well tested. You will likely want to change your ssh config to allow only RSA key or certificate access and to disable passwords, but this can be done after everything is running properly.

I had a look in the BIOS for such a thing, but can't seem to find one. Its the older style of DELL BIOS (A16?) I'll have a look on the internet and see if theres a way of doing that.

I wondered about re-installing (since its ubuntu desktop, not server) and selecting auto-login, but I've only got a disk for 11.04 LTS and I then upgraded to 12.04 LTS and then it restarted and my troubles started, and I don't have very much internet download capacity to play with, so the less I can download 700mb worth of stuff the better :P. But I am open to re-installing if there is no other option I guess.

Thankyou

---

### Post by david.r.maskell on 2013-12-20
I'd probably better add, the monitor is connected through the Digital Port. I might be able to source a VGA cable to try that.

---

### Post by DuckHook on 2013-12-20
> **david.r.maskell said:**
> I'd probably better add, the monitor is connected through the Digital Port...Ah! An important detail. Sometimes Linux will output to the VGA port as a fallback. It's supposed to detect your monitors, but if it can't, the output goes askew. If you have a VGA cord, by all means try that first.

As an aside, "server" is an ambiguous term. I (and, it seems, Ian too) assumed that it was a typical server installation without GUI but with typical server tools like SSH. From your description, what you have is actually a desktop install that you have added a few extra server apps to. If so, then should your VGA switch work, the first thing you should do is install SSH and make sure that it works. So long as you can access your laptop, you can manipulate/fix it.

---

### Post by david.r.maskell on 2013-12-20
> **DuckHook said:**
> Ah! An important detail. Sometimes Linux will output to the VGA port as a fallback. It's supposed to detect your monitors, but if it can't, the output goes askew. If you have a VGA cord, by all means try that first.

As an aside, "server" is an ambiguous term. I (and, it seems, Ian too) assumed that it was a typical server installation without GUI but with typical server tools like SSH. From your description, what you have is actually a desktop install that you have added a few extra server apps to. If so, then should your VGA switch work, the first thing you should do is install SSH and make sure that it works. So long as you can access your laptop, you can manipulate/fix it.

I'll give it a go and get back to you.

Yea, I see why you would have thought by server I was meaning ubuntu server/something without a GUI. Sorry for the mis-understanding.

Thankyou
David

---

### Post by david.r.maskell on 2013-12-22
so..... I connected a VGA cable... it showed up on the screan. first i setup an autologin for the user, then I installed a VNC server so I could connect to ubuntu from my computer via tightVNC. it then booted into command-line... I connected the monitor from startup (because I was starting to see if it had an error or something) it booted into GUI, but said something like couldn't switch monitors. then auto-logged-in. Why did it require the VGA monitor there on startup?

---

