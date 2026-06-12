---
title: "gnu cash problem"
date: 2005-02-02
forum: Repositories &amp; Backports
---

### Post by shrike on 2005-02-02
hi,

I am a total newbie... 8-[ fresh plastic smell and all... anyway I tried to install gnucash and it tells me that I need to install the following dependencies: *libarts or libarts-alsa, libdvdread2, and libvorbis0*.

My problem is that I have no idea how to get these dependencies if I have already linked apt-get or synaptic to other repositories? - I.E. Multiverse and Universe. :!:

---

### Post by davegod75 on 2005-02-02
how'd you try to install it?

sudo apt-get install gnucash


should work and resolve all dependency issuses automatically if i'm not mistaken

---

### Post by mendicant on 2005-02-02
I'm going to sound like a broken record on these forums, but I'd recommend using aptitude or synaptic instead of apt-get.  Aptitude is a drop in replacement for apt-get for common tasks, and has much better handling of automatically installed dependencies.

---

