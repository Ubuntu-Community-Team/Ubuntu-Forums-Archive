---
title: "Installed rTorrent from source previously; overwrite with a package?"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by c3ntury on 2012-09-16
I installed rTorrent manually (through compiling and such), but now I need to upgrade it.

I had a look at whether my system recognised rTorrent being 'installed', and it said it wasn't, so if I did 'sudo apt-get install rtorrent' it'd install an entirely new package. I didn't proceed as it didn't recognise the old version.

How could I go about upgrading without losing my rTorrent session (torrents and so forth), and without screwing everything up?

Best regards,
c3ntury.

My current version - rTorrent 0.8.9

---

### Post by oldos2er on 2012-09-16
If you're using 12.04, rtorrent v0.8.9-2 is in the repositories. If you want to compile a newer version, I would remove the old one first by going into the source folder (you kept it, right?), run **sudo make uninstall**, then compile and install the newer one like before.

---

