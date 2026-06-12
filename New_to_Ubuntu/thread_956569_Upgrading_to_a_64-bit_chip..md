---
title: "Upgrading to a 64-bit chip."
date: 2008-10-23
forum: New to Ubuntu
---

### Post by jasontu on 2008-10-23
I recently got an Intel Core 2 Duo E8400 to replace my Intel 4 540.  It will arrive right around the day that 8.10 is released.  It is a 64-bit chip as opposed to my current 32-bit chip, and I have several questions.

Firstly, am I correct in assuming that a 64-bit chip will run the 32-bit version of the OS just fine?

Secondly, I also assume that one cannot upgrade to a 64-bit version of a 32-bit install.  I have everything *just right* now.  Is there any way can preserve all the work I've put into getting all the schmancy graphical flair, etc. from my current install?

Thirdly, is there anything I should be wary of or careful about when changing out the CPUs?  For example, if I got the chip today, could I just pop it into the motherboard and have Ubuntu boot up just fine?  Windows tends to have fits about stuff like that.

Lastly, how much more awesome is the 64-bit version of the OS?

Thanks!

---

### Post by neurostu on 2008-10-23
1st. YES! 32bit Ubuntu will run fine on a 64bit CPU (I'm doing it now)

2nd. NO, the only way to upgrade from 32bit to 64bit is to reinstall the OS. You can preserver your settings by creating a seperate /home partition and then when you reformat / and install a new OS the /home partition is preserved

3rd. If your motherboard supports the new CPU then you shouldn't have any issues with Ubuntu.  If you have never changed a CPU before its pretty simple but it can be easily screwed up. I would recommend talking to someone who has done it before and watching a few videos on the net to get a good idea of how to do it.  Again though before you unwrap the CPU make sure it is supported by your Motherboard.

64bit version is better b/c it supports more ram, has a slight performance increase and 64 bit application are much faster then 32bit applications.  The average user won't see a difference between the two.

---

### Post by hyper_ch on 2008-10-23
> **jasontu said:**
> Firstly, am I correct in assuming that a 64-bit chip will run the 32-bit version of the OS just fine?
yes

> **jasontu said:**
> I have everything *just right* now.  Is there any way can preserve all the work I've put into getting all the schmancy graphical flair, etc. from my current install?
Very simple:
backup your /home and /etc folder und make a backup of all install packages, reinstall ubuntu with 64bit, put back the /home and /etc folder, start installing all the packages again...

> **jasontu said:**
> Thirdly, is there anything I should be wary of or careful about when changing out the CPUs?  For example, if I got the chip today, could I just pop it into the motherboard and have Ubuntu boot up just fine?  Windows tends to have fits about stuff like that.
I think you also have to replace your motherboard... be sure that you are not statically charged... besides that, don't use too much cooling gel on your cpu, just a very light cover

> **jasontu said:**
> Lastly, how much more awesome is the 64-bit version of the OS?!
Depends on what you do :)

---

### Post by jasontu on 2008-10-23
Thanks for the help everyone!

Based on what you say I think I'll stick with the 32-bit install I already have.  I mostly use my PC to do office, web, and WoW via Crossover Games.  If I decide to try the saving of /home and /etc thing I'll search around here for details.

My current motherboard supports the new CPU but I have to make a BIOS update, which frankly frightens me more than getting the chip into the board.  I've installed many CPUs, but the whole update your BIOS and then overclock the FSB thing still scares me even though it is suggested by the manufacturer.

Thanks again all!

---

### Post by Paqman on 2008-10-23
> **jasontu said:**
> 
Thirdly, is there anything I should be wary of or careful about when changing out the CPUs?

Be *extremely* careful when handling the chip. You absolutely must not touch any of the pins with your bare hands, the static charge on your body will damage the chip, and shorten it's lifespan.

Get yourself an anti-static wristband, you should be able to pick one up at any electronics store, and it'll protect the investment you've made in the chip. Clip the wristband to the chassis of the PC as soon as you open the side panel. That goes for changing RAM, graphics cards, mobos, etc as well.

Other than that, be careful not to bend any pins, and as mentioned, go very lightly with the thermal grease.

---

### Post by jerome1232 on 2008-10-23
> **jasontu said:**
> 
Thirdly, is there anything I should be wary of or careful about when changing out the CPUs?  For example, if I got the chip today, could I just pop it into the motherboard and have Ubuntu boot up just fine?  Windows tends to have fits about stuff like that.


Since you are going from single to dual core, I would check and make sure your bios supports dual core, some older bios's  had to get upgraded (flashed) to work with them. 

I believe both of those processers are LGA775 sockets but you'll want to check that as well, if they are different you won't be able to physically fit the new one on. 

You might want to take cooling into consideration, make sure your old fan is adequate to keep this new cpu cool. Make sure you have some thermal paste/grease/silver to apply to the cpu before placing the fan on it.

---

### Post by neurostu on 2008-10-23
> **jasontu said:**
> Thanks for the help everyone!

Based on what you say I think I'll stick with the 32-bit install I already have.  I mostly use my PC to do office, web, and WoW via Crossover Games.  If I decide to try the saving of /home and /etc thing I'll search around here for details.

My current motherboard supports the new CPU but I have to make a BIOS update, which frankly frightens me more than getting the chip into the board.  I've installed many CPUs, but the whole update your BIOS and then overclock the FSB thing still scares me even though it is suggested by the manufacturer.

Thanks again all!

BIOS updates are simple but potential fatal.  I upgraded the BIOS on a machine once only to have it brick my ethernet adapter. I wasn't sure what caused the problem until I tried going back to the old BIOS.  I was lucky frequently upgrading to the wrong BIOS can brick the MOBO beyond repair.

It certainly isn't a difficult thing to do just make sure you read all the documentation provided by the manufacturer.  If you have already ordered and payed for the new CPU I would go ahead and upgrade the BIOS and install the new CPU.

---

