---
title: "having problems with xgl and nvidia x server"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by fignig on 2008-09-13
so i was running twinview off of the nvidia x server and everything was going fine, until i installed the animations for compiz and i had to enable the xgl. i am currently running off the xgl and it sucks unless i can configure it. i want 2 separate monitors but xgl makes it just 1 big one. i can't maximize anything within 1 monitor it stretches to both of them. is there anything i can do? is there anyway to run both xgl and nvidia x server so i can do the animations or can i enable animations w/ nvidia x server. someone help please.

---

### Post by ajmorris on 2008-09-16
> **fignig said:**
> so i was running twinview off of the nvidia x server and everything was going fine, until i installed the animations for compiz and i had to enable the xgl. i am currently running off the xgl and it sucks unless i can configure it. i want 2 separate monitors but xgl makes it just 1 big one. i can't maximize anything within 1 monitor it stretches to both of them. is there anything i can do? is there anyway to run both xgl and nvidia x server so i can do the animations or can i enable animations w/ nvidia x server. someone help please.
 
Hi there,
why are you wanting to run XGL? You dont need xgl to run compiz. All you need is the nvidia GLX driver (installed by sudo apt-get install nvidia-glx-new), the composite extensions option enabled in /etc/X11/xorg.conf and the Load glx module statement in /etc/X11/xorg.conf. (The xorg.conf entries should be added automagically upon the installation and enabling of the nvidia GLX driver.
 
AJ

---

