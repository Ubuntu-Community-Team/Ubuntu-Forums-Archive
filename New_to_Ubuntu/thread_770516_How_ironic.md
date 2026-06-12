---
title: "How ironic"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by tjefferson on 2008-04-27
This almost qualifies as a testimonial, but I'm still asking for help. 
My hobby is tweaking Ubuntu. I like installing a new OS every 6 months or so and making it work on my computer, usually with a lot of help from this forum or other resources online. This time, it only took me two days to have everything functioning correctly, while Gutsy took me two weeks. It's also fun to note to myself all the changes that occur between releases. It's fun watching Ubuntu grow up.
Yesterday the only problem I had left was the sound. Suddenly, by reinstalling pulseaudio and switching to that option in sound preferences, I could play sound, much to my pleasure.
I rebooted today, though, and I couldn't help but laugh. I have no GUI anymore. I loaded and it takes me to TTY1. I tried to select TTY7 with cntrl+alt+F7, but it's unavailable. Encouragingly, the system beeps when that happens, so I still have sound.
Before I log on I have this message:

Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/ae5c3c6f-58a7-45f7-925d-84361e4feb5e) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/ae5c3c6f-58a7-45f7-925d-84361e4feb5e
kinit: no resume image, doing normal boot...

It then asks for my user name and password. I've tried sudo apt-get update, and I tried reinstalling GDM and ubuntu-desktop. A solution I had tried earlier from a post called Comprehensive Sound Problem Solution Guide v0.5e had warned this might happen, but gave a solution. It didn't work for me. Otherwise I'm stuck. Any suggestions?

---

### Post by sdennie on 2008-04-27
Looking in /var/log/Xorg.0.log might be a good place to start.  I would see if it has any errors towards the bottom.  Also looking in /var/log/gdm/:0.log might help you find the problem.

---

### Post by tjefferson on 2008-04-27
Thanks much but I just solved it by reinstalling GDM and ubuntu-desktop. It didn't work last time, though. This issue is solved.

---

