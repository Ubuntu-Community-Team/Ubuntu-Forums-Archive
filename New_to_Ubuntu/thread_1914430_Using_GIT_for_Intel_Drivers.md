---
title: "Using GIT for Intel Drivers"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by Cynic411 on 2012-01-24
I want to update my OpenGL
I'm using

[HTML]http://intellinuxgraphics.org/download.html[/HTML]

as my source but it requires I install a repository:

```
git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
```

Git looks installed in synaptic and I've tried to add the repository via synaptic too, I just broke it.

So what do I do to install git repositories?

Thanks

Cynic411

---

### Post by sanderd17 on 2012-01-24
Git is a version system. So it's used to keep track of source code.

Dowloading this from GIT will only get you the source code. They also provide a tarball, so it might be more simple to dowload that.

Once you have the tarball, unpack it and read the README.

But it would be even more easy if you find a binary.

---

### Post by satanselbow on 2012-01-24
You need to clone the tree:

```
git clone git://gitorious.org/mypaint/mypaint.git
```

If you are not familiar with the steps involved it might be better to try compiling a simple app 1st before you dive in and potentially bork your X - steps required may not be exactly the same but will get you into the swing of things with something less likely to cause serious breakage ;)

** edit as stated above - tarballs or debs would be preferable ;) **

---

### Post by sanderd17 on 2012-01-24
And I don't know if it's really safe to do either. it will probably be better to upgrade to the next version than to upgrade only your driver.

But even for that, it's a bit early. Precise is only in Alpha right now.

---

### Post by Cynic411 on 2012-01-26
I guess I'm over-reaching with my machine.

Keep running up to the fact I need more with my machine. More range, more power ect. Fiddling with my drivers won't change that.

Ahh...Asus Transformer Prime..one day :)

Thanks for the input guys

---

