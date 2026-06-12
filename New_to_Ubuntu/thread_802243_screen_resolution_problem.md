---
title: "screen resolution problem"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by kyalee on 2008-05-21
I've been having a problem with my screen resolution. I have it set to 1024x768, but at random, it will change to 1280x1024 and I can't change it back. If I log out and log back in, it will usually right itself and it's not a huge deal, but it's getting annoying.

Any ideas? I'm currently running Gusty, and I don't remember having this problem before I upgraded from Feisty.

---

### Post by Lowcountry on 2008-05-21
I'd suggest not upgrading from a previous version, but do a clean install...Sometimes things get buggy when upgrading.

---

### Post by kyalee on 2008-05-21
Yeah, I'll probably do a clean install when I upgrade to Hardy.

---

### Post by sailor2001 on 2008-05-21
you're ok.....I've always upgraded....go to /usr/share/applications/screen & graphics
I take it you do have your restricted drivers enabled.

---

### Post by pdtpatrick on 2008-05-21
check your configuration file in /etc for your monitor and make sure all your settings didnt get corrupted when you did your upgrade and at the same time, perform what the other fellow said. Im guessing you're using an ATI card?

---

### Post by bradbuntu on 2008-05-21
> **kyalee said:**
> I've been having a problem with my screen resolution. I have it set to 1024x768, but at random, it will change to 1280x1024 and I can't change it back. If I log out and log back in, it will usually right itself and it's not a huge deal, but it's getting annoying.

Any ideas? I'm currently running Gusty, and I don't remember having this problem before I upgraded from Feisty.

   Heres' the best way to fix any screen resolution problems: Open a terminal; applications, accessories, terminal and type:

   gksudo displayconfig-gtk

   Type in your password.

   You'll open a window that looks like this, see attachment. Choose plug and play then select your monitor by name and model number or choose generic and then your preferred display size. For me, the generic works the best so try both.

   You'll be asked to log out. Just click on system, quit and log out. Then log back in and see if your resolution is correct. 

   Important, I do not advise messing around with your xorg configuration and this can easily break your installation and you may have to reinstall all over again. 

   In Ubuntu 7.10 there was another tool in system administration to set up your resolution however, seems they left it out in 8.04 for whatever reason. 

   Hope this helps you as much as it did me. If so, please pass it on to others.

   Bradbuntu 

  :popcorn:

---

