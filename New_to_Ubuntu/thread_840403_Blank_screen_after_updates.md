---
title: "Blank screen after updates"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-06-25
hi all,

  i updated my ubuntu some 30 or 40 minutes before, as i set check for updates weekly and today the update icon appears on top panel. i allowed them to install by default and it went fine. it prompts me to restart machine and i did so. after restarting as usual it asked for username and password to login and after credentials are given "instead of desktop" i got a white blank screen and i waited for a while but nothing turned up. what i did is again restarted my PC and same condition still. i restarted manually for 2nd time and in boot prompt i selected "Ubuntu" and countdown starts. I pressed "Esc" this time (not previously) and i found the following:

 1. Ubuntu 8.04; Kernel 2.6.xx - **19** (generic)
 2. Ubuntu 8.04; Kernel 2.6.xx - **19**(recovery)
 3. Ubuntu 8.04; Kernel 2.6.xx - **18** (generic)
 4. Ubuntu 8.04; Kernel 2.6.xx - **18**(recovery)
 5. Ubuntu 8.04; Kernel 2.6.xx - **16** (generic)
 6. Ubuntu 8.04; Kernel 2.6.xx - **16**(recovery)

  Now what i did is i selected 3rd option from above "Ubuntu 8.04; Kernel 2.6.xx - **18** (generic)" and it works fine and landed to desktop. May i know what is wrong with it? also please tell me whether i have updated any wrong things in my PC (as am 30 days old to linux - ubuntu). Please tell me do i have to remove that "19" in  kernel from my PC, if so what is the procedure. Also instruct  me how to work with this updates while updating packages. Thanks in advance. Please help me.

---

### Post by perlluver on 2008-06-25
You got an update for the Kernel, which most likely killed any video card drivers you may have installed.  So you would have to reinstall the drivers for the new Kernel.

---

### Post by mailtwogopal on 2008-06-25
hi,

  Please tell me how to get that things done inorder that graphics work for updated kernel. kindly suggest.

---

### Post by perlluver on 2008-06-25
> **mailtwogopal said:**
> hi,

  Please tell me how to get that things done inorder that graphics work for updated kernel. kindly suggest.

Depends on what video card you have.  Run in a terminal lspci and post the output here, if you are unsure of the video card.  Once that is complete we can work on fixing it up.

---

### Post by mailtwogopal on 2008-06-25
hi,

  i ran "lspci" in terminal and following is the output:

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by perlluver on 2008-06-25
> 01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]

Ok that is your video card, so you would boot in to the recovery mode of the .19 kernel, and run sudo dpkg-reconfigure xserver-xorg, and then when it says your video card, you would use the free drivers, which would be ati.  Then when you reboot into the system you can reinstall, the restricted drivers for your card.  That is a lot to take in I know.  You could also just keep running the .18 kernel if it is running fine.

---

### Post by philinux on 2008-06-25
In Hardy this
sudo dpkg-reconfigure xserver-xorg

Does not set the video up, only keyboard and mouse.

The friendly recovery has a menu and one option is xfix.

My advice would be use kernel ....18

---

### Post by avtolle on 2008-06-25
Try xfix from the recovery menu and see if that will take care of the problem.

---

### Post by mailtwogopal on 2008-06-25
hi,

  if i can use 18 itself, i have to remove 19 since everytime PC boots, i have to press Esc and hav to select. any way to uninstall kernel 19.

---

### Post by philinux on 2008-06-25
Easy way is to install startupmanager from synaptic then tell it to use 18 each boot. Hopefully kernel ...20 will fix things.

A lot of people with specific hardware have reported lost internet, graphics, sound etc etc.

---

### Post by mailtwogopal on 2008-06-25
> **perlluver said:**
> Ok that is your video card, so you would boot in to the recovery mode of the .19 kernel, and run sudo dpkg-reconfigure xserver-xorg, and then when it says your video card, you would use the free drivers, which would be ati.  Then when you reboot into the system you can reinstall, the restricted drivers for your card.  That is a lot to take in I know.  You could also just keep running the .18 kernel if it is running fine.

i did so and i could not see options related to graphics drivers list. it only asks about keyboard layout again and again and atlast warned "overwriting may.............." and came to command prompt. after this is done i pressed "Ctrl+alt+F7" and logged in and i landed to blank screen. even i tried to login using kernel:18 and it also landed to a white blank screen. now i could not see ubuntu desktop at any version of kernel. please help. am curious and thrilling. thanks in advance. i am posting it now thru booting windows. please help me.

---

### Post by mailtwogopal on 2008-06-26
hi all,

 Kindly help me in recovering my Ubuntu desktop as i lost it and cannot landed there thru any version of Kernel. Please help me. Thanks in advance.

---

