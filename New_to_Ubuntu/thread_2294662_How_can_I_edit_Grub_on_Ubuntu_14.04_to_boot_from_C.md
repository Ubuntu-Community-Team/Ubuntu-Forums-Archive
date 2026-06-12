---
title: "How can I edit Grub on Ubuntu 14.04 to boot from CD drive?"
date: 2015-09-12
forum: New to Ubuntu
---

### Post by Tluanda on 2015-09-12
I have updated my laptop fom Windows 8 to Windows 8.1, but something went wrong, so I have to use the installation CD to repair Windows. But when booting the computer I get a dark screen and it wont let me access the BIOS or the select drive menu, I have tried hitting all F keys to access, but so far no luck. Before the update, I had Ubuntu 14.04 installed, so after booting I get the Grub menu, but it won't let me boot from an USB drive from the command line because of security reasons, and I don't know the command to select the CD drive from the command line. I made a Google search, but all the information I've found is outdated, but from what I understand I need to edit the Grub menu to make the CD drive a boot option, how can I do this?

---

### Post by grahammechanical on 2015-09-12
Your problem is nothing to do with the Linux boot loader (Grub). To enter the BIOS boot system we need to press a certain key before the Grub boot menu loads. Once the Grub boot menu loads it is too late to enter the BIOS settings utility.

Your machine's (motherboard) user manual should tell you what key to press as the manufacturer's splash screen appears on the monitor. The correct key can vary from manufacturer to manufacturer. On my Asus motherboard I tap Del. 

Regards.

---

### Post by iulian X on 2015-09-12
>  the correct key can vary from manufacturer to manufacturer. 


f2, f8, f12

---

### Post by tluanda2 on 2015-09-15
Been there, done that, didn't worked!

---

### Post by tluanda2 on 2015-09-15
> **iulian X said:**
> f2, f8, f12

Been there, done that, didn't worked!

---

### Post by Easy Limits on 2015-09-15
Delete or Esc key

---

### Post by tluanda2 on 2015-09-15
> **grahammechanical said:**
> Your problem is nothing to do with the Linux boot loader (Grub).

It has everything to do with Grub, when I turn on the computer first thing I see is the Grub.

> **grahammechanical said:**
> To enter the BIOS boot system we need to press a certain key before the Grub boot menu loads. Once the Grub boot menu loads it is too late to enter the BIOS settings utility.

Your machine's (motherboard) user manual should tell you what key to press as the manufacturer's splash screen appears on the monitor. The correct key can vary from manufacturer to manufacturer. On my Asus motherboard I tap Del. 

I never see the manufacturer's splash screen appears on the monitor. First thing is the Grub. I simply can't access the BIOS boot system.

---

### Post by QIII on 2015-09-15
Hello!

You may either consult your documentation or provide the model and specifications and wait for someone to look it up.

The former will be quicker for you.  The latter will depend on the good heartedness of a volunteer.

At this point, guesses are the best you can hope for - and that is unlikely to be helpful.

GRUB loads after your BIOS turns over control.  If you can't get to your BIOS, it has nothing to do with GRUB.

---

### Post by tluanda2 on 2015-09-15
> **Easy Limits said:**
> Delete or Esc key
Also tried it and it didn't worked.

---

### Post by QIII on 2015-09-15
Are you waiting until after the GRUB menu loads to press keys?

---

### Post by oldfred on 2015-09-15
Many UEFI have a fast boot setting, which is not the Windows fast start up setting in Windows.

If fast boot is set, you may have to fully shut down system, remove battery if laptop, and hold power switch for 10 sec or so. Then you must immediately press correct key to get into UEFI as soon as system starts. 
If that does not work you have to get to motherboard battery and remove it for a while. Then immediately press correct key when booting. That will also reset all UEFI settings to defaults so you have to remember all the changes you made and redo them.

       BIOS Setup Utility Access Keys for Popular Computer Systems
[http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by tluanda2 on 2015-09-27
Thanks for your help, I solved the problem, but I must say nothing you guys told me worked.

If you are having the same problem I did, let me tell you how I did it. After spending a lot of hours googleing, I found something called Plop Manager, which after a bunch of configuration help to change the Grub and include an option to access the Lenovo flash screen, and eventually windows... After an error screen. Turns out windows installed correctly, but the Grub, or Ubuntu, was not letting access it. I don't know why or how, but that's what happened. 

If you guys do not have that problem, that's OK, if don't believe me. I will uninstall this <snip> piece of operating system that has only given me headaches instead of solutions. I shouldn't have installed in the first place. 

If you are struggling as I did, I hope Plop manager can help you, but do yourself a favor once you get to Windows and uninstall this <snip> called Ubuntu.

---

