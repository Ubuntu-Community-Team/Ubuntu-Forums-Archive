---
title: "laptop trouble- help please"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by jadedoll on 2008-06-04
okay, so i've previously triple- booted ubuntu, XP, and suse on my desktop (so i know how to basically install and partition it)...but i have recently gotten an HP Pavilion tx1000us and i put in my ubuntu (7.04) cd and when it started up the screen turned brownish and looked like an ooze was spreading across it...i have no idea what happened and i almost had a panic attack...the laptop wouldn't turn off using the power button, so i had to take out the battery and manually open the cd drive...vista still works fine, but what happened and what do i do to get ubuntu to work??      :confused:

---

### Post by abn91c on 2008-06-04
If vista works ok and the screen is fine now, then its the video card that ubuntu does not like. people here sem to have trouble with ATI drivers and cards if that is what you laptop has. just search here in the hardware forum for help

---

### Post by Lord Xeb on 2008-06-04
Use 7.10 It worked like a charm on my machine. I have an IBM T43 (which was the last 'IBM' model made before Levono came in) and it has an ATI X300 graphics card in it. The only problem though is to get the restricted drivers to work. That can be done by downloading the 'resrticted drivers manager' in synaptic package manager.



Hope that helps.

---

### Post by spiderbatdad on 2008-06-04
Have a look at a Vista/Ubuntu dual boot guide, or two: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Burn your Vista recovery DVD.

My understanding is that vista requires it's own partitioning tool. I have heard others say gparted will do the job just fine. I haven't tried, so I can't vouch for that method, and don't know how it could affect any warranty you have.

Was your bios set to boot from cd as first option?

---

### Post by jadedoll on 2008-06-04
thanks, i will check it out

---

### Post by jadedoll on 2008-06-04
> **spiderbatdad said:**
> Have a look at a Vista/Ubuntu dual boot guide, or two: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Burn your Vista recovery DVD.

My understanding is that vista requires it's own partitioning tool. I have heard others say gparted will do the job just fine. I haven't tried, so I can't vouch for that method, and don't know how it could affect any warranty you have.

Was your bios set to boot from cd as first option?
well i was already in vista, and then put in the disk and restarted the computer so it would open automatically in ubuntu

---

### Post by spiderbatdad on 2008-06-04
You said 7.04...that has to be booted into. 8.04 has a wubi installer disk that can be installed and run from within your vista installation.

---

### Post by jadedoll on 2008-06-04
> **spiderbatdad said:**
> You said 7.04...that has to be booted into. 8.04 has a wubi installer disk that can be installed and run from within your vista installation.
no (because i believe you don't have to set up partitions with that, correct?) and i used the same disk on my desktop and set everything up

---

### Post by jadedoll on 2008-06-04
oh...yeah it's 7.04

---

### Post by spiderbatdad on 2008-06-04
All the information you need is here:[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by jadedoll on 2008-06-04
oh, thanks so much! the other link you suggested seems very helpful as well...i guess the problem is my unfamiliarity with dual booting with vista, thanks again

---

