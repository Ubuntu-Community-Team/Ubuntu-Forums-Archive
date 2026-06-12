---
title: "OpenOffice Keyboard Layout"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by frayalejandro on 2008-05-27
Hi. I use a Spanish keyboard layout. But every time I login back to Ubuntu, it configures the keyboard automatically to the English layout. So I just erased the english keyboard and only left the spanish layout...and it still does the same thing!

Shortcut keys don't respond; Every session, I have to go to system>preferences>Keyboard>layouts>layout options... so that it recognizes my spanish keyboard.:confused:

Any help will be appreciated.:)

---

### Post by ZabiGG on 2008-05-27
Did you install the SCIM keyboard tool? I have a dual language setup (French-English) and it works perfectly.

Cheers,

Z.

---

### Post by frayalejandro on 2008-05-27
Yes, SCIM is already installed.

---

### Post by ZabiGG on 2008-05-28
Did you try configuring Spanish as default both in System > Preferences > Keyboard and in the SCIM tool properties?

---

### Post by frayalejandro on 2008-05-28
> **ZabiGG said:**
> Did you try configuring Spanish as default both in System > Preferences > Keyboard and in the SCIM tool properties?

Yes, and it doesn't work :(

---

### Post by ZabiGG on 2008-05-29
Did you try changing your xorg.conf file in /etc/X11 with gedit?

The 5th and 6th lines seen here (this section is around the middle of the file) should be changed to reflect your setup.

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbVariant"    "alt-intl"
    Option        "XkbOptions"    "lv3:ralt_switch"
    Option        "XkbOptions"    "compose:lwin"

Change us in this line
Option        "XkbLayout"    "us" 
to the keyboard code for Spanish

and this one
Option        "XkbVariant"    "alt-intl"
should be coded with your alternate language

To open the xorg.conf file, open the terminal and type

gksu gedit /etc/X11/xorg.conf

Hope this helps,

Z.

---

### Post by stanley82 on 2009-04-28
> **frayalejandro said:**
> Hi. I use a Spanish keyboard layout. But every time I login back to Ubuntu, it configures the keyboard automatically to the English layout. So I just erased the english keyboard and only left the spanish layout...and it still does the same thing!

Shortcut keys don't respond; Every session, I have to go to system>preferences>Keyboard>layouts>layout options... so that it recognizes my spanish keyboard.:confused:

Any help will be appreciated.:)

Yes, top of screen that's the line with apps, places, system etc and right click.  ADD TO PANEL select keyboard indicator.  I get USA or Can on my top line. I click it and it toggles usa can.  First make sure you have all the keyboards layouts selected that you use from system/preference/keyboard.  Good luck Ian.

---

