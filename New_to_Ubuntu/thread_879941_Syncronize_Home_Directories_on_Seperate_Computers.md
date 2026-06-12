---
title: "Syncronize Home Directories on Seperate Computers?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by chris062689 on 2008-08-04
I have a laptop, and my main computer.
I was just curious, is it possible to sync my home directories so no matter which one I use (for example; if I had to run out with my laptop) everything would be synchronized?  Settings, programs, etc?
I've seen some SVN programs put a green checkmark next to files that are up-to-sync.
I'm just curious if this kind of thing is actually possible.
It would be neat!

---

### Post by northern lights on 2008-08-04
[Unison]("http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html") is a powerful folder synchronizer that works across platforms.

It's in the repositories```
sudo apt-get update && sudo apt-get install unison
```

---

