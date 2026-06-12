---
title: "Install question"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by shnuegums on 2008-04-23
Yeah really new to this but it seems like fun :D

I want to install ubuntu on my d drive with out the grub showing up when I power on. This way I can boot it from bios and selecting the drive ubuntu is on and boot from it that way. How do I do that so it wouldnt affect my mbr?

Well actually I have that innotek virtualbox and that is how I want to boot ubuntu so I can have the best of both worlds. ;)

---

### Post by metalf8801 on 2008-04-23
I did that by disconnecting my other hard drives

---

### Post by neurostu on 2008-04-23
disconnecting during installation or when you were running?

---

### Post by mlentink on 2008-04-23
> **shnuegums said:**
> 
Well actually I have that innotek virtualbox and that is how I want to boot ubuntu so I can have the best of both worlds. ;)

Actually, you wouldn't.
When you run Ubuntu as a virtual machine in Virtualbox on Windows, you will not be able to use full graphics power. No Compiz, no desktop effects, no screen candy. 
Personally, I run it the other way around. For the rare windows programs I simply have to run for work, I run a windows xp virtual machine in Virtualbox. 

I would suggest you take a look at Wubi, which is included in the impending 8.04 release. Google for wubi-installer and you'll get there


Edit: you cannot install Ubuntu on a separate drive and choose the drive throught bios and bypass Grub that way. In order to do that, the Windows drive would need to be physically removed and vice versa...

---

### Post by shnuegums on 2008-04-23
Isn't there a way when installing by installing to say d:\boot\something else
so that when I boot up its in windows and if I go to boot menu and select d: it would boot ubuntu?

---

### Post by shnuegums on 2008-04-23
of course the something else part would be another folder

---

### Post by mlentink on 2008-04-23
> **shnuegums said:**
> Isn't there a way when installing by installing to say d:\boot\something else
so that when I boot up its in windows and if I go to boot menu and select d: it would boot ubuntu?

I don't rightly believe I understand what you're saying. Installation is by definition done by installing.

If you install Ubuntu, and you choose to install it alongside your existing operating system, it will install grub, which will present you with a choice of operating systems at boot time. Simply select the one you want and that will be booted. 
Wubi will work the same way, in essence, but it will not install ubuntu to a real physical partition, but to a virtual one inside a file on your windows partition.

Does that make it any clearer? Or do I indeed completely mistunderstand?

---

### Post by shnuegums on 2008-04-23
No you understand correctly but I want to figure away around the grub installation so that it doestn't give the choice of booting I want to manually boot it from the drive.

---

### Post by mlentink on 2008-04-23
If that is the case then you have no other option but to keep the two disks completely separate. When you install the first OS on the first drive, the second on needs to be disconnected. When you subsequently install the second OS on the second drive, the first one needs to be disconnected. 

It can be done, but it's awkward. GRUB is a lot easier, and far more dependable. Millions of people dual-boot with it.

If you are scared about your windows drive, try Wubi first.

---

### Post by shnuegums on 2008-04-23
No I'm not scared and did have it installed that way before but when I want to uninstall for any purpose I dont want the grub there still and prevent me from booting windows because of some unforeseen error. Thus if I can install the grub on the d: drive and just manually boot from the boot menu it would make it easier not to mention I can swap the d: drive with my other desktops with out having to do a full install again.

---

### Post by shnuegums on 2008-04-23
[https://answers.launchpad.net/ubuntu/+question/11286]("https://answers.launchpad.net/ubuntu/+question/11286")

this is a link to somewhat of what I am looking to do just wondering if anyone has tried this and it worked????

---

### Post by cdenley on 2008-04-23
I think the ubuntu installer will install grub on the first hard drive in the boot order (the one that you will boot to with your current bios settings). You should be able to change the boot order in your bios settings. However, sometimes some bios settings work differently than others, and maybe the boot order can be detected incorrectly for some reason. The safest way to make sure grub is written to the correct drive is to disconnect or disable the incorrect drive(s).

---

### Post by metalf8801 on 2008-04-23
> **neurostu said:**
> disconnecting during installation or when you were running?

before I install Ubuntu then I reconnected them afterworlds the I would hit f2 or was it f12 to so that i could select which drive i wanted to boot from

---

