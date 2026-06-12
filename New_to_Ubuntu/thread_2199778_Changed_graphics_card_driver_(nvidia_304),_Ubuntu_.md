---
title: "Changed graphics card driver (nvidia 304), Ubuntu won't boot"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by matthew.carnovale on 2014-01-15
Hey Gang,

I'm extremely new to Ubuntu and I noticed my windows were trailing a little bit, so I activated a what looked like a newer driver in the restricted driver update installer. It installed fine and prompted me for a reboot. I restarted and when I try to boot Ubuntu, it just brings me to a screen with a blinking cursor. I never make it to a login screen or anything that resembles a gui. I tried looking up other posts on this matter but when I enter recovery mode, my list of options doesn't match those suggested. When I try to log in as the root to type in the suggested commands (ex. nvidia&#8210;settings &#8210;&#8210;uninstall), it says that it's an invalid command line. How do I fix this? Or at least how do I get Ubuntu to boot again, so I can switch back to the original graphics driver that had been working for the last month?

Your help is greatly appreciated!

---

### Post by chkneater on 2014-01-16
If the only thing changed is your /etc/X11/xorg.config file you should be OK.  Look for it in your root directory, once you find it, open it up and open your back up xorg.conifig file (it will be like xorgconfig.backup or something).

Compare the two, if they're not the same, post them both.

BTW, I should have mentioned to use a LiveDVD or something to boot with... sorry!

---

