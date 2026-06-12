---
title: "Gvim - Close all windows"
date: 2010-07-08
forum: Programming Talk
---

### Post by adit on 2010-07-08
I have 4 or 5 windows of gvim open.  I want to close all windows at a time.  What command should I issue?

---

### Post by hanniph on 2010-07-08
> **adit said:**
> I have 4 or 5 windows of gvim open.  I want to close all windows at a time.  What command should I issue?

```
:qall
```
or 

```
:wqall
```

---

### Post by adit on 2010-07-08
```
:qall
```
The above code does not work.  It closes only the current window.  I mean separate windows _not tabs_.

---

### Post by Simian Man on 2010-07-08
There is no built-in way because all of the instances are totally independent.  You could always:
```

killall -9 gvim

```

---

### Post by hanniph on 2010-07-08
> **Simian Man said:**
> There is no built-in way because all of the instances are totally independent.  You could always:
```

killall -9 gvim

```

I guess there will probably be bunch of annoying .swp files left after that.

---

### Post by adit on 2010-07-08
```
killall -9 gvim
```Thanks.  It worked.

---

### Post by Simian Man on 2010-07-08
> **hanniph said:**
> I guess there will probably be bunch of annoying .swp files left after that.

Yes, you could disable them with "set noswapfile", but I would just close the windows all manually.

---

### Post by gmargo on 2010-07-09
Never use signal -9 (SIGKILL) if you can avoid it, since the targeted processes cannot catch the signal and clean up after themselves.  **gvim** (and most processes) will respond very nicely to signal -15 (SIGTERM), which is the default signal for **killall**.  In general, if the default (-15) does not work, try -3 (SIGQUIT), -2 (SIGINT, same as ^C), -1 (SIGHUP), then as a last resort -9 (SIGKILL).

The reason you needed to use **killall** instead of a ":quit" command is that you had several separate **gvim** processes running, each with it's own window.

---

