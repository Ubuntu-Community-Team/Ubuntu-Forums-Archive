---
title: "Wine is trying to execute shell scripts."
date: 2008-11-18
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-18
Hi, all:

Since I installed Wine, I haven't been able to execute bash scripts.  Wine is being used as the default for executables, whether it's .exe or .sh.

How do I fix this?  The context menu for setting default applications doesn't show bash as an option for executing shell scripts.

---

### Post by nhasian on 2008-11-18
the first line of your bash scripts are

```
#!/bin/bash
```

right?

---

### Post by tarahmarie on 2008-11-18
Yep.

---

### Post by snkiz on 2008-11-18
I have the same problem. What I did was change the the program to open them to a text editor. Since I always run my scripts in the terminal, its enough to get me by.

---

### Post by tarahmarie on 2008-11-18
Wow.  That sucks.  I could change them to all execute in a text editor, but I have a LOT of scripts that run in the background, stuff like plasmoids with updating script commands.  What would happen if I did that?

---

### Post by Kellemora on 2008-11-18
Hi Tarah

Wine is configured to run /bin/bash or .sh files by default.

I think you can go into winecfg and tell it not to do that!

TTUL
Gary

---

### Post by tarahmarie on 2008-11-18
I looked at /usr/bin/winecfg and I can't find anything in that script which tells it to execute shell scripts; only windows executables.  

What would I change, and where would i change it?

---

### Post by snkiz on 2008-11-18
> **tarahmarie said:**
> Wow.  That sucks.  I could change them to all execute in a text editor, but I have a LOT of scripts that run in the background, stuff like plasmoids with updating script commands.  What would happen if I did that? If you right click into the properties menu then go to the open with tab what you srt there will be system wide for your user.

---

