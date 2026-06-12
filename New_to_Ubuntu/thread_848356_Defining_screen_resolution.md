---
title: "Defining screen resolution"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Cowpoke on 2008-07-03
I have Xubuntu 8.04 installed and working; however, I cannot get it to work at high resolution.

I am using an ATI adapter and I have a Samsung 700p monitor.  It is supposed to get up to 1600x1200 resolution.  I have actually seen it do that...

I don't know how to set that as the default resolution, and it's not an available option in the display control.

Any tips are appreciated!

Thanks,
Cowpoke

---

### Post by ubuntu-freak on 2008-07-03
Try executing this command in the terminal:

**sudo xrandr -s 1600x1200**

If that doesn't work, execute this next command:

**sudo xrandr -q**

Set the highest resolution it will allow, then once that is set, try setting the actual resolution you want.

If all the above fails, execute this final command:

**gksudo displayconfig-gtk**

If your screen type is listed as "Default", try changing it to "Generic", then have a go at setting your preferred resolution within that application.

---

### Post by wolfen69 on 2008-07-03
another thing you can try is ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot

---

### Post by ubuntu-freak on 2008-07-03
> **wolfen69 said:**
> another thing you can try is ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot

 
Unfortunately that command won't let you configure graphics drivers or resolutions in 8.04+ versions of Ubuntu. The Xorg devs said it was risky, or something similar and just want bugs reported if autodetect doesn't work.

---

### Post by Cowpoke on 2008-09-11
> **wolfen69 said:**
> another thing you can try is ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot

Unfortunate for me...  I tried this, now my screen is compressed into a tight band that runs the center of my screen.  I can still connect from remote -- I tried to revert to an older xorg.conf, but that doesn't fix my squished screen problem.

Is there a -plow switch that I can use instead?  How would I set that?  dpkg-reconfigure doesn't run from remote.

Thanks!!!

Cowpoke

---

### Post by Cowpoke on 2008-09-13
Beware of the last step...  My monitor has been fried. :(

I am reverting to an older (1280x1024) monitor for the time being; I am expecting to bury my old monitor at 12:30 this coming Tuesday (16 September 2008 ).

It was a good monitor; serving me faithfully since 2000.  It tried very hard to display everything I asked it to -- sometimes it even went beyond spec's: just because I asked it to! :cry:  A more noble and loyal monitor I never knew.

The monitor flickered it's last legible image around 11:30pm 10 September 2008 - exact minute is not known.  (It displayed at a vivid resolution of 1600x1200.  I asked it to show me more at a brilliant 1792x1344 when she died.)  Flowers are welcome, monitor viewing will be possible Monday, 15 September between 1:00p and 4:00p EDT.

Replacement suggestions and donations are appreciated.


In memory of my monitor:

Day after day they pour forth speech; night after night they display knowledge with imagery: brilliant and true.
- Psalm 19:1-3

---

