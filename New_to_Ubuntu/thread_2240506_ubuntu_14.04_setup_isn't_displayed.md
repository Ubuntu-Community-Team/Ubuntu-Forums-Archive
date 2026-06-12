---
title: "ubuntu 14.04 setup isn't displayed"
date: 2014-08-20
forum: New to Ubuntu
---

### Post by engineer2 on 2014-08-20
[SIZE=2]Hello guys 
i'm trying to install ubuntu 14.04lts on dell desktop but i'm having problem after booting when the installation should startup  dell monitor entered into standby mood and do not display anything.
this problem happens with desktops only .everything is fine with laptops 
please help I really need a solution for this problem  :(:(:confused:[/SIZE]

---

### Post by fantab on 2014-08-20
What graphics card do have on "desktops"?

Try [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997") kernel option at boot... 'nomodeset' boots Ubuntu in 'fail-safe graphics mode'. Later, after installing Ubuntu, you will have install the appropriate graphics driver.

---

### Post by sp40140 on 2014-08-20
Does the Desktop have any Operating system installed right now? what are the hardware specs? specifically Vid cards?
When you boot with install media.. are you able to see the boot process.. anything on the screen?
Are you trying to install 32 bit or 64 bit (this might not be relevant though).

---

### Post by engineer2 on 2014-08-20
[[COLOR=#000000]sp40140[/COLOR]]("http://ubuntuforums.org/member.php?u=1931408")

the desktops have windows 7 installed on different partition ,for the booting everything is fine until the stage where the secreen with (try ubuntu ,install ubuntu) suppose to appear but it does not.and i'm installing 64bit

---

### Post by Sanctimonious_Ape on 2014-08-20
Yeah, sounds like graphics driver is running the card in a mode your monitor doesn't support so it's refusing to try to display it.  Have you tried the "nomodeset" option yet?  Also, what's the "sp40140" at the top of your previous post?

---

### Post by engineer2 on 2014-08-20
[COLOR=#DD4814][COLOR=#000000][Sanctimonious_Ape]("http://ubuntuforums.org/member.php?u=1939764")
that's a name just like yours it means i'm replaying to that person's question and for the nomodeset i haven't try it yet it needs some reading from me bcoz i have no idea what is it exactly and how and what it does since i'm a total new in ubuntu .

but i'll try it  [/COLOR][/COLOR]

---

### Post by grahammechanical on 2014-08-20
To modify the live session boot parameters:

1) at the first purple screen with the icons of a keyboard and a human, press Enter
2) at the language selection screen select the language (English default) and press Enter
3) at the underlying screen with the options to Try Ubuntu - Install Ubuntu press F6
4) a small menu will appear at the bottom right of the screen. From the list select nomodeset and press Enter
5) press Esc to return to the Try Ubuntu - Install Ubuntu screen. Make your selection and press Enter.

This link shows some images. See Section 6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Sometimes we need to use a combination of these F6 options to get a live session running.

Regards.

---

