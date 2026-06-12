---
title: "[SOLVED] Sound in Zenwalk"
date: 2007-12-19
forum: Other OS Talk
---

### Post by Inxsible on 2007-12-19
I installed Zenwalk 4.8 last night in an old computer I found.

During the install, it ran the alsamixer sound configuration utility and found, correctly- I might add, the Yamaha sound card in the laptop.

I was thrilled when it found it because the card and the laptop is way too old. In anycase, the sound doesn't work.


How do I go about making it work?

Thanks for your time :)

---

### Post by tommcd on 2007-12-20
First run "lspci -v" to as root to make sure it is still being detected. Also check "lsmod | grep snd" to see if a driver is being loaded. 
Try running "alsaconf" again as root to see if it will setup the soundcard.  Then run "alsamixer" again and unmute everything and turn the volumes up. Also check /etc/group and make sure your user name is a member of the audio group.

---

### Post by Inxsible on 2007-12-20
> **tommcd said:**
> First run "lspci -v" to as root to make sure it is still being detected. Also check "lsmod | grep snd" to see if a driver is being loaded. 
Try running "alsaconf" again as root to see if it will setup the soundcard.  Then run "alsamixer" again and unmute everything and turn the volumes up. Also check /etc/group and make sure your user name is a member of the audio group.Thanks. I shall try it tonight and get back to you.

---

