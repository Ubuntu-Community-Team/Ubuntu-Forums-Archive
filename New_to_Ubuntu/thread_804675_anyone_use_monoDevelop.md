---
title: "anyone use monoDevelop?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by muteXe on 2008-05-23
any use this on xubuntu?  Got a few questions...

---

### Post by kellemes on 2008-05-23
> **muteXe said:**
> any use this on xubuntu?  Got a few questions...

You better ask the questions.. ;-)

---

### Post by muteXe on 2008-05-23
Created a new solution, not even added to it yet. It's just the "hello world" example. When i try to build this I get "Build failed. Exexcutable not found: /usr/bin/gmcs". I've cleary not installed something!
Any ideas?
Cheers :o)

---

### Post by N.N. on 2008-05-23
> **muteXe said:**
> Created a new solution, not even added to it yet. It's just the "hello world" example. When i try to build this I get "Build failed. Exexcutable not found: /usr/bin/gmcs". I've cleary not installed something!
Any ideas?
Cheers :o)

Indeed. Make sure you have the mono-gmcs package installed: ```
sudo aptitude install mono-gmcs
```

If you find out that you are missing other files related to monodevelop, try re-installing the package from aptitude: ```
sudo aptitude install monodevelop
``` Installing monodevelop from aptitude will also install mono-gmcs, but installing it from Synaptic won't.

---

### Post by muteXe on 2008-05-23
aaaaaaah!  Cheers for that, i think i installed mono from synaptic.  i'll be doing more from the command line in the future.
thanks again,
mute

---

