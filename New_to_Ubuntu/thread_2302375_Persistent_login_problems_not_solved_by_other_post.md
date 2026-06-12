---
title: "Persistent login problems not solved by other posts"
date: 2015-11-09
forum: New to Ubuntu
---

### Post by jay106 on 2015-11-09
Hi ubuntu forums, I have had ubuntu on my last laptop for a year or so but it required little tweaking to work so for all intents and purposes I'm a newbie. If I'm posting in the wrong area or am making a mistake of any kind do let me know and I'll fix it. 

I'm going to throw a bunch of info at you straight away so there (hopefully) will be enough information to work with. 

This new (to me) laptop has Vista on it, I chose to install ubuntu 32 bit 14.04 on it because it was dreadfully slow, but wanted to dual boot so I (incorrectly) did a manual partition and only made a / partition. It booted correctly but after having some issues with graphics flickering and trying to find fixes for this I rebooted and the computer would not go any further than to tell me I had cryptswap issues.

Realizing my mistake I reinstalled from my usb with the iso and made sure to reformat the space with the old ubuntu os and set aside 4gb of /swap, 20gb for the /, and plenty more for /home. 

My issue now seems to be the infamous login loop, but unlike others the fixes have been a bit of a dead end, I do not know if this is incompetence on my part or I have done something irreversible. I have tried reinstalling ubuntu again and no luck, I cannot boot Vista either it takes me to ubuntu. I am unable to login as guest, it does the same login loop. I tried using "sudo chown  <username>:<username> .Xauthority" and after being prompted for my password I got no response, tried to login once again and still loops. I tried reinstalling and reconfiguring lightdm, still no luck. 

I apologize for the text wall but I figured the more information the better. If I don't get a response I suppose I can try to reformat the USB card on another computer and reinstall the iso to ensure that it's not the problem, I will post those results. Thank you in advance.

SOLVED: I had done something when trying to fix my screen tearing issue that changed the drivers, installing PPA and updating fixed the issue

---

### Post by C.S.Cameron on 2015-11-09
Does Ubuntu work OK when run from the thumb drive?

---

### Post by mastablasta on 2015-11-10
what do you mean no response? if you entered the password and you are just thrown back to prompt it means the password worked. the question is what have oyu been doing and what did you do. which we can't know from the description. a login loop on preformated partition and fresh install doesn't make sense.

---

### Post by jay106 on 2015-11-10
> **C.S.Cameron said:**
> Does Ubuntu work OK when run from the thumb drive?

I get the login loop when booting from the thumb drive as well, which to me is bizarre, could it be that the iso file is somehow compromised?

---

### Post by jay106 on 2015-11-10
> **mastablasta said:**
> what do you mean no response? if you entered the password and you are just thrown back to prompt it means the password worked. the question is what have oyu been doing and what did you do. which we can't know from the description. a login loop on preformated partition and fresh install doesn't make sense.

I was not aware that the lack of response meant that it worked, thank you for clarification. 

I see your point about not knowing what I've done. I have repeated the process from scratch again. I used the universal usb installer from pendrivelinux.com to reformat and put a fresh install of the iso file on the usb drive. I then did an install with manual partition as I did before. I still have the login loop problem, no luck with guest either. 

I know it doesn't make sense, I'm trying to figure this out too, I did not have this problem with my last computer. I appreciate you taking the time to reply.

---

### Post by mastablasta on 2015-11-11
well that is interesting. can you boot into recovery mode? [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
what about into text only mode? [http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html](http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html)

if you manage to get into text only mode, then you can check the logs particularly dmesg for any error messages.

at the moment we do not know much. is the GUI crashing? or is something wrong with boot sectors? so running boot info script form maybe will help identify the issue ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) as well as posting some system specs. 

I am guessing that live sessions work normal and you can boot into it?!

---

### Post by jay106 on 2015-11-11
> **mastablasta said:**
> well that is interesting. can you boot into recovery mode? [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
what about into text only mode? [http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html](http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html)

if you manage to get into text only mode, then you can check the logs particularly dmesg for any error messages.

at the moment we do not know much. is the GUI crashing? or is something wrong with boot sectors? so running boot info script form maybe will help identify the issue ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) as well as posting some system specs. 

I am guessing that live sessions work normal and you can boot into it?!

I was able to boot into recovery mode, I was also able to boot into temporary text only mode. While in text only mode I was able to log in using my normal username. I then attempted to install boot repair using your link but after the first line "sudo add-apt-repository" I was given "Error: need a repository as argument"

The computer is an HP G60-243CL notebook pc. I am running ubuntu 14.04 32 bit since the original Vista os was 32 bit. Should be 3gb ram, amd turion X2, Nvidia GeForce 8200m. I have read that some versions of Nvidia do not play well with ubuntu, could that be the case? 

If you need more specs I'd be happy to give them to you I'm not certain what is relevant.

---

### Post by jay106 on 2015-11-11
> **mastablasta said:**
> well that is interesting. can you boot into recovery mode? [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
what about into text only mode? [http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html](http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html)

if you manage to get into text only mode, then you can check the logs particularly dmesg for any error messages.

at the moment we do not know much. is the GUI crashing? or is something wrong with boot sectors? so running boot info script form maybe will help identify the issue ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) as well as posting some system specs. 

I am guessing that live sessions work normal and you can boot into it?!

Sorry to reply twice but I get the same login loop when booting a live session from my usb, which again makes no sense to me. Maybe it is a hardware issue?

---

### Post by mastablasta on 2015-11-12
it does look like a hardware issue. if you can boot into text mode though it might also be a GPU driver or chip issue (overheating, bad capacitors, not enough power?!).

did you maybe install the drivers for the GPU chip? have you tried using nomodeset boot option? or the VGA one? : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jay106 on 2015-11-12
> **mastablasta said:**
> it does look like a hardware issue. if you can boot into text mode though it might also be a GPU driver or chip issue (overheating, bad capacitors, not enough power?!).

did you maybe install the drivers for the GPU chip? have you tried using nomodeset boot option? or the VGA one? : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had been trying to fix a screen flicker before the login issue, I changed from the open source driver to the proprietary one, I wonder if that did it. I will take a look at the boot options.

Edit: I'm trying to figure out how to use "nomodeset", I'm having trouble finding clear instructions on mobile, would you happen to know how to do this? I see Nvidia cards as a common issue when I Google this so it may be the key to fixing this.

Edit 2: I have successfully booted in nomodeset and it gives me a low-res login screen but still no login

---

### Post by jay106 on 2015-11-13
So on a whim I decided to install PPA since it is said to fix nvidia driver issues and after a reboot I was finally able to log in, success! I can only assume that I did something to the drivers in an attempt to fix the screen tearing/flickering issue and this fixed it.

---

### Post by mastablasta on 2015-11-14
so it was the drivers. check the info on your card/chip that is out there on the internet. you may need to use older version of driver (manual install) to use the card. unfortunatelly i do not know much about nvidia. you could also tr yinstalling nvidia drivers, then running their report script then removing their drivers (since they cause screen issues). then you can use the created report to troubleshoot at nvidia support or on their forums. unfortunatelly it seem like they can't thelp a lot (iunless it is a known issue for the chip) without the report created by script.

---

### Post by mörgæs on 2015-11-14
If a PPA solved it then the problem was old drivers. It would most likely also have been solved with a fresh install of 15.10, just remember to accept closed-source/restricted drivers during install (for Nvidia, that is).

Support for Nvidia is getting better and better for each release, also for semi-old cards like the 8xxx series.

---

