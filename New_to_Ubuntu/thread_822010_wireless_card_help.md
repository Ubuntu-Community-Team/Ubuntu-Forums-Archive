---
title: "wireless card help"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by moosejc on 2008-06-07
I am pretty new to linux, and I have installed Ubuntu 8.04 on my IBM Thinkpad T60. The OS works fine, however, my wireless card (which is an Intel PRO/Wireless 3945ABG) is not supported, and I cannot get it to work. I have downloaded iwlwifi, but keep getting the following error:

```
WARNING: $SHELL not set to bash.
If you experience build errors, try 'make SHELL=/bin/bash'.

Kernel Makefile not found at '/lib/modules/2.6.24-16-generic/source'
```

I get similar errors when i tried to install the mac80211 subsystem. I have searched other threads and tried everything i could find. I am completely lost and don't know what to do from here. Any ideas?

---

### Post by mikewhatever on 2008-06-07
Intel PRO/Wireless 3945ABG is supported out of the box (has been for some time) under Linux. It should work both on installed system and from the live cd. You should provide more info on the type of router, error messages you got etc. Also, post the output of the following <sudo lshw -C network>.

---

### Post by flint_ on 2008-06-09
I have a thinkpad, and was unable to get my card working until I called Levono tech support and found the "on-off" switch on the left hand side of the edge of the laptop.  If on you will see the color "green"  Is this the way yours is?

Regards,

Flint

---

### Post by ukripper on 2008-06-09
3945ABG is supported out of the box even in gutsy.

---

