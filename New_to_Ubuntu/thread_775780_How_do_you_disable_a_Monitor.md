---
title: "How do you disable a Monitor?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by keeler1 on 2008-04-30
I have a 19" lcd and a 27" LCD TV plugged into my desktop.  Whenever I boot into ubuntu it uses the 27" LCD TV as the main monitor with 680x400 resolution (My other monitor that I would want to be the primary monitor is blank).  The resolution is way to low and I can not change anything.  I have to unplug the second monitor inorder to do anything.

I would like to use the nvidia twinview thing, but the nvidia xserver settings application is not working apparently.

I need a 1360x768 resolution for the tv and 1440x900 for my monitor.  I tried changing this in the nvidia setting app but it did not work.  I also would need the monitor to be screen0 and the tv screen1.

Is there a way to do this with the nvidia app? or do I need to change my xorg.conf and if so how do I keep the system from changing itself back again.

Most importantly however, how can I disable the tv?  I need to not have it be screen0 on bootup?  It is not in my xorg.conf at the moment and the nvidia settings application doesnt even know it exists but as soon as I reboot screen0 is the tv.  So obviously things are being changed without my permission.

---

