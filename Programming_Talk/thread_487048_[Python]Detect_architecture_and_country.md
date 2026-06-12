---
title: "[Python]Detect architecture and country"
date: 2007-06-28
forum: Programming Talk
---

### Post by Kiwinote on 2007-06-28
For a program I am writing I have been googling on ways to detect the architecture and locale on a computer. 
For the architecture detection I have found the platform.machine() command. The only thing is, is that I can't find a list of all possible outputs. Any ideas? (Preference would be the same way that apt uses to decide which architecture package to download)
I have not yet been able to find anything that can detect the country code of the country you are in. As far as I know this should be hidden in you system somewhere, because when you install Ubuntu you have to select your location. Ideas would be appreciated.

Thanks,
Kiwinote

---

### Post by pmasiar on 2007-06-28
check [http://docs.python.org/lib/module-locale.html](http://docs.python.org/lib/module-locale.html) - does it help?

---

### Post by Kiwinote on 2007-06-30
I found that one, but it didn't seem to work: for me it gives ```
>>> import locale; print locale.getlocale(locale.LC_ALL)
(None, None)
```
Does it work for you? Any other ideas..?

---

### Post by Kiwinote on 2007-07-02
ok, solved the architecture one with ```
architecture = commands.getoutput('apt-cache -v')
architecture = architecture.split(" ")[4]
```
Any ideas on the country detection?

---

### Post by ssam on 2007-07-02
```

import os
os.environ['LANG']

```

will get you language

```

tz = commands.getoutput('date +%Z')

```

will get you timezone (though there is probably a neater method)

```

arch = commands.getoutput('uname -m')

```
might be more portable (should work on any linux/unix) for getting arch

---

### Post by Kiwinote on 2007-07-02
> **ssam said:**
> ```

import os
os.environ['LANG']

```
will get you language

The second set of letters is the country of the language. It doesn't refer to the country you are in, so that doesn't help too much. (someone in France could have installed an English system)
> **ssam said:**
> ```

tz = commands.getoutput('date +%Z')

```

will get you timezone (though there is probably a neater method)
doesn't tell you which country in the timezone you are in..

Any other ideas?
Thanks,
Kiwinote

---

### Post by Kiwinote on 2007-07-03
Anyone else got ideas on country detection? (bash / python / filename)

---

### Post by christhemonkey on 2007-07-03
The only way i can think of getting the users location accurately is, when installing ubuntu your are prompted for your location, this is saved in your evolution contacts.

So you can get this information by parsing the evolution contacts for the current user names details and then getting the country of their address.


The "about me" dialog has this information by doing just that (but its written in C) if you can try and disect some meaning form how it goes about it see here:
[http://svn.gnome.org/viewcvs/gnome-control-center/trunk/capplets/about-me/gnome-about-me.c?revision=7523&view=markup](http://svn.gnome.org/viewcvs/gnome-control-center/trunk/capplets/about-me/gnome-about-me.c?revision=7523&view=markup)

This should be fairly trivial(ish) to implement.

---

