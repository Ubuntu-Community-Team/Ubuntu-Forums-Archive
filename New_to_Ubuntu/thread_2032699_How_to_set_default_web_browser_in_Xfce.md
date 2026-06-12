---
title: "How to set default web browser in Xfce?"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by ub07 on 2012-07-24
The default web browser for Xubuntu was Firefox, but I wanted to change it to Chromium. Somewhere along the line, I put in the wrong name or path, and now I get a "Failed to Execute Default Web Browser" error everytime I click on web browser in the dock or "web browser" in the menu. I cannot find out how to change it (even back to Firefox would be better than nothing).

In the Settings Manager under "Preferred Applications" Chromium shows up as my default web browser so the problem is not there. The problem is that these shortcuts (on the dock and in the menu) point to something that is not correct.

---

### Post by Bufeu on 2012-07-24
Don't know if this will work in XFCE, but try this: [http://crunchbanglinux.org/forums/topic/16411/quick-and-dirty-change-default-browser/](http://crunchbanglinux.org/forums/topic/16411/quick-and-dirty-change-default-browser/).

---

### Post by december0123 on 2012-07-24
Hello, 
If I understand you correctly: you click on an icon and it fails to launch a browser. Just right click on it and change the path to for example: ```
 chromium-browser 
```
Hope that helps!

---

### Post by ub07 on 2012-07-24
> **december0123 said:**
> Hello, 
If I understand you correctly: you click on an icon and it fails to launch a browser. Just right click on it and change the path to for example: ```
 chromium-browser 
```
Hope that helps!

That worked for the icon on the dock, but not the first item "Web Browser" in the menu. I think that there is a variable somewhere that holds the default value. I think this because when I right-clicked on the dock icon, there was some code there that I replaced with chromium-browser.

---

### Post by december0123 on 2012-07-24
Ok then!

Right click on the menu, edit it, find the place to write down the command and type ```
 exo-open --launch WebBrowser %u 
```

---

### Post by ub07 on 2012-07-24
> **Bufeu said:**
> Don't know if this will work in XFCE, but try this: [http://crunchbanglinux.org/forums/topic/16411/quick-and-dirty-change-default-browser/](http://crunchbanglinux.org/forums/topic/16411/quick-and-dirty-change-default-browser/).

Actually, it wasn't the exact solution, but it pointed me to the right directory where I deleted the wrong shortcut and then it allowed me to reconfigure my default web browser. Thanks.

---

### Post by ub07 on 2012-07-24
> **december0123 said:**
> Ok then!

Right click on the menu, edit it, find the place to write down the command and type ```
 exo-open --launch WebBrowser %u 
```

Thanks, but I solved the problem. I really appreciate your responding. 

Thanks to the both of you.

---

