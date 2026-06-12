---
title: "Screen Res problem"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by arseniy on 2008-04-28
I was editing xorg.conf (in /etc/X11) to add right-click and stuff to my MacBook's Synaptics touchpad, and then I logged out and back in (so the changes would take effect), and I got an 800x600 screen. It's supposed to be 1280x800 (macbook 13" core 2 duo), and I tried to change the res in (System -> Preferences -> Screen Resolution) but all I could choose is 800x600. What do I do? Thanks in advance for help!

---

### Post by dokdoom on 2008-04-28
Please tell me that before you made any changes to your xorg.conf that you backed it up?

---

### Post by arseniy on 2008-04-28
:( No... stupid decision?

How do I fix it?

---

### Post by dokdoom on 2008-04-28
I wouldn't say it was a stupid decision unless you knew better. If I were you I would run

dpkg-reconfigure xserver-xorg

This will take you through a wizard like setup for your xserver ultimlatey crafting your new xorg.conf

Most of the questions they ask you will tell you which one to choose and also the default answer may be your best solution. Through this you will be able pick the correct resolution, then bring you back to a point before your xorg files was messed up. Now before you make any changes to that file you need to back it up.

sudo cp /etc/X11/xorg.confg /etc/X11/xorg.conf.back

Now when you make changes, and say X doesn't start, or your resolution is not functioning properly you can simply revert back by typing

sudo cp /etc/X11/xorg.conf.back /etc/X11/xorg.conf

Sometimes when you do mess up your xorg.conf it won't give you X, it will just kick you to the terminal. That is where you run that command to copy your working xorg over the bad xorg.

---

### Post by arseniy on 2008-04-28
I ran ```
dpkg-reconfigure xserver-xorg
``` and all I was asked was to configure the keyboard and mouse. Nothing about the display at all. So I looked on google, just for the heck of it, and found this:

```
Add the following code to the Display section.

SubSection “Display”
	Depth 24
	Modes “1280×800&#8243; “1024×768&#8243; “800×600&#8243; “640×480
EndSubSection
```

I did that, and nothing worked. I also tried it without that extra thing of code, and it still didn't work. Any other ideas? Maybe I'm doing something wrong...

---

### Post by arseniy on 2008-04-28
Whoops never mind, got it. I booted into recovery mode, and made it autodetect the devices in that third option (something like "Autoconfigure x-server" - it sounded right so I did it). And it worked! Thanks for trying to help though :)

---

### Post by mapes12 on 2008-04-28
Hi Arseniy

Could you post exactly what you did to get your screen res working please. I have the same problem.

Thanks in advance.

Mark

---

### Post by arseniy on 2008-04-29
Yeah sure. When the laptop boots, watch GRUB. When it says 'press ESC for menu...2...1" press ESC. Choose the first Recovery Mode option you see, and press Enter. Then choose that third option called something like 'autoconfigure xserver' and let it go. Then choose the first option that's like 'continue booting normally'. There ya go!

---

### Post by ubuntu-freak on 2008-04-29
Also, in desktop-mode you can run:
 
**gksudo displayconfig-gtk** 
 
and in Kubuntu:
 
**gksudo displayconfig**
 
to set and force your correct resolution.
 
Nathan

---

