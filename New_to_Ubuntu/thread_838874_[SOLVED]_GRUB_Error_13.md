---
title: "[SOLVED] GRUB Error 13"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by SIXAXIS on 2008-06-23
Hi again guys,

I installed Ubuntu again on my laptop with Windows XP and Windows Vista. Windows Vista screwed over my XP and I messed up my MBR. There was nothing I could do except install Ubuntu and hope GRUB fixes it. It did, partially. I still cannot boot in Windows XP. It gives me the error 13. I don't know what Ubuntu or Vista did, but it may have deleted boot.ini and the ntldr. Is there a way I can confirm that these files were deleted and if they were, how could I fix this without re-installing XP? Oh yeah, I am pretty sure that all my settings are correct. Windows XP is on hda5.

Thanks for the help guys. I appreciate it.

---

### Post by |{urse on 2008-06-23
check this out manG

[http://www.linuxforums.org/forum/gentoo-linux-help/53072-grub-gives-error-13-when-trying-boot-windows-xp.html](http://www.linuxforums.org/forum/gentoo-linux-help/53072-grub-gives-error-13-when-trying-boot-windows-xp.html)

---

### Post by bumanie on 2008-06-23
You may need to try easybcd bootloader from [neosmart]("http://neosmart.net/dl.php?id=1"). It is good at managing a triple boot.

---

### Post by SIXAXIS on 2008-06-24
@|{urse: I already tried that. The partition and drive numbers are correct and so are the settings.

@ bumanie: I am going to try EasyBCD.

Thanks guys!

---

### Post by SIXAXIS on 2008-06-24
Okay, so I used EasyBCD and it worked better than VistaBootPRO, but then I would get the error that hal.dll is missing when I boot up XP. I used the XP Recovery Console and it used "bootcfg /rebuild". That seemed to do the trick.

---

### Post by SIXAXIS on 2008-06-24
I figured it out. I just deleted the Ubuntu partition. Re-installed XP on partition 1 and Vista stayed on partition 2. I ran the Vista DVD and recovered the startup. It automatically added Windows XP and I now have both.

---

### Post by sydbat on 2008-06-24
Well that sucks. What about Ubuntu? IS this something that we have to worry about from Microsoft - Vista messing with installs so you can only have their OS working fully?

---

### Post by SIXAXIS on 2008-06-24
I think I can install Ubuntu now and use GRUB, but after going through hell yesterday, I'd rather not.

---

### Post by sydbat on 2008-06-24
That's too bad. Can I ask why you have XP *and* Vista? Do you like Vista? (not trying to bash Windows, just curious)

---

