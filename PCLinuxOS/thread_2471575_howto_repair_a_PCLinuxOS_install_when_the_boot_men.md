---
title: "howto repair a PCLinuxOS install when the boot menu is gone?"
date: 2022-02-03
forum: PCLinuxOS
---

### Post by fred-vie on 2022-02-03
hello,I have destroyed my installation by uninstalling thai language packs. At least thats what it said it was. I ended up losing all functions except for the running apps. After restarting I found that I also lost the boot menu along with all the repair options. Tried to start it from the stick but it gives no repair options from that either.Is there anything I can do to repair it after booting from the PCLinuxOS USB-stick? The time shift files are still on the drive but I have no clue howto start a repair.I'm not working with Linux for long and just did the most basic and necessary things to get it to do what I needed.

---

### Post by schragge on 2022-02-03
1. Even if PCLinuxOS uses APT (or, more precisely, [Apt4rpm]("http://apt4rpm.sourceforge.net")), it isn't based on Debian. So, probably the wrong forum to ask. FYI, PCLinuxOS has [its own forum](https://www.pclinuxos.com/forum), and it's quite active AFAICS.

2. I don't think you can destroy the installation just by uninstalling language packs. Perhaps, it's a coincidence, and you uninstalled something else at that time as well?

3. [quote=fred-vie]I ended up losing all functions except for the running apps.[/quote]
So, you can still run apps. Great. Now, please explain what do you mean by this.

---

### Post by fred-vie on 2022-02-04
1) I know they have theyr own forum but I cba sending my pw unprotected per email to get into that. Its retarded. This forum says PCLinuxOS too, but I mentioned already before I posted that it is not really used too often.   2) It said thai and language pack and I removed it because I dont use thai but after nothing worked anymore. I filtered it so there was no other package shown thus a mistake is out of the question and what you think doesnt matter.   3) Only the apps that where open already where still working. No new ones could be started, not even text files could be opened anymore. But it doesnt matter, I need a way to repair it from the USB- PCLinuxOS stick like I mentioned before because the bootmanager is gone too and just fixing the bootmanager wouldnt help either because it wasnt working anymore while it was running, except if the repair options would appear as well after fixing the boot manager.   Best would be if I could just play back the time shift files but I wouldnt know where to begin with since I can not boot into it anymore and dont know how it would work starting it from the stick.  A fresh install makes no sense either because it would take me days again to set everything up as I would want it to. Why this forum ignores the paragraphs that I make is beyond me...

---

### Post by schragge on 2022-02-04
See [RestoreGrub2]("https://pclinuxoshelp.com/index.php/RestoreGrub2") in the *PCLinuxOS Knowledge Base.* [Boot-Repair-Disk](https://sourceforge.net/p/boot-repair-cd/home/Home) is a possibility, too.

---

### Post by fred-vie on 2022-02-05
cheers!

---

### Post by mIk3_08 on 2022-02-05
> **fred-vie said:**
>  The time shift files are still on  the drive but I have no clue howto start a repair.I'm not working with  Linux for long and just did the most basic and necessary things to get  it to do what I needed.
> **fred-vie said:**
> cheers!
If you want to visit the pclinuxos just [click here]("http://pclinuxos.com").  And if you want to visit there forum just [click here.]("https://pclinuxos.com/forum")I may not that knowledgeable about these pclinuxos But maybe this can help. This pclinuxos are using KDE Plasma Desktop. I think this is awesome machine too. cheers

---

### Post by kc1di on 2022-02-05
Hi fred-vie,
Do you have the original DVD/USB live install disk?  If so you can repair the broken grub install from there.  Boot to the live session and go to system settings under that you will find boot as an option.
go to that tab and reinstall grub from there.  Then reboot.  You really should get back into PCLinuxOS forums though as you'll get much better support for that Distro there. 
They are a great group and many there to help with almost any problem in PCLinuxOS.  Good luck.
P.S. In PCLinuxOS there are two control centers if you have the KDE version one is just for the KDE desktop the Other is PClinuxOS's control center it is the PClinuxOS control center you want.

---

### Post by fred-vie on 2022-02-11
> **mIk3_08 said:**
> If you want to visit the pclinuxos just [click here]("http://pclinuxos.com").  And if you want to visit there forum just [click here.]("https://pclinuxos.com/forum")I may not that knowledgeable about these pclinuxos   Like I explained before. I would have to send username and pw by unprotected email to have access to that forum which I'm not willing to do. It is retarded and unsave and as long as I can not register online I will not be using PCLInuxOS again! I would just like to repair it to get the data that I do not have access to without booting into it.

---

### Post by fred-vie on 2022-02-11
> **kc1di said:**
>  Do you have the original DVD/USB live install disk?  If so you can repair the broken grub install from there.  Boot to the live session and go to system settings under that you will find boot as an option. go to that tab and reinstall grub from there.  Then reboot.  You really should get back into PCLinuxOS forums though as you'll get much better support for that Distro there.  

Thanks for the info. I'm going to try that, But I also have the repair disk image Schragge told me about.   I'm just scared it will somehow botch up the boot manager of the just recently installed Linux Mint somehow. The reason I'm saying that is that both so called "boot managers" (PCLOS and Mint) where too stupid to boot up the windows partition instead the system restarts and goes back to the boot manager where it then starts into Linux if I dont prevent it. 

So it wouldnt surprise me if I "repaired" it and then I couldnt start Mint anymore which is my current Linux. Not that I'm happy with it but I have yet to find a distri that does not make any problems with something.   

Also I am pretty sure I will not be able to start into PCLinuxOS without a repair of the OS itself via the Timeshift option and I never did that before so there is that.   

> **kc1di said:**
>  They are a great group and many there to help with almost any problem in PCLinuxOS.  Good luck. P.S. In PCLinuxOS there are two control centers if you have the KDE version one is just for the KDE desktop the Other is PClinuxOS's control center it is the PClinuxOS control center you want. 

see above mentioned post(s)

---

### Post by howefield on 2022-02-11
> **fred-vie said:**
> I would have to send username and pw by unprotected email to have access to that forum which I'm not willing to do. It is retarded and unsave and as long as I can not register online I will not be using PCLInuxOS again!

Good idea, cut yourself off from the very people who could assist you. 

These forums are not a substitute for any another.

Thread closed.

---

