---
title: "120hz refresh rate help"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by fenderjaguar on 2013-05-08
I have a 120hz monitor. I can easily set it to 120hz by going Nvidia X Server Settings > X Server Display Confuration. 

However, whenever I restart, it switches back to 60hz. It's a minor issue, but does anyone know how to lock it? Thanks..

---

### Post by eriktilton on 2013-07-19
):P Why does Ubuntu hate blazing-fast refresh rate monitors? I've come to Ubuntu from Windows XP[INDENT] 
I remembered how great it was in XP when I ran the monitor at **800x600@160Hz,** blazing through Call  of Duty 4 and other games so well that I was kicked from almost every  server because I could hit people before they could see me coming around  the corner.

So I install Ubuntu and start tweaking. I go online and learn about 

**Xrandr**

OK so I try it and Xrandr **doesn't work** to get me 800x600@160Hz, for some reason. *60-85Hz* is the max. Let me try

**Xorg**

I put in some monitor-related stuff and screw up my computer.
Time to reinstall Ubuntu! Ohh well.

**Let me try Nvidia X Server Settings**

Huh! The highest refresh rate it'll let me do is 100Hz @ 1152x864.  Everything else is between 60-85Hz. Hmm OK I guess, I can live with **1152x864@100Hz**.

But I really really really *like* **800x600@160Hz**!

And *1152x864@100Hz doesn't stick*, when I restart the computer it goes to 75Hz :sad:.

So let me see if I can get Ubuntu to fetch my monitor EDID with **edid-decode**.

Is "fetch" even the right word? I don't know.

Edid-decode doesn't work. Let me try **get-edid**.

[I]"The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID"[/I]

adghopdsjfg
sd

What I would eventually like to do (like you) is be able to use **800x600@160Hz**  in Ubuntu. I would like this setting to "stick" so that when I restart the computer it'll default to that speed.

I hope things get fixed for us
[/INDENT]

---

### Post by dannyboy79 on 2013-07-19
are you launching nvidia-settings with gksudo so that you can save the 120hz setting?

---

