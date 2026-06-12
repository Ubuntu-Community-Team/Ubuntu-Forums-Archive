---
title: "Text not being rendered"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by Loki*PI on 2011-12-01
Hi:  I just did a fresh install of Oneiric. Having trouble with text not being rendered. This is across several applications, various places on the desktop, and even the login screen. Complete letters are not formed. A lower case t just has the top point and right arm. A c is only a small segment of curve from the top, etc.

This isn't happening everywhere, mostly desktop, tomboynotes, etc. Email is clear and browser text is normal. 

Wondering if I am missing a font or something? I've search the forum and seen lots of complaints about not being able to change fonts, but haven't seen this problem mentioned.

Current on all updates.

Any ideas anyone?

Thanks

---

### Post by fantab on 2011-12-01
It is a strange one. Try Gnome-Tweak-Tool to customize fonts.

What type of Monitor do you use, LCD?

---

### Post by Loki*PI on 2011-12-01
It is a no-brand LED monitor but I've been using ubuntu on it for 3 or 4 years no problem. This just started with Oneiric.

I'll look at tweak-tool.  Thanks

---

### Post by corncob on 2011-12-01
I'm experiencing this on Google Earth on Oneiric.  This is the only app that I have this problem with.  Changing fonts didn't help.  Funny thing, I installed it on my friend's computer (Oneiric also) and it doesn't have the problem.  Maybe I'll try reinstalling it.

---

### Post by satanselbow on 2011-12-01
> **corncob said:**
> Maybe I'll try reinstalling it.

I had the same on a clean LM12 install - rebooted to clear it and it has not returned ;)

Pretty sure it only manifested itself after a batch of updates so probably a Xorg(?) config needed flushing with the boot :confused:

---

### Post by Loki*PI on 2011-12-14
Installed 'Advanced Settings' and changed fonts and font sizes a couple times but I'm still having the problem. I am not seeing a pattern where the partially formed letters occur, it seems to happen across all applications and screens but not every letter. For example in an email the header maybe clear but in the body of the email the letters will be only partly formed. Sometimes in terminal letters will be incomplete, then with the next launch it is ok.  

Any ideas other as to whats wrong?

---

### Post by Loki*PI on 2011-12-17
I am still trying to resolve this. It seems to come and go, sometimes the text is so broken it cannot be read even in terminal, browsing, and email. Other times it is minor effecting mostly capital letters. Example: capital N will look something like  ' '  

I've tried several fonts and different sizes but the problem is consistent.

---

### Post by fantab on 2011-12-17
> **Loki*PI said:**
> I am still trying to resolve this. It seems to come and go, sometimes the text is so broken it cannot be read even in terminal, browsing, and email. Other times it is minor effecting mostly capital letters. Example: capital N will look something like  ' '  

I've tried several fonts and different sizes but the problem is consistent.

 Have you tried adjusting HINTING from Advance Settings-Fonts?

Do you use any proprietary Graphic Drivers? If yes, try reinstalling those. 

If you are on desktop, I suggest you check the Monitor Cable. Also check other cables for any loose connectivity. 

If the above seem to check Okay then try reinstalling Ubuntu.

If the problem still persists contact the Monitor support service, it could be the monitor issue.

---

### Post by corncob on 2011-12-17
Do you have another monitor and cable you could try?

---

### Post by Loki*PI on 2011-12-17
Wow fantab, I have no idea what hinting is but I played with that and a couple other settings in Advance Settings Fonts and it seems to have cleared up the problem.

corncob,thanks for the suggestion.

---

### Post by fantab on 2011-12-17
I am glad that you got it as it should be.

By the way HINTING is for LCD monitors to render text fonts properly.

---

### Post by Loki*PI on 2012-01-13
HI: I need to re-open this. I thought I had it resolved but the problem is back and worse. Often now some of the icons have 'blank' areas running across them, sort of like a lighting streak. Often email fonts are so broken as to be unreadable.

All of this comes and goes. Just now the header on this Chrome page reads something like: Ub''nt" For'ms. Other parts of the page are ok.  

I have switched monitors, cables - no change. Tried a variety of fonts and sizes. Tweaked all the various setting in 'Advanced Settings' - no joy.  

I've thought about trying to re-install the fonts but I doubt that is the problem, it seems unlikely that all the fonts are corrupt and if they were it would be a consistent problem.

Anyone have any ideas on this one?  

Thanks

---

### Post by Loki*PI on 2012-01-13
here are results from lshw -c video:


*-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dfe00000-dfe7ffff ioport:7000(size=8) memory:e0000000-efffffff memory:dfe80000-dfebffff

All this doesn't mean a lot to me but maybe someone understands it better.

Also found a thread that is discussing what seems to be the same problem:  "rendering of characters in Firefox (periodic problem)" and is unresolved also.

---

### Post by Loki*PI on 2012-01-14
Results of some testing on an email that was very hard to read
serif - very bad breaking up of text
san-serif - very bad also
variable width - bad
Arial - bad
Ume Gothic - bad

monospace - no problem
fixed width - no problem

Times New Roman - slight problem
Century School Book - slight problem
Courier New - minor problem
WenQuan Yi Micro Hei - minor problem
FreeMon - no problem

I hope some of you that know more about fonts and how they work than I do may see a pattern here. 

I've used advanced settings tool and changed all the fonts into mono. That doesn't solve the problem but I can now read things, although the appearance is a little strange.  There are still white streaks occasionally across some icons.

---

