---
title: "Howto: Solve the Thunar opening twice problem in Xubuntu"
date: 2006-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by picpak on 2006-07-21
From my [blog](http://xubuntu.wordpress.com/2006/07/11/how-to-solve-the-thunar-opening-twice-problem/):

If Thunar is left running in the background when you log out, and starts up in the background when you log in again, you may have a problem with Thunar opening twice. Here&#8217;s how to fix it:

1) Go to Xfce Menu > System > Xfce 4 Task Manager.

2) Scroll through until you see Thunar. Right click it, and click Kill. If it asks if you want to actually kill the process, say yes.

3) Exit all of your programs, and go to Xfce Menu > Quit. Check &#8220;Save session for future logins&#8221;, and log out.

4) Log in, start Thunar, and hopefully it will only load once. This works for xfrun4 too!

* Note: To make sure Thunar doesn&#8217;t load up in the background next time you log in, uncheck &#8220;Save session for future logins&#8221;.

---

