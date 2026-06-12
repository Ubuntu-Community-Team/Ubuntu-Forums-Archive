---
title: "problem with Samsung 931b monitor in Hardy"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by ap659 on 2008-10-24
Hi to the forum members,

  first of all this is a great idea, and my thanks upfront to all who are helping out the new adopters. Now, I'm familiar with unix command line but not with desktop Linux. Having heard a lot of good things about Ubuntu Hardy, I have installed it on my old Compaq desktop.

There seems to be a problem with detection of monitor- the exact model is not reported in xorg.conf, nor is the integrated graphics card. Now, the monitor is configured automatically by Ubuntu at the correct resolution, but here's where the REAL problem is- half the time, upon leaving the monitor idle, it goes blank and Ubuntu is unable to turn it on again. The only solution remaining is to do a hard reboot.

Also, here's what displayconfig-gtk shows:

Screen tab: plug-n-play model. If I try to select the model, the Samsung Syncmaster 931B isn't available in the list. Selecting a similar model 930b, or 931bf(vga) soon crashes the whole display.

Graphics card tab: driver as none. If I try to select, choose driver by name shows intel i810. If I say ok here, still the graphics tab shows driver as none.

Can you guys please help out? My machine specs follow- 
PC model: Compaq Presario 5000 (desktop PC)
Intel PIII 733MHz
Chipset: Intel i810E, rev A3
Bios: Compaq, ver:686C3
Graphics: Intel onboard 82810E graphics controller (VRAM 36MB)
Monitor: Samsung Syncmaster 931B (analog connection)
RAM: 384MB

again, thanks a ton,
ap659

---

### Post by nhasian on 2008-10-24
hmm I hope that someone else here on the forum would be able to help you resolve the problem, but as a workaround you could prevent the pc from putting the monitor to sleep by going to System/Preferences/Power management.  then under "put display to sleep when inactive" to never.

---

### Post by ajgreeny on 2008-10-24
I agree, it certainly sounds like a power management problem, so I would do as nhasian says, but also check that the system is not set to suspend after a certain amount of time, as this often causes problems, particularly with older machines, as far as resuming a session is concerned.

---

### Post by ap659 on 2008-10-24
Thanks for responding, nhasian and ajgreeny- guess I should have said this earlier. I had always set the sleep mode off, by setting to 'never' as suggested by nhasian. This problem is distinct from the sleep issue- the monitor blanks out and becomes unresponsive after a while, and this is happening when sleep/suspend is disabled.

-ap659

---

### Post by Butthead on 2008-10-24
Hmm, I have a Samsung 931B, and it sure showed up in my Hardy monitor list. :confused:

BTW - it is (supposedly?) safe to use the 930B driver instead.  That's what they told me over on the Mandriva forum. :guitar:

---

### Post by ap659 on 2008-10-26
thanks, Butthead... 931bf shows up in my list (and does not work), but not 931b. The 930b selection also crashes the display. For now, I'm continuing with the display selection as generic monitor, plug-n-play. In the power management, I have now changed setting to 'never set the monitor to sleep' and after that the monitor so far has not crashed.

Strangely, the Ubuntu system has recently hanged twice while attempting to shutdown! I must say that though I'm somewhat pleased with the desktop experience, overall the Ubuntu experience did not turn so positive- basic user issues like display crashing, crashing while shutdown are not encouraging at all. Firefox on my low spec system is quite slow and creaky, and behaves strangely when I right click links- sometimes trying to bookmark them, or save them. Another big glitch in my opinion is during disk partitioning phase of installation ( using the alternate 8.04.1 CD )- which partition is using XP is not very obvious; also only at the very end of the installation is the user informed that he has another OS installed ( grub config stage i think ).

On the plus side, the artwork and theme is good, the update manager is wonderful ( way better than XP ), nautilus is great ( again much better than windows explorer ).
Last, and certainly not the least, the community here is wonderful and so many tried to help even in this thread. I greatly appreciate all the inputs.

-ap659

---

### Post by Butthead on 2008-10-26
Hmm, that's strange?  Does the 931BF driver show up as installed under "System Settings" too? :confused:

Remember, you have to enable stuff as "root" there for settings to stick.

---

