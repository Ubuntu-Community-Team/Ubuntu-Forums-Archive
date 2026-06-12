---
title: "kernel updates strike again! nvidia problem"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by iansane on 2008-05-26
Hi,

I have become quite good at reinstalling my nvidia drivers everytime there's a kernel update.

A couple of versions back, developers decided to take away the ability to set up video with "dpkg-reconfigure xserver-xorg". I couldn't use the nvidia config tool cause it said "no driver" or something to that affect.

I would have to use dpkg-reconfigure xserver-xorg to make it appear in the config file. 

Anyway, I had to switch to the older version of xserver-xorg and lock it so it wouldn't auto update next time for kernel updates. So I'm wondering if anyone knows is it safe to unlock it yet? Did they decide to put video options back in?

BTW I'm running 8.04 server with ubuntu-desktop using nvidia6100 drivers.
Not that that makes any difference to the question.
Thanks

---

### Post by cybergalvez on 2008-05-26
> **iansane said:**
> Hi,

I have become quite good at reinstalling my nvidia drivers everytime there's a kernel update.

A couple of versions back, developers decided to take away the ability to set up video with "dpkg-reconfigure xserver-xorg". I couldn't use the nvidia config tool cause it said "no driver" or something to that affect.

I would have to use dpkg-reconfigure xserver-xorg to make it appear in the config file. 

Anyway, I had to switch to the older version of xserver-xorg and lock it so it wouldn't auto update next time for kernel updates. So I'm wondering if anyone knows is it safe to unlock it yet? Did they decide to put video options back in?

BTW I'm running 8.04 server with ubuntu-desktop using nvidia6100 drivers.
Not that that makes any difference to the question.
Thanks

I installed my nvidia drivers using envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) when the kernel gets updated so does the nvidia drivers.  This last update worked without a hitch
Jose

---

### Post by iansane on 2008-05-26
well it may have to do with running 64 bit server with desktop but I used envy once and still had to use dpkg-reconfigure xserver-xorg to make it show up in the config files as an available driver. I could be wrong but I think envy just downloads it and then installs it with scripts to save having to manually stop gdm and telinit 3 and click through all of those prompts.

Both ways I have the same problem.

---

