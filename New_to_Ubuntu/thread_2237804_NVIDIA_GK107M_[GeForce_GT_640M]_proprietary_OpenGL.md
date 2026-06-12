---
title: "NVIDIA GK107M [GeForce GT 640M] proprietary OpenGL vendor"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by Zach_Follette on 2014-08-04
Hi all, I am posting because of a little problem I am having with my NVIDIA and Intel cards.

Here is my 'Additional Drivers' screen showing that I am using the correct nVidia proprietary driver.
[IMG]http://i1375.photobucket.com/albums/ag446/zFollette/Screenshot-08042014-022000AM_zpsea78410e.png[/IMG]
But when I run the command ```
glxinfo | grep vendor
``` I get this output:
```

server glx vendor string: SGI
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: Intel Open Source Technology Center

```

I am not too sure what the 'server' and 'client' are, but I am wondering how to switch my OpenGL vendor to NVIDIA

---

### Post by kc1di on 2014-08-04
Is this an optimus card? where you choose either Intel or Nvidia?

if so you may want to try nividia prime 
[See here]("http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m") for info:

or bumblebee - [see here]("http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04")

---

### Post by Zach_Follette on 2014-08-04
> **kc1di said:**
> Is this an optimus card? where you choose either Intel or Nvidia?

if so you may want to try nividia prime 
[See here]("http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m") for info:

or bumblebee - [see here]("http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04")

Yes, it is an Optimus. I think I'll try prime because I was having some problems with bumblebee in Fedora 20. If prime fails, I'll look into bumblebee again, since Fedora and Xubuntu are completely different.

EDIT: Wow, thanks a lot.
```
glxinfo | grep vendor
``` now returns:
```

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

```

I used prime, if you're wondering.

---

### Post by kc1di on 2014-08-04
your welcome enjoy :)

---

