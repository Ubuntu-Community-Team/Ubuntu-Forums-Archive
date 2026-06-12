---
title: "Self-compiled Pidgin &quot;forgets&quot; about installed protocals"
date: 2008-09-19
forum: Packaging and Compiling Programs
---

### Post by SamuelC on 2008-09-19
Hi all,

With the advent of Pidgin 2.5.0 (and now 2.5.1), I started compiling Pidgin myself.

When I first did it, I didn't know better and just ran configure/make/make install as-was. I removed the pidgin package first, but I didn't remove libpurple0 until after the freshly-compiled Pidgin failed to run, and I didn't remove pidgin-data until way later.

Here is where my issues start. About every time I started Pidgin, it wouldn't recognize any of the protocols (the Accounts menu would have them, but each account would be followed by "(unknown)"), there were no protocols listed on the dropdown menu when editing an account, and attempting to add a new account resulted in a segfault (as revealed by watching **pidgin -d**).

A bit of Googling later revealed that I could try uninstalling my custom-compiled Pidgin, removing (and **--purge** with dpkg) pidgin, libpurple0 and pidgin-data, and running **configure** with the **--prefix=/usr** argument to install Pidgin into **/usr/bin** instead of **/usr/local/bin**. I did all that followed by **make uninstall**, **make clean**, **configure**, **make** and **make install**.

It seemed to work. Until the second next time I restarted Pidgin. Then, it was back to the same old, same old. I discovered, however, that I could get it to work if I uninstalled, reconfigured (without the **--prefix** argument), let it install to **/usr/local/bin**, uninstalled that, reconfigured for the right path, then installed.

It's down to something of a habit now: run Pidgin, find it's broken, and do ```
sudo bash -c "make uninstall && ./configure && make install && make uninstall && ./configure --prefix=/usr && make install"
``` (so I can just walk away and come back 15 minutes later to find it working).

System: 2.8GHz P4 with 1GB RAM (rebuilding isn't a completely trivial procedure), Ubuntu 8.04 with all updates done.

Can anyone give me any advice or suggestions? This is really, really annoying, and it's happening pretty much every time I run Pidgin.

   --- SamuelC

P.S. Sorry if this is the wrong place for this topic - this looked like the best place to me.

---

### Post by InfinityCircuit on 2008-09-19
Why are you compiling from source?  2.5.0 is in hardy-backports and 2.5.1 is in intrepid.

---

### Post by SamuelC on 2008-09-19
Because I didn't know there were backports from beta releases of Ubuntu. Whoops! I'll give that a shot.

I think I might've messed something up, though, because the GetDeb package didn't work either (and required the same procedure to remedy, substituting **dpkg --purge pidgin pidgin-data libpidgin0** for **make uninstall**).

   --- SamuelC

---

