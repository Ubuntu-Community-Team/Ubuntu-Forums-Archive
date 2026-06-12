---
title: "My KDE looks weird"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by CC_Joe on 2008-08-21
So, I'm having trouble figuring out themes with KDE. I really have no idea how to install new themes. I go to kde-looks.org and I download a .deb file, but installing that doesn't make it available in kde's theme manager. What am I doing wrong?

I attached a screenshot so I can show you what's wrong with my themes. Notice how thunar is all black on the inside? How do I change that? And see how firefox has white menus? I can't figure out how to change that too.

Argh, I'm having a hard time with kde.

---

### Post by ggaaron on 2008-08-21
Have you tried right click on desktop, desktop settings, and new theme - it should install themes from kde-look. On the other hand it will have nothing to do with Thunar and Firefox as they are not KDE and not Qt programs. Ubuntu doesn't provide the excellent KDE4-gtk package that let's you choose theme for GTK applications in KDE4 so I don't know if much can be done for GTK applications - there is qt-gtk package or something, but it is buggy=/

---

### Post by CC_Joe on 2008-08-21
Can I just install that KDE4-gtk package?

EDIT: Alright! Did some looking around other forums and "sudo apt-get install gtk-qt-engine-kde4" did the trick. I just had to check a box under system settings in KDE. GTK apps are integrated much better now.

Although I'm still not certain on how to properly install new themes in KDE. I'll keep looking around.

---

### Post by ggaaron on 2008-08-21
Unfortunately I think that you've just installed this:
[http://www.kde-look.org/content/show.php?content=9714](http://www.kde-look.org/content/show.php?content=9714)
and not this (not in Ubuntu repositories yet):
[http://www.kde-apps.org/content/show.php/gtk-kde4?content=74689](http://www.kde-apps.org/content/show.php/gtk-kde4?content=74689)

The second one is a lot better so keep an eye on this - gtk applications look beautiful=) As for KDE themes there are this steps(taken from kde-look.org):
    *  Install the Theme/Style by either extracting and compiling it, or installing an RPM.
    * Open the KDE-Menu and start the Control Center.
    * Select "Look and Feel".
    * Select "Style" if the package you installed was a style, or select "Theme Manager" if the package you installed was a theme.
    * Select your theme or style.
    * Click "Apply"
    * Have fun! :-) 

You've written that you've done them, so check if you have required KDE, Qt version to run your selected theme. Also if you've installed deb for right version of Ubuntu. If it doesn't work you can try posting on kde-look.org.

---

