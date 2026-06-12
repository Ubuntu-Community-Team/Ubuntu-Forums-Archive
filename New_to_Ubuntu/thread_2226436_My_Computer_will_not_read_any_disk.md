---
title: "My Computer will not read any disk"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by lewis4 on 2014-05-27
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I'm new to Linux Ubtuntu, so I hardly know what to do when something's broke. My computer will not pick up/read any disk that I put into my disk drive. As i'm no smart person when it comes down to these breaks & errors I'm hoping you guys can help me solve this problem.[/COLOR]

[COLOR=#000000]Help me please![/COLOR]

---

### Post by sandyd on 2014-05-27
Moved to absolute beginners section

---

### Post by stalkingwolf on 2014-05-27
the first thing to do is to check the one time boot menu and see if the disk drive shows in the menu.  watch when first booting , it should tell you what key to use to get this menu.  as far as i know there is no rule as to which key, ive seen F8,F9,F10,F12, esc and del.
If it wont read any disk it sounds like a hardware issue.   Bad drive, bad cable missing driver.
You can also run the recovery mode and fix  broken packages.  That is usually the second option in the grub menu.

---

### Post by squakie on 2014-05-27
Maybe you can explain more by giving an example.  I assume we are talking about CDs or DVDs?  When does this happen - when you are trying to boot, when you are running and want access to a CD or DVD?  Are you trying to play a commercial DVD and that's what isn't working?  Too many unknowns.

---

### Post by lewis4 on 2014-05-28
> **squakie said:**
> Maybe you can explain more by giving an example.  I assume we are talking about CDs or DVDs?  When does this happen - when you are trying to boot, when you are running and want access to a CD or DVD?  Are you trying to play a commercial DVD and that's what isn't working?  Too many unknowns.

 Yes yes I am. I have a problem with Ubuntu 14 with the Network Interface, as I am going to be starting up a Modded Minecraft server.I have read some of the way's to enable/make/run a static ip, but when I go into my interface nothing is there, where as on the videos/tutorials on YouTube & the forums there interface has stuff in it and I believe I have mucked something up somewhere and I'd like to reinstall Linux Ubuntu.

---

### Post by lewis4 on 2014-05-28
> **stalkingwolf said:**
> the first thing to do is to check the one time boot menu and see if the disk drive shows in the menu.  watch when first booting , it should tell you what key to use to get this menu.  as far as i know there is no rule as to which key, ive seen F8,F9,F10,F12, esc and del.
If it wont read any disk it sounds like a hardware issue.   Bad drive, bad cable missing driver.
You can also run the recovery mode and fix  broken packages.  That is usually the second option in the grub menu.

I don't think it is a hardware problem, this laptop I am currently using cost 2K, & on windows 8.1 the disk registered as in the CD/DVD bay. I hate windows 8.1, that's why I changed to Linux.

---

### Post by squakie on 2014-06-01
Let's see - you've checked the boot order in the BIOS to be sure the optical drive is before the other drives, right?  You've checked the BIOS to see what it is showing for drives - your optical drive is not disabled, right?  I don't think that the interfaces file normally has anything in it, or if it even exists by default.  I know when I went to set up static IP I had to create the contents of the interfaces file.  I also see you are talking about Minecraft - have you done anything on this PC with that yet?  Has it somehow locked the optical drive?

---

