---
title: "[SOLVED] Rebuild-Restore Desktop (to &amp;quot;out of box&amp;quot; state)"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by ExWindowsDude on 2008-09-03
I'm trying to restore/rebuild my desktop to it's original state.

I was previously given instructions to run

```
gnome-panel
```

It "works" (it rebuilds the desktop), however once I close my term window it rolls back to the "bad" (unwanted) state.

The error message I see (before closing the term window) is:

```

bender@bender-desktop:~$ gnome-panel

(gnome-panel:18441): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


```

Any suggestions?
Thanks

---

### Post by NESFreak on 2008-09-03
the warning is nothing to worry about.
try executing ```
nohup gnome-panel
``` instead

---

### Post by billgoldberg on 2008-09-03
> **ExWindowsDude said:**
> I'm trying to restore/rebuild my desktop to it's original state.

I was previously given instructions to run

```
gnome-panel
```

It "works" (it rebuilds the desktop), however once I close my term window it rolls back to the "bad" (unwanted) state.

The error message I see (before closing the term window) is:

```

bender@bender-desktop:~$ gnome-panel

(gnome-panel:18441): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


```

Any suggestions?
Thanks

Does it work when you enter it in the "alt+f2" popup?

Or when adding a "&" after the command in the terminal?

That error is nothing to worry about.

---

### Post by ExWindowsDude on 2008-09-04
> **NESFreak said:**
> the warning is nothing to worry about.
try executing ```
nohup gnome-panel
``` instead

That FIXED it, THANKS!

---

