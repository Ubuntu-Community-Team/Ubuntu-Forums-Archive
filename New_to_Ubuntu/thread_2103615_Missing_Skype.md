---
title: "Missing Skype?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Oweirdone on 2013-01-10
I installed Skype on my laptop, and now it's not there. I can't find it through the home search, or at all in the software manager? Anyone know what's going on?

Many thanks

Owe.

---

### Post by LuciferRex on 2013-01-10
have you tried running it from the terminal? ```
skype
```

---

### Post by Oweirdone on 2013-01-10
```
~$ skype
skype: command not found

```

---

### Post by fantab on 2013-01-10
how did you install it? from software center or directly from Skype?

---

### Post by Oweirdone on 2013-01-13
From the software center, where it no longer is :\ I'll give it a shot from Skype :)

---

### Post by walternzani on 2013-01-13
Have you tried reinstalling from the terminal?

---

### Post by fantab on 2013-01-13
Did you enable required repositories? To install certain NON Open Source Applications you have to enable "Independent" and Canonical 'Partner' repos. If not you can enable them using software center or Synaptic package manager or Software Sources.

---

### Post by scarabcoder on 2013-01-13
> **Oweirdone said:**
> I installed Skype on my laptop, and now it's not there. I can't find it through the home search, or at all in the software manager? Anyone know what's going on?

Many thanks

Owe.
Okay i've had that problem, just install it from skype.com, from there it will open the Software Center. That fixed it for me!

---

### Post by drawkcab on 2013-01-14
There's a new version of Skype I think.  I installed it on a buddy's machine via ppa.

---

### Post by d4m1r on 2013-01-14
Doesn't sound like it was ever installed or must have been removed...You can reinstall it using the command below:

```
sudo apt-get install skype
```

If it returns some kind of error, post it here.

---

### Post by Oweirdone on 2013-01-23
Sorry about not returning sooner guys, had a few screen issues :')

Skype is all nicely installed again, I got it off their main site this time rather than Software Manager, and it all works fine :)

Thanks for all the help,

Owe.

---

