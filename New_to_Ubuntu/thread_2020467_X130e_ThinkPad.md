---
title: "X130e ThinkPad"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by perogie on 2012-07-08
I have loaded the latest Ubuntu using the live CD. It will not boot. It just goes into Windows 7

---

### Post by mapes12 on 2012-07-08
You need to enter your BIOS at start up and set the boot order so that the Thinkpad boots from the CD drive.

Then take a look at this page:-

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by perogie on 2012-07-08
I guess I did not explain myself properly, sorry. Unbutu is already loaded. When I restart my computer it does not give the option of Windows or Ubuntu. After the Bios loads it goes straight to Windows 7.

---

### Post by skinnersbane on 2012-07-08
> **perogie said:**
> I guess I did not explain myself properly, sorry. Unbutu is already loaded. When I restart my computer it does not give the option of Windows or Ubuntu. After the Bios loads it goes straight to Windows 7.

It sounds like you installed Windows after Ubuntu, which means it wrote over the MBR.  Windows will not easily support dual booting (it can be done, but don't bother).

This is an easy and common thing to fix.  See the Ubuntu help on this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I recommend you just do the terminal way, but you can do the graphical way if you like :)

---

### Post by perogie on 2012-07-08
No, I bought the machine with Windows 7 on it. I installed Ubuntu after.

---

### Post by Redblade20XX on 2012-07-08
> **perogie said:**
> No, I bought the machine with Windows 7 on it. I installed Ubuntu after.

Just follow the article skinnersbane has linked. Use the graphical method, it should install (re-install??) the grub boot loader.

-Red

---

### Post by mapes12 on 2012-07-08
Try this:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by echo6 on 2012-07-08
Is it possible that your Grub menu is hidden?

Take a look at the Hidden section here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Try any key combination or if that doesn't work holding shift key down during boot.

---

### Post by YannBuntu on 2012-07-10
Hello

**@echo6:** if GRUB was just hidden, it would automatically boot on Ubuntu, not Windows.

**@perogie:** please run Boot-Repair, and indicate the URL that will appear.

---

### Post by perogie on 2012-07-10
Thanks
I have my wifi on and I am plugged into my route and it styill keeps asking me to connect to the internet even when i wanted to use the boot repair  program without updates. I check to see if my connection is good with the live Cd...all is well. Not sure why it will not connect.

---

### Post by perogie on 2012-07-10
Thanks
I wil give it a try.

---

### Post by YannBuntu on 2012-07-11
> **perogie said:**
> Thanks
I have my wifi on and I am plugged into my route and it styill keeps asking me to connect to the internet even when i wanted to use the boot repair  program without updates. I check to see if my connection is good with the live Cd...all is well. Not sure why it will not connect.

Hi. That's a known bug of B-R, it should be fixed in the last releases. 
1) Update Boot-Repair by opening a terminal (Ctrl+Alt+T) then type:
```
sudo apt-get update; sudo apt-get install -y boot-repair boot-sav
```

2) Then run Boot-Repair (via the Dash or the "boot-repair" command)
3) If needed, you can disable internet check via the Advanced options -> Other options tab -> untick the "Check internet" option

---

### Post by echo6 on 2012-07-11
> **YannBuntu said:**
> **@echo6:** if GRUB was just hidden, it would automatically boot on

Are you confident that is the case here?  He should at least explore the possibility that the config has changed.

---

### Post by YannBuntu on 2012-07-11
yes, I am 100% sure of it. After a fresh install, direct boot on Windows means that:
- either the kernel has not been detected by GRUB (should be rare)
- or the BIOS doesn't boot on GRUB -> need to either setup the BIOS or install GRUB correctly (eg via Boot-Repair).

---

### Post by perogie on 2012-07-12
All is working with the GRUB-EFI reloaded.

---

### Post by YannBuntu on 2012-07-13
Good job!
For our information, please could you indicate your current [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL ?

---

