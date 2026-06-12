---
title: "best distro for pentium 4?"
date: 2008-03-06
forum: Other OS Talk
---

### Post by myusername on 2008-03-06
hi i was wondering what the best distro optimized Pentium 4? (512 ram 64 video 2ghz processor) i would want something based on Debian and generally easy to install or should i just use a different kernel for Ubuntu? if so can somebody point me in a direction of a kernel how to?

Thanks

---

### Post by fedex1993 on 2008-03-06
well i use debian on my server its a pent 4 1gb of ram but if that is not light enough use puppylinux or xubuntu or there is also damn small linux

---

### Post by adityakavoor on 2008-03-06
ubuntu 7.04 is best till date

---

### Post by tgalati4 on 2008-03-06
Linux Mint 4 XFCE will be stylin' on a 2 GHz P4.

---

### Post by myusername on 2008-03-06
i have tried all of those (except puppy)
i was just wondering if there was one that could use ALL my processing power

---

### Post by jrusso2 on 2008-03-06
I have a Pentium 4 ghz with a gig of ram and it runs any linux distro just fine.

Long as you have enough ram the P 4 has enough CPU.

Not sure what graphics card you have but that might limit things like compiz fusion if you don't have an nvidia or ati card.

---

### Post by Tux Aubrey on 2008-03-06
I'm not sure what you are getting at.  A P4 2.0Ghz is a perfectly adequate machine for most 32 bit distros.  Unfortunately, I am finding that many of the non-ubuntu Debian desktop distros are poorly maintained or buggy.  Your machine should run well with something like Xubuntu and would fly with Fluxbuntu.  My personal, idiosyncratic choice would be a minimal Ubuntu install with E17 - the OzOs desktop package is great for me.  Then I just add the particular apps I want from the Ubuntu/Oz repos.

---

### Post by sandysandy on 2008-03-06
Has anyone tried gOS (google Operating System) - not officially supported by google but with lots of google apps.

regards

---

### Post by vishzilla on 2008-03-06
> **sandysandy said:**
> Has anyone tried gOS (google Operating System) - not officially supported by google but with lots of google apps.

regards

I believe its greenOS. Any XFCE or E17 distro will work terrific like Xubuntu, gOS, OzOS etc

---

### Post by myusername on 2008-03-06
thanks for the replys but i was wanting something i686 optimized. ubuntu is made for i386 and up therefore it has a wider range of support but slows down the capabilities of an i686 processor (my processor)

using an i386 distro on an i686 processor is like using a 32bit operating system on a 64 bit processor

---

### Post by p_quarles on 2008-03-07
> **myusername said:**
> using an i386 distro on an i686 processor is like using a 32bit operating system on a 64 bit processor
You were apparently misinformed. i386 refers to a large family of chips with a common architecture. You can rest assured that any modern Linux distribution is optimizing its prepackaged kernels to run on equally modern computers.

Try running Ubuntu 7.10 on an actual Intel 386 processor, and you will see that it is most definitely not optimized for that. It's doable, but it takes a lot of optimization before you would even get it to begin working. 

The Pentium 4 is a very common chip, and while it's a few years old, it is still widely used. It's definitely going to get its resources used efficiently in any well-designed and -maintained distro. 

If you're not getting the best performance from the chip, it most likely has nothing to do with the kernel. You could always try compiling your own, but I would first look for dust in the area of the CPU. Pentium 4s have pretty lousy power management, and can easily overheat (and start scaling down) if the insides of the case are not kept clean.

---

### Post by mips on 2008-03-07
> **myusername said:**
> thanks for the replys but i was wanting something i686 optimized. 

Then go for Arch which is i686 optimized. If you are willing to read the installation wiki then it is not hard to install. Package manager is better than debians. There is no default desktop, you choose your own. If you like kde rather use kdemod.

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)
[http://kdemod.ath.cx/](http://kdemod.ath.cx/)

---

### Post by SunnyRabbiera on 2008-03-07
> **myusername said:**
> i have tried all of those (except puppy)
i was just wondering if there was one that could use ALL my processing power

Huh?
Your way of thinking on this bit is a bit wrong in my opinion sorry to say, Linux is not like XP where it sucks power from the processor for no real reason.
No it utilizes the minimum of the chip thus making it last longer and not fry it like an egg.
Hey I have as P4 on this puppy here, never had one issue with ubuntu at least concerning speed, power and efficiency.
Also I feel you are mislead by the i686 processor thing, you know that the packages in the repos are practically universal right?
Like I said have a P4 here too... never had an issue with it.
How old is yours, mine is a P4HT Cedar Mill/Prescott (from the year mine was made in)

---

### Post by myusername on 2008-03-07
mips- i was gonna try arch but i didn't know how hard it would be to install my wireless card (wusb54gc) that is why i wanted a debian based because i would know how to fix it.

SunnyRabiera- i have got the Essex model but according to wikipedia that model doesn't exist so i don't know how old it is....i just want something fast and looks good (perferably gnome)

thanks for all the replies

---

### Post by mips on 2008-03-09
> **myusername said:**
> mips- i was gonna try arch but i didn't know how hard it would be to install my wireless card (wusb54gc) that is why i wanted a debian based because i would know how to fix it.


What chipset does that card use?

---

### Post by SunnyRabbiera on 2008-03-09
> **myusername said:**
> mips- i was gonna try arch but i didn't know how hard it would be to install my wireless card (wusb54gc) that is why i wanted a debian based because i would know how to fix it.

SunnyRabiera- i have got the Essex model but according to wikipedia that model doesn't exist so i don't know how old it is....i just want something fast and looks good (perferably gnome)

thanks for all the replies

Yeh but I have ubuntu installed on computers with older P4's and no issues there.
I just gave ubuntu to someone with a computer dating back to when the p4 was initially made and there are no issues there.

---

### Post by myusername on 2008-03-09
i tried arch didn't like it much but it was fun to setup and my wireless card worked (its a linksys WUSB54GC with the rt73usb chipset) it wasnt noticable faster than ubuntu so i reinstalled gutsy and went with the hardy kernel (which is awesome imo) so yeah thanks for all the posts but for now, i'll stick with good ol' ubuntu

---

