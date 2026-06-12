---
title: "[hardy] Computer unusable after monitor turns off"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by altonbr on 2008-04-27
On my girlfriends computer, she has a problem where whenever the monitor turns off: It can not be turned on (or activated) with the mouse or keyboard (unlike my computer). I checked her screensaver and power management settings through System > Preferences > Screensaver and System > Preferences > Power Management and all seems fine.

The screensaver is set to activate after 30 minutes and the monitor it set to turn off after 50 minutes. The screen is NOT set to lock.

I have even tried to kill the GNOME session (Ctrl + Alt + Backspace) and switch to tty1 (Ctrl + Alt + F1) and neither seem to activate the monitor.

Is their a configuration file I can look at (or destroy) to reset her preferences?

She is running Hardy, upgraded from Gutsy. She said that this occurred in Gutsy but rarely as often as it does now in Hardy (which is every time).

---

### Post by fsamuels on 2008-04-28
I am having screensaver lockups on Hardy myself (after upgrading from Gutsy). Try disabling the screensaver completely and see if it still happens. On my system I have an ATI Radeon x300 with 2 monitors. As soon as the screensaver pops up, it blanks my main monitor and my second monitor stays the same. I can move the mouse but keyboard and mouse clicks do nothing. I have to restart the machine. I can't seem to even edit the screensaver anymore from System -> Preferences -> Screensaver because it comes up with empty boxes. My only solution at this point is to kill 'gnome-screensaver'.

---

### Post by altonbr on 2008-05-01
Yup, I had to result to disabling the screensaver as well. Her machine has no real GPU, only an embdedded VIA chip.

I'll look into posting a bug on Launchpad... :(

---

### Post by BorisDBlade on 2008-05-01
I have a Toshiba laptop, mine turned off the disks and monitor after 1 hr. nothing would let it come back up. I had to remove my battery and bootup on ac power. I was very close to cracking it open to see if I fried my proc as it would not even boot up bios after turning it off. Know it doesn't help much, but I ended up leaving any power saving setting off for now.

---

### Post by Canis familiaris on 2008-05-01
This is mainly an ATi problem in my belief try installing the latest graphics drivers using [Envy]("http://albertomilone.com/nvidia_scripts1.html") and see whether that solves the problem.

---

### Post by Canis familiaris on 2008-05-01
> **altonbr said:**
> Yup, I had to result to disabling the screensaver as well. Her machine has no real GPU, only an embdedded VIA chip.

I'll look into posting a bug on Launchpad... :(

Oops didn't see that it was VIA chipset problem. You can Ignore my previous post.
You can however try this:
Go to Command line: (crtl+alt+f1)
```

sudo dpkg-reconfigure xserver-xorg
```

and in the video card choose Vesa.

---

