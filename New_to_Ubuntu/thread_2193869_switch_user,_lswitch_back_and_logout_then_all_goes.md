---
title: "switch user, lswitch back and logout then all goes black"
date: 2013-12-15
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2013-12-15
I am not sure where to post this. Maybe a hardware issue, or maybe not, so please do the following experiment if you run Ubuntu 13.10

Boot up, switch user to guest, then switch back. Do it several times, so now you are back in your own account. Now try to logout. I got stuck in a black screen with some words which i have no idea what they mean except that nouveau is doing something.. At this point the computer is stuck in a limbo and has to be manually shut down (either press the power button or more elegantly get into tty and do a sudo poweroff)

Now if you have another user account, you can do this experiment. Boot up, log into your account, boot out log into the other account, then log back to your own account and switch to guest, again screen goes black..

If you don't have another user account, but have another DE installed, say LXDE, or gnome fallback. You can do the experiment by rebooting, log into Unity, then logout and log into the other DE, then switch to guest, black screen..

I have a Nvidia card, I tried these with both the proprietary driver and nouveau and the results are somewhat similar. Briefly, you can either switch to guest account or log out and log into a different de /usr but cannot do both in the same session,--by that I mean the time between reboots.

Can anyone confirm this behaviour and perhaps shed some light on it? Is Ubuntu's session management completely broken? Thanks.

---

### Post by monkeybrain20122 on 2013-12-16
Any idea?

---

