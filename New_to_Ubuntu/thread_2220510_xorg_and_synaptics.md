---
title: "xorg and synaptics"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by reddeadresolve2 on 2014-04-28
How does ubuntu/xubuntu handle xorg in Ubuntu 14.04?

I recently bought a Dell XPS13 9333 and I've been trying to configure the touchpad settings.

I have used these directions: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I have successfully generated an xorg and edited my values values but the changes do not stick, after reboot they revert back to the original settings. 

I could use some help in understanding how xorg and the associated /usr/share/X11/xorg.conf.d/ files work

---

### Post by jrussell88 on 2014-05-31
I have the same problem with 14.04.

I put a 60-synaptics.conf file in /usr/share/X11/xorg.conf.d but the settings are not applied on reboot. 

Can anyone suggest what the problem might be?

---

