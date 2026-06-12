---
title: "[SOLVED] No panels on desktop!"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-11-01
I never use evolution, so I removed evolution **completely** (and evolution-commons, evolution-data etc) using synaptic. Synaptic gave the warning that it was going to remove gnome-panel, fast-user-switch (or something like that) etc. I said ok and continued.

I also did an apt-get autoremove next.

After restart, my desktop doesn't have the panel and taskbar. How do I get it back?

I'm on Intrepid Ibex.

Thanks.

---

### Post by lisati on 2008-11-01
I had a similar thing happen today, but after tinkering with the desktop settings - I'd initially installed ubuntu with the Gnome desktop but decided to use the xubuntu desktop instead. It's possible that there's some dependencies that have been broken.

It is possible that someone else has a less drastic solution than the fresh install I ended up doing.

---

### Post by bumanie on 2008-11-01
If you can still get terminal up > sudo apt-get install ubuntu-desktopIt is possible to remove some of evolution, but there are a couple of files that are critical to the entire system. I think evolution-data-server, evolution-data-server-common need to remain intact. As you have done an autoremove, you may have to reinstall evolution from source before anything works properly again. Being a new installation, it may be easier to reinstall and if you uninstall evolution, leave the two files mentioned above.

---

### Post by Eto_Demerzel on 2008-11-01
For a start, I got back the panel by simply installing gnome-panel using get-apt. 

The problem seems to arise because evolution-data-common-server is required by the panel (To get rid of evolution, I had simply selected to completely remove anything that started with evolution- in Synaptic).

The panel getting removed was obvious. I wonder what else has been removed accidentally.

---

