---
title: "Turning off geolocation in Fx 3.5"
date: 2009-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by NoBugs! on 2009-07-06
The Geolocation feature in Firefox 3.5 can be removed in 3 steps:

1) Open Firefox 3.5, type "about:config" in the location bar, and search for "geo.enabled". Double click to set this preference to "false".

2) In places menu -> search for files, search for a file named "NetworkGeolocationProvider.js" somewhere in the directory /usr/lib/

3) Once you've found the file, go to the terminal and run: "gksu nautilus". Press Ctrl+L and go to the directory the file is in. Now right click, rename file and change the file name (add "." or something at the start of the file name). This should disable this component.

---

### Post by jpeddicord on 2009-07-07
All you really need to do is the first step. The last two will really only break the functionality and probably other parts of the browser that depend on it.

Regardless, approved, and thank you for your tutorials & tips contribution.

---

### Post by NoBugs! on 2009-07-12
> **jacobmp92 said:**
> All you really need to do is the first step. 
Good point. The first step disables this feature, the other steps are to *remove* this component, for those who don't need or want it. I don't think it causes any major problems, since it is a javascript file that most important functions access with try...catch ( [https://bugzilla.mozilla.org/show_bug.cgi?id=487467](https://bugzilla.mozilla.org/show_bug.cgi?id=487467))
Also, I forgot to mention, you can rename/move the file back to NetworkGeolocationProvider.js and reset the preference to change it back.

---

