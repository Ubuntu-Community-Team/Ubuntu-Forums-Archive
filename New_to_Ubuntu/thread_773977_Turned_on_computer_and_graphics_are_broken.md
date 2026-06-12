---
title: "Turned on computer and graphics are broken"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jdlaw on 2008-04-29
I was wondering if anyone could help me with this:

I just installed ubuntu yesterday and everything was running just great, today when I restarted the computer all that came up on the screen once the loading bar of ubuntu disappeared was a load of what looked like black and white boxes covering the entire screen. At the moment I'm writing this message by using the liveCD which seems to work fine.

Any help on solving this would be greatly appreciated.

---

### Post by hermes0710 on 2008-04-29
> **jdlaw said:**
> I was wondering if anyone could help me with this:

I just installed ubuntu yesterday and everything was running just great, today when I restarted the computer all that came up on the screen once the loading bar of ubuntu disappeared was a load of what looked like black and white boxes covering the entire screen. At the moment I'm writing this message by using the liveCD which seems to work fine.

Any help on solving this would be greatly appreciated.


Can you post the contents of /etc/X11/xorg.conf and /var/log/Xorg.0.log?

---

### Post by jdlaw on 2008-04-29
Thanks for the quick reply, after fiddling about for a bit longer I found how to fix it myself - I booted into recovery mode and rebuilt my xorg.conf

It's once again working great.

---

### Post by aberry5555 on 2008-04-29
Ok, here's a quick fix that should work but bear in mind that any changes you made to your screen res, drivers etc will be cleared, this sets it back to the default settings (the same that are on the livecd).

When you see these black and white squares press ctr+alt+backspace (not the del key, the backspace key <- ). This should bring up a line of text asking you to log in, type in your user name and password and it will log you in and give you a command prompt. type in the following:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

It will ask you for a password and maybe a few questions, go through them and answer any relevent questions, if it asks any at all. If it comes to asking for the driver (I can't honestly remember if it does, it's been a while) choose "ati" for most ati cards, "nvidia" for an nvidia card or "vesa" for most anything else (vesa is a very basic driver and you'll need to change this to the appropriate driver later, but at least it will get you somewhere to start.)

after this type reboot, hold tight and, touch wood, after it's restarted you should have a desktop back.

<-- EDIT -->

Ah, I was too slow :p well done for getting it working!

---

