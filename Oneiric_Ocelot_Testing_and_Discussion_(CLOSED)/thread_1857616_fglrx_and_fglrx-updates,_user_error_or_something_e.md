---
title: "fglrx and fglrx-updates, user error or something else..."
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zuti on 2011-10-10
I couldn't come up with a better place for this, so here goes: 

I was under the impression, that if I want to receive fglrx updates after the 11.10 release, I should use the fglrx-updates packages. I'm having problems installing them with Jockey, but apt-get works. 

However I noticed that every time I try to install fglrx-updates, my video acceleration stops working. (vaapi/xvba and vlc or mplayer-vaapi). I also noticed that every time fglrx-updates is installed, xvba-va-driver is uninstalled as it apparently depends on the regular fglrx package... Am I doing something wrong, or is there a problem here? I've tried to search launchpad, but am not sure if this is known or if it even belongs there (and currently can't even get any results from lauchpad's search). 

Ideas, comments, anything?

---

### Post by zuti on 2011-10-12
Nevermind. I see someone has reported this: [https://bugs.launchpad.net/ubuntu/+source/xvba-video/+bug/871615](https://bugs.launchpad.net/ubuntu/+source/xvba-video/+bug/871615)

---

