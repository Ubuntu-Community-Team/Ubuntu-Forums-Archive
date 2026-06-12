---
title: "i used USB Startup Disc Creator but pc won't boot to ubuntu-11.10-desktop-i386.iso"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by manatarms on 2012-04-19
Good morning everyone, I'm trying to boot Ubuntu 11.1 from my flash drive using USB Startup Disc Creator, but when it says to reboot my pc - it just loads right back into original os. Am I missing a step or something - it seemed like pretty simple instructions to me.

thanx for any help you could throw my way!!

---

### Post by arochester on 2012-04-19
Have you got your computer set to boot from the USB rather than the hard drive?

---

### Post by sudodus on 2012-04-19
Have you checked in the BIOS menu system, that USB is before internal hard disk drive in the boot order?

Sometimes that is not working, because the computer thinks that the USB drive is a hard drive. Then you need to change the order of the hard drives, and put the USB stick before the internal HDD.

If it is still not working, try with unetbootin 
[[COLOR="red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

or the method in this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

Good luck :-)

---

### Post by audiomick on 2012-04-19
I have had the problem, I think it is my laptop that does it, that no matter what I set in BIOS or anywhere else, it will only boot from USB if I manually go into the boot menu every time and point it to the USB medium.

Getting to the boot menu is generally a key-press during boot up, same as getting into BIOS. You'll need to watch your screen during boot to see what it is.

---

### Post by manatarms on 2012-04-19
> **audiomick said:**
> I have had the problem, I think it is my laptop that does it, that no matter what I set in BIOS or anywhere else, it will only boot from USB if I manually go into the boot menu every time and point it to the USB medium.

Getting to the boot menu is generally a key-press during boot up, same as getting into BIOS. You'll need to watch your screen during boot to see what it is.

thanx, audiomick this is my first time working with Linux, :oops: so I'm having trouble getting into (actually, I'm having trouble finding it) the boot menu. I thought I was supposed to press F1 or F10 when I reboot my pc. Actually I tried that during the Dell startup screen and also during the screens after that but I'm not getting anywhere I can point it to the USB medium.:confused:

---

### Post by sudodus on 2012-04-19
> **manatarms said:**
> thanx, audiomick this is my first time working with Linux, :oops: so I'm having trouble getting into (actually, I'm having trouble finding it) the boot menu. I thought I was supposed to press F1 or F10 when I reboot my pc. Actually I tried that during the Dell startup screen and also during the screens after that but I'm not getting anywhere I can point it to the USB medium.:confused:
On my Dell dimension 4600, F2 goes directly to the BIOS menu, and F12 goes to a 'Boot device menu'. So try to press each of those keys (or F9, DEL, or ENTER) at the first splash screen at [re]boot! If that does not help, browse the internet to find out how reach your boot settings.

---

### Post by audiomick on 2012-04-19
> **sudodus said:**
> On my Dell dimension 4600, F2 goes directly to the BIOS menu, and F12 goes to a 'Boot device menu'. So try to press each of those keys (or F9, DEL, or ENTER) at the first splash screen at [re]boot! If that does not help, browse the internet to find out how reach your boot settings.

All of those. I think I have seen F11 and esc as well. The buggers are all different... ;)

---

### Post by manatarms on 2012-04-19
Okay, so I was able to get into the boot sequencer and moved '4 USB Device' up to '1 USB Device' then I save & exit. However, when I reboot I get the following error;

Unknown Keyword in configuration file.
Boot:

---

### Post by sudodus on 2012-04-19
> **manatarms said:**
> Okay, so I was able to get into the boot sequencer and moved '4 USB Device' up to '1 USB Device' then I save & exit. However, when I reboot I get the following error;

Unknown Keyword in configuration file.
Boot:
One big step forward :KS

Now, if the USB Startup Disc Creator does not create a working system, try with ***unetbootin*** 
[[COLOR="red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

or the method in this link (basically ***cloning*** with dd)
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

Good luck :-)

---

### Post by manatarms on 2012-04-22
> **sudodus said:**
> One big step forward :KS

Now, if the USB Startup Disc Creator does not create a working system, try with ***unetbootin*** 
[[COLOR="red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

or the method in this link (basically ***cloning*** with dd)
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

Good luck :-)

I had trouble installing Unetbootin, plus I haven't the experience to figure out how to go about putting into action what that second link was explaining. 

Anyway, to make a long story short, I found my dvd burner and burned myself a disk. So, I'm marking this thread as solved. Thanx everyone for the help.

---

