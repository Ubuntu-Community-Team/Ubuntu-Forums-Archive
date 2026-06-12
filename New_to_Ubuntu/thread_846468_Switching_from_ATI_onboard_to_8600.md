---
title: "Switching from ATI onboard to 8600"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by drewcoon on 2008-07-01
Hello!

I've got an NVidia 8600 GT coming in the mail soon, and I was wondering how to switch over from my ATI onboard? I've never switched from onboard to card before so I'm not sure what I'm doing.

What I'm planning on doing is:

-sticking card in empty PCIe slot
-hook up monitor

will i get a picture through it without driver? if not,

-login with onboard card, download and install NVidia driver
-reboot, disable onboard card in BIOS, then boot up to (hopefully) pretty NVidia graphics?

Will my plan work as expected? I need someone who knows a little better what they're doing to help out. Thanks :)

---

### Post by markbuntu on 2008-07-01
The first thing you should do after installing the new card is to get into the bios.

Be sure to check that the bios recognizes the nvidia card and you can enable it then disable the ATI onboard in the bios, then exit the bios and boot up as ususal. 

Ubuntu should recognize the new card and use the built in default vesa driver to get you through the log in screen and into your regular display manager.

Then get the nvidia driver.

If you boot up with the old card enabled, the os will try to use that and you could be into all sorts of problems.

---

### Post by LowSky on 2008-07-01
dont forget to uninstall the ATI proprietary driver before hooking up the Nvidia card.

---

### Post by drewcoon on 2008-07-01
Ok, so the new plan is,

-Uninstall ATI drivers
-pop in NVidia Card
-go into BIOS, disable onboard, make sure it recognizes new card
-hook up monitor to new card, boot up and pray for GUI
-install NVidia drivers

Better idea than my old one?

Thanks :)

---

### Post by markbuntu on 2008-07-01
Yes, that should work just fine. 

At some point in changing a video card you need to make a leap of faith.

---

