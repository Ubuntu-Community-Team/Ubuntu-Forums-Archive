---
title: "[SOLVED] How do I force a 32 bit app to run on 64 bit system?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by hufferd on 2008-06-05
Can some one tell me how I can force a 32 bit app to run on a 64 bit system ? 

I have downloaded the software I need for my light scribe support from here but much to my disappointment I started trying to install it and it wont install I get an error something like 64 bit compatibility issue or some crap like that :( Anyone have any ideas?

---

### Post by wdaniels on 2008-06-05
What kind of install distribution is this light scribe thing? If it's a .deb pacakage you can use:

```
sudo dpkg -i --force-architecture <package file>.deb
```

---

### Post by drs305 on 2008-06-05
There was a post on exactly this issue a week or so ago. Check it out here:
[http://ubuntuforums.org/showthread.php?p=5052994](http://ubuntuforums.org/showthread.php?p=5052994)

---

### Post by roachk71 on 2008-06-05
Another possibility, if the program still won't run as expected, is that the **ia32-libs** package needs to be installed using Synaptic or Adept.

Many 32-bit applications need the 32-bit libraries to run on a 64-bit Linux box (I have the 32-bit Gens emulator, which won't render correctly without 'em.)  :twisted:

---

### Post by hufferd on 2008-06-05
> **drs305 said:**
> There was a post on exactly this issue a week or so ago. Check it out here:
[http://ubuntuforums.org/showthread.php?p=5052994](http://ubuntuforums.org/showthread.php?p=5052994)

HEy wow thanks I will take a look at this  

I did a search and nothing came up  but will take a look now thanks 
  ~D
:)

---

