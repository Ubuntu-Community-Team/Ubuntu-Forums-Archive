---
title: "HOW TO: Add another Keyboard layout in XFCE."
date: 2005-09-16
forum: Outdated Tutorials &amp; Tips
---

### Post by kagashe on 2005-09-16
Hi,

The answer is there on XFCE Wiki:>  How do I configure Xkb

Add the XkbLayout Option to your xorg.conf-file. Here is an example if you want to use german and russian keyboard-settings:

   Section "InputDevice"
   Identifier  "Keyboard0"
   Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "de,ru"
   EndSectionYour default layout will be there in the Option   "XkbLayot" line e.g. if the default is English (US) keyboard it will be displayed as>        Option      "XkbLayout" "us"You have to add a comma "," and type the symbol of the other keyboard. (de for german and ru for russian in the example).
You may have to restart X (or there may be some other way to make the saved /etc/X11/xorg.conf file effective).

You have to install xfce4-xkb-plugin (through apt or synaptic) and add xkb layout switcher to the panel.

kagashe

---

### Post by Espina on 2008-09-15
I did get to the xorg.conf file, but I couldn't edit it.

Could you please help me?  I want to switch between english and spanish keyboard layout.

Thanks!

---

### Post by lorenbr on 2008-09-19
You can edit the xorg.conf file by opening up the terminal and typing in the following command:

gksu gedit /etc/X11/xorg.conf

Alternatively, you should be able to enable the two keyboard layouts by going to System > Preferences > Keyboard, clicking over the the Layout tab, and using the "Add" button.

I hope that helps...

---

### Post by Espina on 2008-09-19
Thank you very much, it actually did help me.

Just a few comments:  

1-The 8.04 Xubuntu distribution (with Xcfe environment) doesn't come with gedit, it comes with mousepad, so you have to make that little change in the name on the command line.

2-I haven't found a way of installing it as you latter suggested, but with that simple instructions you gave me and later adding the language bar on the upper task bar I was able to change between keyboard layouts with no problem.

Thank you very much again!

---

### Post by foxy123 on 2008-09-26
> **Espina said:**
> Thank you very much, it actually did help me.

Just a few comments:  

1-The 8.04 Xubuntu distribution (with Xcfe environment) doesn't come with gedit, it comes with mousepad, so you have to make that little change in the name on the command line.

2-I haven't found a way of installing it as you latter suggested, but with that simple instructions you gave me and later adding the language bar on the upper task bar I was able to change between keyboard layouts with no problem.

Thank you very much again!

There is an easier way to do it. Go to Settings/Settings Manager/Keyboard. Click on Layout ta b and add a layout you need.

---

### Post by Weaseal on 2008-09-30
This solution didn't work for me.  I added the xfce4 xkb app, but when it shows that it has switched languages, everything still inputs in English.

Here is what I added to xorg.conf:```
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option "XkbLayout" "us,ro"
EndSection
```Have I missed something?

---

### Post by foxy123 on 2008-10-04
> **Weaseal said:**
> This solution didn't work for me.  I added the xfce4 xkb app, but when it shows that it has switched languages, everything still inputs in English.

Here is what I added to xorg.conf:```
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option "XkbLayout" "us,ro"
EndSection
```Have I missed something?

Did you try keyboard options in the settings manager?

---

### Post by crgutierrez on 2008-11-14
yes, i did try the settings manager many times, but did not work until I edited the xorg file.................something is not yet ready in xubuntu for an easy switch

---

### Post by shaulreznik on 2008-12-05
Modify your /etc/default/console-setup as described below
[https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/259489](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/259489)

---

