---
title: "Ubuntu Unity/Classic booting into 1080i resolution"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by crono141 on 2013-02-17
I'm having a weird problem with my startup resolution.  I have an nVidia 460gtx commecting via hdmi to my sony bravia tv.  Everything works, except that when I log into the Ubuntu desktop window environment (either Unity or Ubuntu classic), I cannot see the top or side bars due to overscan.  I discovered that for some reason it is defaulting to 1080i resolution.  When it boots overscanned, I go into the nVidia x settings and set it to 1920x1080x60hz, and the overscan issue disappears.  All well and good until I reboot.  It will then default back to 1080i and boot with an overscan issue.

I've tried writing the new correct configuration to xorg.conf, but this does not fix the initial boot issue.  Does anyone have any ideas?

---

### Post by crono141 on 2013-02-28
No one has any ideas, eh?

EDIT:  Well, after a quick "I don't know what I"m doing but what the heck" moment, I sudo gedit the xorg.conf file and removed the metamode "1920x108_60i 0+0" and that fixed my problem.

Just wish you didn't have to edit a config file manually for it to decide to use the last video mode you told it to use.

---

