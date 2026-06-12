---
title: "[SOLVED] Installing Opera"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by mczonie on 2008-09-15
I just installed Opera, and the computer says it's installed, but when I go to Applications > Internet, it's not there. Any idea what's going on here? 

TIA.

---

### Post by howefield on 2008-09-15
You might need to reboot before the icon shows.

---

### Post by shoot2kill on 2008-09-15
have you tried running opera from the terminal to see if it is all installed correctly.. and did you install it through the terminal, or synaptic ??

---

### Post by whizbaby on 2008-09-15
Open a terminal (applications>accesories>terminal)
and try:
```
opera
```
does it show up now? If so you only need to add it to the menu manually.

---

### Post by mczonie on 2008-09-15
> **howefield said:**
> You might need to reboot before the icon shows.

Just tried that. It's still not there.

---

### Post by mczonie on 2008-09-15
> **shoot2kill said:**
> have you tried running opera from the terminal to see if it is all installed correctly.. and did you install it through the terminal, or synaptic ??

No, I went to opera.com and installed it from there. I didn't even know you could install it from synaptic, but I just went there and it says it's installed.

---

### Post by shoot2kill on 2008-09-15
you could make a new shortcut in the applications menu, with a command of
```

opera

```

or if you dont want to mess about, use synaptic and mark opera for re-instalation...

---

### Post by Whiffle on 2008-09-15
Try doing

sudo updatedb 

and then when that finishes,

locate opera

chances are its in /opt/opera or something.

---

### Post by mczonie on 2008-09-15
> **whizbaby said:**
> Open a terminal (applications>accesories>terminal)
and try:
```
opera
```
does it show up now? 

Yes, but it also told me this:

```
OR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported

```

Any idea what this means?

---

### Post by whizbaby on 2008-09-15
If opera is running - it doesnt mean much.
libjvm.so has something to do with java, so maybe install sun java and firefox java plugin?
You can do this by
```
sudo apt-get install ubuntu-restricted-extras
```
after enabling universe/multiverse in your repositories.

---

### Post by mczonie on 2008-09-15
> **whizbaby said:**
> If opera is running - it doesnt mean much.


So it doesn't mean that there's anything wrong with my computer? I got Opera running and as long as there's nothing wrong with my computer, that's all I care about.

---

### Post by whizbaby on 2008-09-15
Noh you can safely ignore those warnings. If java doesnt work install what I said above (the repos can be activated in synaptic and the package installed by synaptic, too).
If you make an icon, you won't even see the error messages :)

---

