---
title: "[SOLVED] what extension for launcher icons useing gnome?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by iansane on 2008-06-01
Hi, I installed sunbird just for fun and made a launcher for it in my Applications menu. I found icons for it in the png format. When I try to change the icon through "edit menus" it won't let me use png. I read a tutorial on using gimp to save them as xpm but it won't take those either.

They don't even show up in browse unless they are .svg and gimp won't save as a svg. So how do I make an icon and use it for a launcher?

I'm running Ubuntu 8.04 using gnome.

Thanks

---

### Post by buntu_Geek on 2008-06-02
Inkscape has full support for svg images....

check its official website

[http://www.inkscape.org/](http://www.inkscape.org/)

To install....
```
 sudo apt-get install inkscape
```

---

### Post by iansane on 2008-06-02
Thanks buntu_geek I'll try it out.

---

### Post by iansane on 2008-06-02
OK well that wasn't the problem after all. I used Inkscape to save as an svg and it still wouldn't show anything when I used the browse option so I tried just typing in the full path and there were the .xpm and the .svg. Both of them work so I could have used gimp like the tutorial said.

Apparently there is a problem with "browse icons".

Anyway Inkscape looks like a real cool program and might be easier than using gimp since it seems to be specifically for icon making.

Thanks

---

### Post by HotShotDJ on 2008-06-02
> **iansane said:**
> Apparently there is a problem with "browse icons".No, the problem is user error. :)  I know this, because I initially drew the same conclusion as you did.  When you get to the directory from which you wish to select the icon, it is empty, and you say "drat!!  Where are the icons that I know are in there!!"  Well, the thing is, that particular window will only show directories... once you are in the directory that contains the icon you want, you must click on "Open".  The icon(s) will then appear in the icon browser.

---

