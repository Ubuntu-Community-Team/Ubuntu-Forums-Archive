---
title: "[SOLVED] xorg.conf editing"
date: 2008-12-26
forum: Programming Talk
---

### Post by cmat on 2008-12-26
I turned out empty on google but I'm interested in a library that can edit/add/remove keys within the xorg.conf file. Preferably in Python but if you have some code in other languages I could translate it. I'm interested in this so I can create a script that can modify the files contents.

---

### Post by meanburrito920 on 2008-12-26
idk if a library currently exists for this, but seeing as how it is simple file editing, you could probably throw something together rather fast. All you need to do is just do a seek for the key name and then standard IO would take care of the rest. Hmmm... I wouldnt mind throwing something together for this when I have a little time. Maybe tomorrow I'll throw write this if no one can find a currently existing python library.

---

### Post by cmat on 2008-12-26
I would attempt to create such a library but I can't trust anything I make to such an important file. There are lots of things that I don't know about that can go wrong. I rather have a tried and tested library.

---

### Post by meanburrito920 on 2008-12-26
Very true. However, I doubt there exists a library to edit the file, especially if nothing came up in a google search. This is probably due to the fact that most gurus will edit the file by hand, and there are few applications that actually deal with the file, so there was no real demand for a library in any language.

---

### Post by cmat on 2008-12-26
I'm making an application that manipulates *xorg.conf* for setting up Wacom tablets. The driver exists on linux but various features don't work yet without hacking the xorg.conf file. To change settings I have to keep opening the thing up in gedit and changing values. I want to create a GUI to do this instead. I'm pretty good at wxPython so the only issue is file manipulation. It's outside my comfort zone. Editing xorg.conf is one thing but it can be a real turn off for new users. 

Since Ubuntu 9.04 may revert back to using xorg.conf I think its time for such a library.

---

### Post by meanburrito920 on 2008-12-26
You've been beaten to the punch

[http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243)

---

### Post by meanburrito920 on 2008-12-26
You've been beaten to the punch

[http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243)

---

### Post by meanburrito920 on 2008-12-26
woops, double post. dont know how that happened.

---

### Post by cmat on 2008-12-27
I've seen that but it's written in C++ I think. C++ make me a sad person. Also it's more like a pocket knife for xorg rather than doing the specific task I need to do.

---

### Post by slavik on 2008-12-27
I know that Perl has a config module that can be used to read/write configs. It is stipulated in the config that it uses the apache format which is very similar to what Xorg uses. Maybe that is worth a look.

---

### Post by cmat on 2008-12-27
Thank you. I've been busy and I've come up with a Reg. Exp. for Xorg sections. Here's what I came up with...

```
^[ \t]*Section[ \t]+\"\w+\".*?|^\s+\w+\s+.*?$|^EndSection
```

This is my first *real* attempt at using the re module so any feedback to improve this critical item is much appreciated.

---

### Post by slavik on 2008-12-27
Perl6 way:
```

grammar Config {
  token TOP { [<section>|<option>]* }
  token section { '<Section ' <name> '>' [<option>|<section>]* </Section> }
  token option { <name> ['=' <value>]? <value>* \n }
  token name { \w+ }
  token value { \w+ }
}

```
Code is untested, but should be similar to what is pictured above. Of course that is only for reading the Xorg/Apache style config, writing them would be a bit different.

Also, Apache can have options not belonging to a section, Xorg does not.

---

### Post by tseliot on 2008-12-27
> **cmat said:**
> I turned out empty on google but I'm interested in a library that can edit/add/remove keys within the xorg.conf file. Preferably in Python but if you have some code in other languages I could translate it. I'm interested in this so I can create a script that can modify the files contents.

I developed X-Kit which is installed by default in Ubuntu now (since Intrepid) as it's already used by Jockey (Restricted Drivers Manager), EnvyNG, (in some cases) Update Manager and Mythbuntu. The name of the package is "python-xkit".

It's a Python library which does exactly what you need. You can get the latest stable release from [my bazaar branch]("https://code.launchpad.net/~albertomilone/xorgparser/main") or simply [download the tarball]("https://code.launchpad.net/xorgparser/+download").

> **cmat said:**
> I'm making an application that manipulates *xorg.conf* for setting up Wacom tablets. The driver exists on linux but various features don't work yet without hacking the xorg.conf file.
I'm working on this as you can see in [this spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/wacom-tablets-ui"). We discussed this project at the UDS in Mountain view.

---

### Post by cmat on 2008-12-27
> **tseliot said:**
> I developed X-Kit which is installed by default in Ubuntu now (since Intrepid) as it's already used by Jockey (Restricted Drivers Manager), EnvyNG, (in some cases) Update Manager and Mythbuntu. The name of the package is "python-xkit".

It's a Python library which does exactly what you need. You can get the latest stable release from [my bazaar branch]("https://code.launchpad.net/~albertomilone/xorgparser/main") or simply [download the tarball]("https://code.launchpad.net/xorgparser/+download").


I'm working on this as you can see in [this spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/wacom-tablets-ui"). We discussed this project at the UDS in Mountain view.

Excellent! Thanks for all your help. Marked as solved.

EDIT: Where can I get documentation for X-Kit?

---

### Post by slavik on 2008-12-28
> **tseliot said:**
> I developed X-Kit which is installed by default in Ubuntu now (since Intrepid) as it's already used by Jockey (Restricted Drivers Manager), EnvyNG, (in some cases) Update Manager and Mythbuntu. The name of the package is "python-xkit".

It's a Python library which does exactly what you need. You can get the latest stable release from [my bazaar branch]("https://code.launchpad.net/~albertomilone/xorgparser/main") or simply [download the tarball]("https://code.launchpad.net/xorgparser/+download").


I'm working on this as you can see in [this spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/wacom-tablets-ui"). We discussed this project at the UDS in Mountain view.

5 point infraction to you for not posting sooner. :P

---

### Post by tseliot on 2008-12-28
> **cmat said:**
> Excellent! Thanks for all your help. Marked as solved.

EDIT: Where can I get documentation for X-Kit?

It's all in the docstrings:
```
import XKit.xorgparser
help(XKit.xorgparser)
```
or
```
import XKit.xutils
help(XKit.xutils)
```

NOTE: xutils has some features you might want to use (it's all documented).

> **slavik said:**
> 5 point infraction to you for not posting sooner.
ouch ;)

---

