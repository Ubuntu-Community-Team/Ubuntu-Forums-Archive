---
title: "[SOLVED] I killed a hard drive"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by telltommy on 2008-10-21
with my stupidity. I have an old computer in the basement i thought i'd make use of. So i put in a good hd and booted up to see what was on it. Big mistake, i should have put the Ubuntu install cd in first.  Now I can't install Ubuntu because i get this message as i boot:

"Busy Box V1.1.3 (Debian 1:1.3 Ubuntu12)
Built in shell (ash)
enter help for list of built-in commands. (initramfs) [56.096411] ata 1.00: exception Emask 0x0 Sact 0x0 Serr 0x0 action ox2 Frozen.
[56.096466] ata 1.00 cmd c8/00: 08:00:00/00:00:00:00/EO tag O dma 4096."


I have no idea what to do next. Is this hd ruined?

---

### Post by louieb on 2008-10-21
Provided you plugged it in correctly probably no harm done to the drive. 

The busy box prompt just meant there is a problem. Could be a bad burn of the CD or not enough memory to load the CD. or some type of hardware that requires the use of boot codes.  [BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions") 

What kind of PC? What kind of hard drive (ide or sata)?  How much memory?  Might try a lightweight distro such as DSL or Puppy.

---

### Post by telltommy on 2008-10-21
thanks for the reply. The pc is a 3.2 gb 512mb ram 160gb hd. the hd is ide. I don't know the other terms you're using (distro, dsl, puppy) beyond my know how. I need real beginner advice. thanks
I tried all the boot options (f6) but i get the same reponse, something wrong with the hd or it's buffer, frozen, etc.

---

### Post by louieb on 2008-10-21
Sure sounds like you have a bad CD. The CD should boot even if there was no hard drive at all. Run the check media for defects option. 
I burn mine at 2x no faster that 4x. [BurningIsoHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BurningIsoHowto") 

That PC has plenty of memory and power to run the Ubuntu live CD.

"distro"  is short for Linux distribution.  **Puppy** and** DSL** are distributions that  need less memory than Ubuntu.  [DistroWatch.com: Use Linux, BSD.]("http://distrowatch.com/") 

Another check you can make is run  memtest form the live CD. Just start it up and let it run.  Come back later and see if finds anything. 

If you think the hard drive is bad - go to the manufactures website and download their hard drive diagnostic utility.

---

### Post by bobpur on 2008-10-21
With those specs that computer should have some life left in it. I'd check [www.crucial.com](www.crucial.com) and find out how much memory it will hold and max it out if the benefits of doing so outweigh the money involved.

I agree with the others about checking out the cd and, maybe, burn a new one. One other thing you might check is that there may be a reason that computer was placed in the basement. 

Good luck.

---

### Post by telltommy on 2008-10-22
cd is fine. I put in the backup hd from my main computer and it formatted and loaded Ubuntu with no trouble. This is a hd problem that happened after i put in the drive and started the old computer. After that i was unable to install Ubuntu.

---

### Post by alwez_loner_TZ on 2008-10-22
If you think its that hard disk then maybe you can put the hard disk to you PC that you use if it does not work then trash the hard disk. But you never know it could be a lot of things....

---

### Post by telltommy on 2008-10-22
I don't know how to thank you all enough. It was the hd. One pin not making good contact. I discovered it when i used Seagates tools. thanks again and i'll mark this solved.

---

