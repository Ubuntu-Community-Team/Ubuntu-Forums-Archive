---
title: "FireFox doesn't remember homepage"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by think13 on 2008-07-02
Firefox 3 started out working perfectly for me on 8.04, but recently, it started forgetting all my preferences.  For example, it will always open to the default Ubuntu homepage, even after I change the homepage.

I noticed it start to happen when my NoScript whitelist got reloaded every time I restarted Firefox.  I uninstalled NoScript and the problem still happens.

This is probably not an Ubuntu problem, but I thought I could at least ask here.

---

### Post by think13 on 2008-07-02
Solved it myself.  The problem was that my firefox profile was corrupted.  To solve it, I ran ```
firefox -ProfileManager
``` deleted my old profile, and created a new one.  I did lose my bookmarks, but I think going into the old profile folder and copying the bookmarks file would have done that.  I'm just too lazy...

---

### Post by aysiu on 2008-07-02
You can import your old bookmarks from /home/*username*/.mozilla/*oldprofilename*/bookmarks.html

---

