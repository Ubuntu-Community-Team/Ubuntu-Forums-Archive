---
title: "GUI Frontend for rtorrent?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by aimpau on 2008-09-27
Hi all,

I've been using rtorrent a lot and I want to have a GUI frontend for it. How do I create one? I know basic C and C++ and that's it.

If you're going to make one, how would **you** do it so that it would be:

Fast
Super Less memory consumption (mine current: rxvt-unicode: 2MB, rtorrent:3MB)
Looks like transmission (simple)
Doesn't run on java (ntorrent)
Preferably integrates best with Xubuntu.

Back in XP, I was using TurboC++ and some Visual Basic. What is the best IDE for linux that can satisfy the above requirements?

Lastly, anyone want to unite with others to start this great project?:)

---

### Post by cariboo on 2008-09-27
Have a look at QT4 Designer for KDS or Gambas For Gnome.

Jim

---

### Post by mali2297 on 2008-09-27
I guess you would build the client upon Rakshasa's LibTorrent library?

If you want it to fit well with Xfce, I suggest using GTK+ for the frontend. 

Perhaps it would help to take a look at the source code of (say) Transmission's GUI, and the simple LibTorrent client here:
[http://libtorrent.rakshasa.no/wiki/LibTorrentSimpleClient](http://libtorrent.rakshasa.no/wiki/LibTorrentSimpleClient)

---

