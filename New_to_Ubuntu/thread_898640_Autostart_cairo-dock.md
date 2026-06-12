---
title: "Autostart cairo-dock?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Tomlin on 2008-08-23
I'm trying to get cairo-dock to auto start. I've set up sessions to run cairo-dock.

[IMG]http://i287.photobucket.com/albums/ll128/wftomlin/Screenshot-3.png?t=1219516824[/IMG].

When the computer starts up, the dock doesn't appear on screen but a look at System > Preferences > Sessions > Current Session shows it's running.

[IMG]http://i287.photobucket.com/albums/ll128/wftomlin/Screenshot-SessionsPreferences.png?t=1219516903[/IMG].

If I manually go to Applications > System Tools > Cairo-Dock OR type Alt+F2 and enter cairo-dock, the dock pops up.

[IMG]http://i287.photobucket.com/albums/ll128/wftomlin/Screenshot-4.png?t=1219516958[/IMG]

What am I doing wrong?

Thanks.

Tomlin

---

### Post by ggaaron on 2008-08-23
Does cairo-dock need composite WM (like compiz) to work? If yes then you should try to force it wait a few seconds before starting. Theoretically 'sleep 5 && cairo-dock' should work, in practice I remember that for similar things I had to write a bash script and execute it.

---

### Post by Tomlin on 2008-08-23
Thanks ggaaron, that worked. 5 wasn't long long enough, but 15 works.

Tomlin

---

