---
title: "geany debugger plugin"
date: 2016-03-22
forum: Programming Talk
---

### Post by r.stiltskin on 2016-03-22
Is the geany debugger (gdb) plugin broken, or am I?  I'm running Xubuntu 14.04 LTS, everything is up to date, geany 1.23.1+dfsg-1 and geany-plugin-debugger 1.23+dfsg-3, gdb 7.7.1-0ubuntu5-14.0, gcc 4:4.8.2-1ubuntu6.

No problem running gdb in terminal, but in Geany --  I have -g option in my build commands, I can specify a target file, I can set breakpoints, I can set a variable to watch.  That's about all.  I don't see a "load" button.  The only active button I see is "run" but if I click that Geany instantly crashes.  What am I missing?[ATTACH=CONFIG]267931[/ATTACH]

---

### Post by r.stiltskin on 2016-03-22
Apparently there is no separate "load" button - just selecting [open] in the "choose target file" dialog loads it.

It seems the debug plugin ver. 1.23 in the Ubuntu repository is broken.  I uninstalled geany and all plugins and installed the latest version (1.27) from the [geany-dev ppa]("https://launchpad.net/~geany-dev/+archive/ubuntu/ppa") and it works.

---

