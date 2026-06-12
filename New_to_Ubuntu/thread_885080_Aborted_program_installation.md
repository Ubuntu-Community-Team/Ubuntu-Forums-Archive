---
title: "Aborted program installation"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-08-09
I was attempting to install a home finance program called Buddi, from a site reached via a link on the Linux App Finder site. After it downloaded, I was offered to option to install using the Debian installer, something I've done before with no problem. This time however, the installation stalled part way through. Eventually, not knowing what else to do, I rebooted.

Unfortunately now, if I try to run the Debian installer, Synaptic, etc, I'm being told that another installer is in operation and I need to close it first, which I haven't the faintest idea how to do. Can anyone point me in the right direction please?

---

### Post by spiderbatdad on 2008-08-09
There may be better ways, but```
sudo killall dpkg
sudo killall apt-get
sudo killall synaptic
```

You may also need to run:```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

