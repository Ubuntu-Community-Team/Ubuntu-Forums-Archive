---
title: "About Me App is Missing an Option"
date: 2011-05-30
forum: Programming Talk
---

### Post by Metungkp on 2011-05-30
I've got a Fujitsu U810 on Ubuntu 11.04.  My About Me Application is missing the Fingerprint Authentication Option.  I've been searching for 3 days to no avail. 

I'm not sure if this is related but my Ubuntu Software Center is not working right.  I was going to uninstall About Me and reinstall but i couldn't.  Nothing happens when I enter a letter in the search box.  I only get the busy clock.  Nothing also happens when I click installed software or when i click an option, i only get the clock.  I just noticed this problem just before starting this thread.

Please, Help!


Thanks!
KP

---

### Post by Metungkp on 2011-05-30
I got this when I tried running an update:


E: Malformed line 62 in source list /etc/apt/sources.list (URI)
E: The list of sources could not be read.

---

### Post by epicoder on 2011-05-30
Sounds like your sources.list has an error in it. This, thankfully, is easily fixed.

See this [Ubuntu Docs](https://help.ubuntu.com/community/Repositories/CommandLine) page for a good guide to editing it.

If that page doesn't help you, then paste line 62 of /etc/apt/sources.list in code tags here.

---

### Post by Petrolea on 2011-05-30
> **Metungkp said:**
> I got this when I tried running an update:


E: Malformed line 62 in source list /etc/apt/sources.list (URI)
E: The list of sources could not be read.

The link to which the program should connect is probably incorrect or it is not correctly typed. Post the line here and we'll see.

---

### Post by Metungkp on 2011-05-30
Thanks>  I just deleted thst line

---

### Post by Petrolea on 2011-06-01
> **Metungkp said:**
> Thanks>  I just deleted thst line

You can mark this as [SOLVED] now :)

---

