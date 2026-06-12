---
title: "Hardy not using entire screen"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Greevous on 2008-08-23
I just did a fresh install of Hardy on my Toshiba Satellite after using Gutsy successfully for several months. But now my screen space is limited to a small box in the center of the screen and my resolution is stuck at 800x600 when it should be 1024x768. 

I have seen this before on my laptop some time ago, but I forgot how I fixed it. I think I might have edited my xorg.conf file... Any help would be appreciated.

---

### Post by overdrank on 2008-08-23
> **Greevous said:**
> I just did a fresh install of Hardy on my Toshiba Satellite after using Gutsy successfully for several months. But now my screen space is limited to a small box in the center of the screen and my resolution is stuck at 800x600 when it should be 1024x768. 

I have seen this before on my laptop some time ago, but I forgot how I fixed it. I think I might have edited my xorg.conf file... Any help would be appreciated.

Hi and you may try and boot into recovery mode and use the xfix option. You can also try and use the command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
```and configure there.

---

### Post by Greevous on 2008-08-23
Thank you, overdrank. This fixed it. My first mistake was configuring it there and "testing" first, which never worked out.

---

