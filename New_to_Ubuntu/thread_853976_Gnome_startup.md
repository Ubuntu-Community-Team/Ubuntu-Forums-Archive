---
title: "Gnome startup"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by justice_4_you on 2008-07-09
Hi everyone!

This is my problem (well is not really a problem, everything works, just it doesn't work like i'd like it to):

When my gnome starts up, it loads a number of external application i installed, compiz, emerald, and avant just as example.
Now what i wanted gnome to do, is to load showing just the splashscreen till everything is ready to be used, avoiding me to see avant getting crazy during its startup.

I tried editing gnome session using the gui provided by gnome itself, i put avant priority to 40, and emerald priority to 11 (just one more then compiz) but i just crashed the system. So i deleted /home/username/.gnome2/session and everything is exactely as it was before...

So, any idea to make my gnome load as i want?

i'm using UBUNTU 8.04

---

### Post by mcduck on 2008-07-09
So what you actually need is to dealy AWN startup until everything else is running?

You could create a script to start AWN with a bit of delay, and add that script to yoursession startup instead of starting AWN directly:

```
#!/bin/sh

sleep 20s
awn &
```

(to create the script just paste that code into text editor, save as "startawn.sh" or something, and right-click the file, go to Properties and set the file as executable.)

---

### Post by justice_4_you on 2008-07-09
actually is exactely the opposite.
i need gnome to delay the displaying of the desktop until everything has fully loaded.

---

### Post by mcduck on 2008-07-09
> **justice_4_you said:**
> actually is exactely the opposite.
i need gnome to delay the displaying of the desktop until everything has fully loaded.

I don't think that's possible. From your first post I understood that the actual problem would be that AWN acts funny when everything else isn't loaded yet. For that problme the delayed start of AWN is definitely the best solution.

---

### Post by justice_4_you on 2008-07-09
ok thanx!

Maybe someone else will have better news...
just another question..

looking at your code: what does that "&" char means??

---

### Post by mcduck on 2008-07-09
the "&" at the end of a command leaves the command running in background.

For example, if you run "awn" in a terminl the AWN will start, but it's attached to the terminal so you can't use that terminal for anything else until you close AWN. And if you close the terminal, AWN will close as well.

Adding the "&" to the end will leave the terminal usable to other tasks and leves AWN running even if you close the terminal.

---

### Post by justice_4_you on 2008-07-09
thanx again! i was looking for a way to do something like this...

---

