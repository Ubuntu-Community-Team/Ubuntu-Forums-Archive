---
title: "Asus X550V not booting from USB drive"
date: 2017-04-07
forum: New to Ubuntu
---

### Post by jimit12 on 2017-04-07
[COLOR=#111111][FONT=Ubuntu]So simply the idea is that my PC is not booting from USB drive. I've now been searching about this for a while and can't find anything really helpful. I've been trying to boot so many Linux distros, example Ubuntu, Mint, Zorin OS, Antergos, Solus, Parrot Security, Debian, Fedora and so on. The problem can't be on my USB stick because I've tried more than one stick and also all of my PCs USB ports.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What I've found is that maybe the Nvidia graphics driver makes booting from USB not possible. I have Nvidia Geforce GTX 950M on my PC. Also all distros boot from USB on the recovery mode. Without the recovery mode the boot progress just stops. Example with Ubuntu it starts booting but it stops on the Ubuntu logo after two of the loading dots have turned to white.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So I think it's the Nvidia drivers that's blocking my booting and Linux installation. I have also tried changing all settings in the bios example Secure boot control and CSM.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Does anyone know how to fix this I really would like to use Linux I'm so bored on windows and I can't find fix to this anywhere. Thank you in advance![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]SYSTEM SPECS: Computer model: Asus X550V notebook PC Graphic drivers: Nvidia Geforce GTX 950M and Intel Core i5[/FONT][/COLOR]

---

### Post by ^83%u#@^ on 2017-04-07
Try to reset bios settings and only enable CSM

Security -> Secure Boot Control - Disabled
Save Changes and Exit
reboot
then
BOOT -> Launch  CSM c Disabled -> Enabled ->Lauunch PXE OpROM -> Enabled 
Save Changes and Exit
reboot
then
BIOS - Boot - Boot Option - Choose what you need

---

### Post by yancek on 2017-04-07
You make a passing reference to being "bored" with windows but do not indicate whether you have any version of windows actually installed on this computer and, if so which version fo windows that might be.

A common temporary solution with specific video cards such as Nvidia is to us the "nomodeset" parameter on boot.  If you see the boot menu, just hit the e key on the keyboard to edit.  The boot screen should change and use the keyboard arrow keys to scroll down to the line beginning with the word linux, add nomodeset to the end of the line and press the appropriate key shown to continue booting.

---

### Post by RobGoss on 2017-04-08
Hello and welcome to the forum, Have you tried accessing your **BIOS **and setting your **USB** option to boot first?

Also what key combinations are you using in order to boot from the **USB**?

Sometimes it's just a matter of finding the right options to get things rolling. Another suggestion is did you try this **USB **stick in another machine to see if it would boot there could be something wrong with the USB stick it self

---

