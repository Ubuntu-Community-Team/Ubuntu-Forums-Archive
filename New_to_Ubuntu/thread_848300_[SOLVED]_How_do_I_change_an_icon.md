---
title: "[SOLVED] How do I change an icon?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-07-03
I wanted to get the newest version on eclipse, so I went and downloaded it from their website. There is apparently a "bug" in all of the linux versions for a while, where they don't have icons in it. I did some searching around and found an icon that I want to use, [here]("http://www.kde-look.org/content/show.php/eclipse+icon?content=71809"). But now when I use GNOME-Do and execute it, it just has a default icon. I have tried changing the icon path in /usr/share/app-install/desktop/eclipse.desktop, I right clicked on the application and changed the icon there as well. But no matter what I have done, the icon doesn't change in GNOME-Do. Any suggestions?

---

### Post by Bodsda on 2008-07-05
A psoibble solution is to find the icon and replace it. In a terminal type

```
<nameOfApp> | grep -i png
```

where <nameOfApp> is the name of the application, for instance, to find the xchat icon

```
locate xchat | grep -i png
```

after you have found the icons, just replace them with your own icon.

Hope this helps

Bodsda.

---

