---
title: "Poor Performance"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by bernardocrodrigues on 2013-11-15
Hey everyone,
I'm new to the Ubuntu/Linux environment and i'm facing some performance issues while using Ubuntu compared to what i get when using Windows 8.1. Booting is considerably slow and Ubuntu feels slow as well. Programs take longer to open (compared to windows); i feel some lag while dragging windows around; System settings take forever to apply and even to browse. It feels very strange. A friend of mine who already is familiar to ubuntu said that something is indeed wrong. 

Here is my rig:
CPU: 3370k
GPU: GTX 670
Memory: 16 Gb
Mobo: Sabertooth Z77

Ubuntu version i installed: 13.10 64 bit

I'm running windows 8.1 on a SDD, and i firstly partitioned my 250 gb HDD using windows disk manager (30gb and 220gb) so i could use the 220gb portion as data storage on windows and ubuntu. Then i formated the 30gb partition again when installing ubuntu. The bootloader was intalled on this HDD and i set my bios to primaly boot from it.

When booting Ubuntu sometimes i get a black screen for about 15 seconds only with the cursor flashing. Other times i get the message "Kvm: disabled by bios". And then the ubuntu logo comes up and it takes about another 10 seconds to get to the log in screen. When i log, it takes another 5 secs to show up my desktop.

I've already updated the system to the latest ubuntu version and aditional drivers.

I was thinking, maybe, this had something to do with UEFI or where i installed the boot loader or even the version of ubuntu i chose. Either way, thanks in advance to whoever read this and for any help i get.

Looking forward for aswers!

---

### Post by jdeca57 on 2013-11-15
It's hardly fair to compare startup speed on an SSD with the speed of an HDD. Of course Windows boots 10+ times faster, and of course programs on the SSD start up 10+ times faster...

---

### Post by Mark Phelps on 2013-11-15
Ubuntu is going to take longer to "reboot" than Win 8.1 because when you "shutdown" Win 8.1, it really goes into hibernation. That's know in Win8 as "Fast Startup" -- and it's always going to be faster than rebooting any OS from a cold start.  That's not a reflection on Ubuntu in terms of start times.

Program startup is going to be slower in Ubuntu because you're running it from the HDD instead of the SSD.  Again, not a reflection on Ubuntu performance.

As to the lag, it's likely that you're using open source drivers in Ubuntu, which don't have the level of hardware acceleration that the restricted drivers have -- which is going to show up primarily in display-related activities.

Also, Ubuntu is graphics-intensive if you're using the default Unity desktop.  For faster desktop performance, you should consider replacing Unity with a different desktop.

---

### Post by chris_coulson2 on 2013-11-15
What are the specs on the HDD? Of course, as the previous person mentioned, comparing boot times between an OS on an SSD and HDD isn't fair at all. Had you placed Ubuntu on the SSD and Windows on your HDD, you'd be saying the opposite. SSD's are *considerably* faster than spinning disks, and it's not even close.

If the KVM message bothers you, you can enable virtualization in your BIOS and the message will go away. It will have no negative effects on performance so long as you don't plan on experimenting with Virtualbox/VMWare/other virtualization software.

---

### Post by Impavidus on 2013-11-15
From a 7200 RPM HDD 25 seconds booting time can be considered normal. That's what my laptop does.

---

### Post by QIII on 2013-11-15
"Fast Boot" is more than just hibernation.  OEMs that offer it on their motherboards also have some of the usual POST activities disabled when Fast Boot is selected.

Some boards allow selective disabling of checks or a minimal test routine.

If one were to do that and hibernate a Linux distro, similar boot times would be achieved.

---

### Post by coffeecat on 2013-11-15
Apart from boot times and application response times, you also mention this:

> **bernardocrodrigues said:**
>  i feel some lag while dragging windows around

What video card do you have and are you using the default driver, or have you installed a proprietary driver?

---

### Post by thesleash on 2013-11-15
i would open a terminal and use following command

man top

---

### Post by OrangeCrate on 2013-11-15
My computer boots plenty fast for me. I turn it on, I go get a cup of coffee, and when I get back, it's ready to go. What more could you ask?

---

### Post by chris_coulson2 on 2013-11-15
> **OrangeCrate said:**
> My computer boots plenty fast for me. I turn it on, I go get a cup of coffee, and when I get back, it's ready to go. What more could you ask.

Some people just can't be pleased, I guess! ;)

---

### Post by bernardocrodrigues on 2013-11-15
Thanks for the response everyone! 
I know the incredible performance gain you get when using an SSD however i thought, since i heard that linux OSs were generally faster and lighter than windows, there would be a smaller difference between the to systems. However, since you all think that the booting time i'm getting is plausible and consistent i'm ok with it. I just want to roll out any possibilities of incompatibility with my hardware or something i did wrong when installing.
> [COLOR=#000000]it's likely that you're using open source drivers in Ubuntu[/COLOR]
> [COLOR=#000000]What video card do you have and are you using the default driver, or have you installed a proprietary driver?[/COLOR]
GTX 670. I'm using a driver that is saying "proprietary, tested". I just ran Trine 2 and it is running smoothly. So i think the drivers are ok. Another question now: If i run Trine 2 on windows and in ubuntu and compare the frame rates (considering that both are running the game from a HDD. Will one of the systems get a huge edge over the other? Will it be driver related?
> [COLOR=#000000]KVM message bothers you, you can enable virtualization in your BIOS and the message will go away.[/COLOR]
I already enabled the only virtualization related option in my bios, and i keep getting this message once in a while.

I plan on installing Ubuntu on the SSD later to feel the difference (Will partition the SSD). Will this affect Windows features? Such as the "Fast boot". Or will it be able to work normally?

---

### Post by Mark Phelps on 2013-11-15
> If i run Trine 2 on windows and in ubuntu and compare the frame rates (considering that both are running the game from a HDD. Will one of the systems get a huge edge over the other? Will it be driver related?

If there is a huge difference, they yes, it's primarily the video driver.

---

