---
title: "Ubuntu/Kubuntu live CD does not work"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by chinmoy1955 on 2008-09-18
I received one live Cd each of Ububtu and Kubuntu from Canonical. In my computer, I cant boot normally from the live CD; I just get a blank screen after some booting activity and text screens. But I can boot only when I choose "Safe Graphics" mode.
When I tried to use the CD's on my friend's computer, I could not boot at all, *even in safe mode*. What I get is a screen full of coloured lines. I next booted the PC normally into Windows XP and loaded the CD. From the opening menu I chose to install Ubuntu through windows as a dual booting system. After the installation was completed, I booted and found the new boot menu with Windows and Ubuntu as boot options. On selecting Ubuntu, the few initial text screen are displayed and then the screen freezes with those coloured horizontal lines.
Now my friend wants me to remove Ubuntu from his system and I am not sure how to go about it! There is a folder called Ubuntu (size about 4GB) which I was tempted to delete, but then decided not to since it may render the system un-bootable. Trying to uninstall from the start menu does'nt work. Can somebody help me out of this embarrasing and humiliating situation and help me restore my friend's system to its original condition?

---

### Post by hellion0 on 2008-09-18
Just to clarify, did you finally get Ubuntu installed via Wubi? That's what it sounds like you ended up doing.

Since you tried going through Windows, does Add/Remove Programs in the Control Panel show it as an uninstallable option?

---

### Post by SkippyMarine on 2008-09-18
also on a side note, your graphics card could be a main concern... Getting jumbled graphics is normally due to incompatible graphics drivers within the kernel... what graphics card are you n your mate using?
SkippyMarine

---

### Post by Orange_and_Green on 2008-09-18
Hello chinmoy 1955,

I am sorry you are having all this trouble.

When you boot from the live cd, you could choose "Other Options" from the first screen (after you pick your language), and add the option
```
acpi=off
```
at the end of the line shown.
That **might** fix a couple of things...

---

### Post by chinmoy1955 on 2008-10-01
> **SkippyMarine said:**
> also on a side note, your graphics card could be a main concern... Getting jumbled graphics is normally due to incompatible graphics drivers within the kernel... what graphics card are you n your mate using?
SkippyMarine
Sorry for a delayed reply to your query.
My system has a nVidia GeForce 6200 A-LE (AGP) graphics adapter; my friend's computer also has an in-built graphics adapter from nVidia. These are well known and extensively used graphics cards and I feel Ubuntu should support such well known brands.

---

### Post by chinmoy1955 on 2008-10-01
> **hellion0 said:**
> Just to clarify, did you finally get Ubuntu installed via Wubi? That's what it sounds like you ended up doing.

Since you tried going through Windows, does Add/Remove Programs in the Control Panel show it as an uninstallable option?

Hello hellion0, 
Now what is Wubi?!! You may have noted that I am a newbie in Linux, so I'll feel more at home if you can be more expressive about your suggestion.
I will repeat what I exatly did:
I started Windows, then I inserted the Ubuntu Cd into the CD drive. Autostart took me into some sort of main menu which has a install option. This is supposed to install Ubuntu in tandem with Windows without touching the Windows installation. It creates a Ubuntu folder in the hard disk with all the necessary files and creates a boot menu which shows up when you next boot your system. I am able to boot into Windows from the boot menu, but when I select Ubuntu, I get the garbled graphics and nothing else.
 There is a program group named Ubuntu in the Start menu of Windows which has a uninstall option, but clicking that leads to nothing, there is no response. I hope I have explained the whole thing clearly for your diagnosis. Thanks a lot.

---

