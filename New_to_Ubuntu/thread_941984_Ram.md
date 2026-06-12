---
title: "Ram"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by zamadatix on 2008-10-08
if i was to exit everything right now my ram wouldnt change much according to the monitor, but when i start up its in the 100's, what way can i empty my ram and swap without restarting and everything.

---

### Post by OutOfReach on 2008-10-08
You can try to log out and log back in. Try to kill some unnecessary process (but, be careful not to kill important system daemons, etc). Or you can try a lighter desktop enviroment or window manager (Openbox, Fluxbox, Xfce, etc..)

---

### Post by zamadatix on 2008-10-08
i was looking more of for a program like clear ram in which you type the value of the amount of ram you want cleared and it loaded the system up with 0's until the os cleared enough ram

---

### Post by pi.boy.travis on 2008-10-08
Many different Ubuntu programs use the same tools, such as the gecko rendering engine.

If you are short on RAM, I would recommend Xubuntu.

---

### Post by snowpine on 2008-10-08
Ubuntu uses your ram for cache to make your computer run faster. There is no reason to "clear out" your ram. If you open up a new application that needs that ram, it will dump the cache and free the space for the new application. It's a waste to have lots of ram and not use it! :)

If you want your system to use less ram on startup, OutOfReach's suggestion to use a lightweight windows manager is a good one.

---

### Post by familyguy.02 on 2011-02-23
This program might help you out. I've never tried it myself, but looks promising :) 

[http://manpages.ubuntu.com/manpages/lucid/man1/memdump.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/memdump.1.html)

---

### Post by NightwishFan on 2011-02-23
Trust me (and snowpine). There is no reason to want to dump your ram clean. That is something silly utilities are made for on WinXp that do not help any thing (and if they do, it is a flaw in the systems memory management to begin with).

Linux caches all unused ram for future use which improves performance. It will certainly pull something out of swap if it needs to. Generally even if you are starved for ram it will use the currently running task with a lot of speed.

---

### Post by philinux on 2011-02-23
Thread closed - necro.

[IMG]http://s4.postimage.org/55is5ax4e/Thread_Necromancer.jpg[/IMG]

---

