---
title: "Gfxboot for Ibex?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by xreaper on 2008-12-02
Hey everyone ^^ just me here, wondering about gfxboot. I have previously managed to get gfxboot working well with a dual boot of Hardy Heron and XP, but now that I have upgraded to Intrepid Ibex, I have been stopped at every attempt to get it working properly. The main problem is something to do with not having the right program to read stage1.

I am now, back at square one with no gfxboot files on my computer. Can someone please point me in the right direction? Thanks in advance to anyone who can help ^^

---

### Post by mano cazalet on 2008-12-02
It should work with a newer version of [grub-gfxboot]("http://sidux.com/debian/pool/main/g/grub-gfxboot/")

---

### Post by xreaper on 2008-12-02
hey, I have tried the previous suggestion and I have managed to get most of it working, but now instead of it loading the message file. it comes up with an 'invalid file format' error and then proceeds to the normal text based grub boot menu. can anyone please help me there?

---

### Post by lowtolerance on 2008-12-10
Have you tried different message.xxxx files? I was receiving the same error with some themes, but others work fine.

---

### Post by mjpoetic on 2008-12-10
> **lowtolerance said:**
> Have you tried different message.xxxx files? I was receiving the same error with some themes, but others work fine.

Which ones worked for you? I am having the same "invalid file format" problem

---

### Post by lowtolerance on 2008-12-10
I've had luck with the standard gfxboot-theme-suse package, the "debianorange" theme on kde-look.org, as well as the "da vinci" theme, also on kde-look. unfortunately, i don't really care for any of them, but they work and you should be able to swap out the back.jpg with no trouble. also, the "da vinci" theme's message file has a menu.config in it if you unpack it, and in there you can tweak some settings, which i haven't seen on other themes. 

Hopefully those will work for you guys. They aren't the greatest, but may be better than nothing?

---

### Post by mjpoetic on 2008-12-15
Thanks, got it semi-working now...just a few kinks I want to work out and personalize.  I really like the Da Vinci theme but I can't get it working properly because it's for a 1280x800 widescreen and I have a 1680x1050 widescreen.  I am going to fool around with the values in the config file and see what happens.  Wish me luck!

---

### Post by Malac on 2009-04-26
I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111196[/ATTACH]

Hope this helps

---

### Post by karllv on 2009-04-26
> **Malac said:**
> I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111196[/ATTACH]

Hope this helps

9.04 or 8.10?

---

### Post by Malac on 2009-04-27
> **karllv said:**
> 9.04 or 8.10?
Both, done the same way on two machines.
Followed the original how-to except with the newer grub-gfxboot deb
and added the grub-install command,
i.e.: sudo grub-install /dev/sda
Yours may be a different dev.
These are not 64-bit machines though for that you would need to patch and compile the grub-gfxboot original tar.

Hope this helps.

---

