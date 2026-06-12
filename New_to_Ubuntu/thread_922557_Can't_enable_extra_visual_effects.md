---
title: "Can't enable extra visual effects"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by amc6987 on 2008-09-17
Hey guys,

I am trying to hook up my desktop, trying to get the dock and widgets installed. I have been using this page to do it:[http://blogs.howtogeek.com/tuxgeek/2008/09/08/pimp-your-gnome-in-7-steps/](http://blogs.howtogeek.com/tuxgeek/2008/09/08/pimp-your-gnome-in-7-steps/)

It worked, but then I restarted my computer and everything was gone. I tried going through the steps once again, but I am not able to select the extra or even normal visual effects. All I get is a message saying that desktop effects cant be enabled.

I think it may be something with my ati or my nvidia. Im not sure which to use so I installed them all from the synaptic manager. But it seems like I cant use both; when installing the nvidia-glx driver, it automatically uninstalls whatever fglrx I have installed.

Please help! I feel like this may be very easy to fix, I just have no idea how.

---

### Post by Therion on 2008-09-17
First off, make sure you have the nVidia driver for your card both installed AND enabled.  

Open the Driver Manager (under System/Admin) and see what driver is enabled.  You may need to re-enable the Restricted so you're not using the default Vesa driver (which would prevent you from using the Advanced effects).


Ahhh... I see you're cross-posting in another thread.

---

