---
title: "Broken Package(s) Oneiric"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by oserdavid on 2011-10-22
Gentle gurus
I'm having trouble with a broken package in Oneiric 64 and I'm getting this:

Preparing to replace libcupsimage2 1.5.0-8 (using .../libcupsimage2_1.5.0-8ubuntu2_amd64.deb) ...
rm: cannot remove `/usr/share/doc/libcupsimage2': Directory not empty
dpkg: error processing /var/cache/apt/archives/libcupsimage2_1.5.0-8ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libcupsimage2_1.5.0-8ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I actually went in using 'rmdir --ignore etc, etc' (forgotten the etc bit, need to check it again) and managed to delete the directory. But this has not helped. The above message still appears.

I suspect it may be because I'm working from a Live USB stick - but just in case it isn't...

---

### Post by cavh on 2011-10-22
In a terminal, try 

```
sudo apt-get update
```

followed by 

```
sudo apt-get purge libcupsimage2
```

followed by

```
sudo apt-get install libcupsimage2
```

---

### Post by oserdavid on 2011-10-22
Thanks Cavh - that worked fine. Now I just how to work out how to update my software catalog. Think I'm going to start all over again with a new installation - trying not to break Software-update again!
David

Oops! Meant Software-Center

---

### Post by Silent Warrior on 2011-10-22
Uh... I suppose that would avoid any issues from release upgrades, but I'm quite sure that's overkill. One single package conflict/problem doesn't mean your entire system is falling to bits, mkay?

---

### Post by oserdavid on 2011-10-22
> **Silent Warrior said:**
> Uh... I suppose that would avoid any issues from release upgrades, but I'm quite sure that's overkill. One single package conflict/problem doesn't mean your entire system is falling to bits, mkay?

Good point but I'm just trying to run a usefulive system which is reasonably fault free on a .nerd stick. It no big deal to start over again if I break Software Center (even though I know I can download and use Synaptic). So far so good....
David

---

### Post by cavh on 2011-10-23
Cool, please mark the thread as solved using the thread tools at the top right.

---

