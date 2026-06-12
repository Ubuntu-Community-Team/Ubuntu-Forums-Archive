---
title: "Flash Player apt-get failure"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by williamHH on 2008-04-23
```
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
```
is what I get whenever I try to "sudo apt-get flashplugin-nonfree".
I really am a newbie, this is just about the only cmd-line thing I know.
EDIT:
oh and also when I try to use the add/remove thing, it throws this error at me "Amarok cannot be installed on your computer type (i386)", and Synaptic throws another strange error at me.

---

### Post by myusername on 2008-04-23
try installing ubuntu-restricted-extras it installs all the codecs and flash

---

### Post by Xiong Chiamiov on 2008-04-23
[[link]]("http://www.psychocats.net/ubuntu/flash")

---

### Post by williamHH on 2008-04-23
> **myusername said:**
> try installing ubuntu-restricted-extras it installs all the codecs and flash
```
E: Couldn't find package ubuntu-restricted-extras
```

---

### Post by Xiong Chiamiov on 2008-04-23
> **williamHH said:**
> ```
E: Couldn't find package ubuntu-restricted-extras
```
I think my link will be more helpful, as psychocats has outlined everything very well.

---

### Post by williamHH on 2008-04-23
Alright, I think i fixed it, just had to set all the repositories to active. Now about that "i386" thing in my earlier post...(nvm fixed.)

---

