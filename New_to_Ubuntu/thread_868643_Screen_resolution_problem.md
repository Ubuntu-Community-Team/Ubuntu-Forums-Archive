---
title: "Screen resolution problem"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by gordohumphrey on 2008-07-24
I just installed ubuntu today and somehow, I don't even know how, I got my wireless usb adapter to work. So anyway, the problem is the only options it gives me for screen resolution are no good. I am stuck with 800x600. What do I do? Keep in mind that I've been using windows my entire life and I don't even know how to use linux well.

---

### Post by overdrank on 2008-07-24
> **gordohumphrey said:**
> I just installed ubuntu today and somehow, I don't even know how, I got my wireless usb adapter to work. So anyway, the problem is the only options it gives me for screen resolution are no good. I am stuck with 800x600. What do I do? Keep in mind that I've been using windows my entire life and I don't even know how to use linux well.

Hi and welcome, You can use the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware look for VGA. Then you may search the forum for additional help or post back here.

---

### Post by marshall.robert on 2008-07-24
im not great but this is what i have picked up on my linux adventure:
it could possibly be a driver issue, so you can check to see if you need it with the restricted drivers manager (System -> Administration -> Hardware Drivers) or you could try the new Screens and Graphics Preferences program by pressing ALT+F2 and typing in "gksu displayconfig-gtk" and have a stab at that.

---

### Post by markbuntu on 2008-07-24
Open a terminal and copy and paste this command. It will reconfigure your x server which controls the screen and other stuff.


sudo dpkg-reconfigure -phigh xserver-xorg

If you have been blindly messing around there is a good chance you messed up the x configuration. Or if you incidently installed a new video driver, etc. This command allows you to fix all that. Save it somewhere, you may need it in the future.

---

