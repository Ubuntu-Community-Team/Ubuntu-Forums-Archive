---
title: "Ubuntu can no longer find my wireless network"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by MrPatton84 on 2008-08-08
I've just installed Ubuntu a few days ago, and managed to get my laptop connected to my wireless internet using madwifi. However, after installing some Ubuntu updates yesterday, my Wicd manager says that no networks can be found, and my connection properties displayed an error message saying "SIOCGIFFLAGS error: no such device."

The connection name here was "ath", and I've just changed it to "lo". The error message isn't there anymore, and it says that the connection is idle, but Wicd still can't find any networks. 

Any suggestions? If there's one thing I wan't to be able to do in Ubuntu it's connect to the Internet!

Many thanks in advance, 
Chris.

---

### Post by Austin_KW on 2008-08-08
lo is the loopback device (the PC itself); it was always there.

If the device (ath0?) has disappeared the there may be no driver for it. This may happen if an update gives you a new kernel. 

Redo the steps you did to get it working the first time.

---

### Post by MrPatton84 on 2008-08-08
Yeah, the ath has disappeared. You must be right about the update. 

So I should just redo the steps that I used to set up the wireless in the first place? Okie doke, I'll try that and we'll see if I get anywhere... :) thanks very much. 

Any advice for if this doesn't work? And how should I avoid it happening in the future when I download more updates?

Thanks,
Chris

---

