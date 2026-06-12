---
title: "Error compiling VLC Players on Ubuntu 12.04."
date: 2013-09-25
forum: Packaging and Compiling Programs
---

### Post by Javaid.Salman on 2013-09-25
When I issue this command for dependent libraries for VLC Player

```
sudo apt-get build-dep vlc
```


The error I get in return is:


```
The following packages have unmet dependencies:
 libpulse-dev : Depends: libpulse0 (= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15.2 is to be installed
                Depends: libpulse-mainloop-glib0 (= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15.2 is to be installed
 libudev-dev : Depends: libudev0 (= 175-0ubuntu9.1) but 175-0ubuntu9.2 is to be installed
E: Build-dependencies for vlc could not be satisfied.

```

I will be deeply grateful for any help.

---

