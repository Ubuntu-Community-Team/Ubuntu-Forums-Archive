---
title: "Downloading .debs from the repos without installing them"
date: 2006-10-12
forum: Programming Talk
---

### Post by rekahsoft on 2006-10-12
I want to just download .debs from the repos for use offline..is there a simple way to do this instead of having to find the the web address that i would have to wget? Something like sudo apt-get source <package-name> although this just downloads the sources...i want to downoload the .deb...is there a way to do this?

---

### Post by fatsheep on 2006-10-12
You could try checking the "download packages only" option in synaptic when you're installing something.  I'm not really sure where it downloads the packages to though...

---

### Post by rekahsoft on 2006-10-12
> **fatsheep said:**
> You could try checking the "download packages only" option in synaptic when you're installing something.  I'm not really sure where it downloads the packages to though...

hmm..well i want to be able to do it from a shell script if that helps...

---

### Post by amo-ej1 on 2006-10-13
quoting the  ye good ol' ```
man apt-get
```:

```

       -d, --download-only
              Download only; package files are only retrieved, not unpacked or
              installed. Configuration Item: APT::Get::Download-Only.


```

After ```
apt-get -d install package
``` you will be able to find the packages in ```
/var/cache/apt/archive/
```.

---

### Post by Engnome on 2006-10-13
[www.packages.ubuntu.com](www.packages.ubuntu.com)

---

