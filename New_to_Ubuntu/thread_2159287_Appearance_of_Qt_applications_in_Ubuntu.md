---
title: "Appearance of Qt applications in Ubuntu"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by newb85 on 2013-07-02
I was wondering why my Qt-based applications looked so atrocious in Ubuntu.  They don't match the system at all.  I installed Qt Configuration from SC.  There's a GUI Style dropdown.  The default is Desktop Settings, which is presumably supposed to mimic the Desktop Environment in use.  Only, it doesn't.  Applying Desktop Settings doesn't change the GUI style, and Qt Configuration doesn't give any preview.

Am I missing something?  I'm running 13.04, with the default Unity.

---

### Post by ajgreeny on 2013-07-02
In Xubuntu 12.04 I had to install the KDE **system-settings** package in order to get my KDE/QT apps to look good.  Opening that you can use the Appearance tab to make the QT apps use a gtk widget set, and change various other settings as you wish.

The KDE apps I use still look a bit different from gtk apps, but they are not so strikingly different as they would be without those settings.

---

### Post by newb85 on 2013-07-02
Reviews seem to indicate that KDE System Settings doesn't play well with Unity.  I'm probably going to steer clear of that one.

---

### Post by vasa1 on 2013-07-02
> **newb85 said:**
> I was wondering why my Qt-based applications looked so atrocious in Ubuntu. ....
While on 12.10, I had installed ReText and whatever other recommends came along. I also installed Qtconfig, but ReText still looked "different". I haven't installed ReText on 13.04.

Can you mention a couple of Qt-based apps that look off for you?

---

### Post by BBQdave on 2013-07-02
Scribus appearance the same as other applications in Ubuntu Unity 12.04, though that is the only Qt-based application I have.

---

### Post by fantab on 2013-07-02
There is a package called 'qt configuration' where you have to change the theme setting to gtk. I am not sure if 'qtconfig' is installed by default in Ubuntu (I am not currently on Ubuntu machine), or to what qt package it belongs.

If your Ubuntu is using qt4 then in terminal run 'qtconfig-qt4', if not 'qtconfig' will do. This helped me in maintaining uniformity with qt based applications in Arch-gnome. 
You may find this useful: [URL="https://wiki.archlinux.org/index.php/Uniform_Look_for_QT_and_GTK_Applications"]https://wiki.archlinux.org/index.php/Uniform_Look_for_QT_and_GTK_Applications

[/URL]

---

### Post by vasa1 on 2013-07-02
@fantab, both OP and I installed qt-config. Anyway, I can't add more because I don't have ReText installed now.

---

### Post by fantab on 2013-07-02
> @fantab, both OP and I installed qt-config.
I missed that in the first post.

Especially in Ubuntu theming is quite uniform between Gtk and Qt by default. I haven't had any theming issues with qt-based applications in Ubuntu, and I do use quite a few qt applications.

What theme are you using for Gtk? Is it ambiance or have you changed it to something else? If you are using some other theme make sure it supports KDE and/or Gtk2 as well. I have noticed only the themes that support both gtk and kde work best. If the theme you are using does not have kde support then it could be difficult to get uniformity.

You must have Gtk2 theme engines as well for qtconfig to apply gtk themes. It is my understanding that gtk2 themes work best with qtconfig.

Also with qtconfig you may have to restart the application apply the new settings. If you are using any dark theme then enabling 'plastiq' in qtconfig also helps.
My skype in Arch has huge font settings if I use any other setting than plastiq. Gtk setting works fine with theme colors but not with fonts, esp, in Skype.

My two cents.

---

### Post by newb85 on 2013-07-02
Qt Octave is what got my attention.  But now i have a bigger problem.  Since messing with the settings in QTConfig, I've rebooted my system.  Now Qt Octave won't open at all.

Edit: changed the Qt GUI style to Cleanlooks, and now Qt Octave opens again.

---

### Post by newb85 on 2013-07-02
Here's what it looks like.

---

