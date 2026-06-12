---
title: "nvidia-settings won't let me 'save to X configuration file' - it crashes!"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by alecwh on 2008-11-03
Hello,

I'm having an issue with nvidia-settings. I need to set up my dual monitors by using "TwinView". I did this successfully in 8.04, but I'm having issues in 8.10.

When I open nvidia-settings, and set everything up, I hit 'Apply' and everything is perfect (my other screen starts working, everything is normal!). However, when I then click "Save to X Configuration File" (below 'Apply'), nvidia-settings crashes. As far as I know, there is no error returned... I ran it from the terminal by doing this: "gksu nvidia-settings".

Can someone help me fix this? I am desperately needing my other screen!

---

### Post by bodhi.zazen on 2008-11-03
It seems to be a bug (I have the same problem) with the new X and nvidia cards.

I suggest you go to launchad => bug report.

---

### Post by issih on 2008-11-03
Just a possible thought for a work around.. I'm pretty certain you can preview what nvidia-settings is going to try to write to the xorg file.

You could try copying that and pasting it into the xorg.conf manually (make a back up though for gods sake!).

I know this worked for getting 1920x1080 on a monitor that was being recalcitrant under intrepid, even though the new X isn't really meant to need an xorg file.

hope that helps

---

