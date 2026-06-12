---
title: "Audio doesn't work under Hardy"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by akmet on 2008-04-30
Hello,

I've been scouring the web for a solution and haven't found one yet that works, hoping you guys can help me out.  

The master volume control in Gnome gives me the following errors when I try to bring it up / unmute it.

"No volume control GStreamer plugins and/or devices found"

lspci |grep audio; shows the following;
02:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

lsmod |grep snd; shows nothing

aplay -l; shows
aplay: device_list:205: no soundcards found...

I've done the full uninstall of alsa with --purge switch, and reinstall with no results.

Running following kernel (per uname -a)
Linux usagi 2.6.24-16-386 #1 Thu Apr 10 12:50:06 UTC 2008 i686 GNU/Linux

Side note, the system actually has two sound cards, one on the motherboard and a PCI (Turtule Beach Riviera), the motherboard card (can't remember brand/manufacturer) is disabled in the bios.

I'm still "newbish", and thank you for your time and patience, your help is appreciated!

---

