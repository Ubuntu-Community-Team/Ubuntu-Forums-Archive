---
title: "re install unity  12.04"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by ub9876 on 2013-06-25
I got rid of unity and have some problems like VLC not installing etc. I put up with it for months but now want to reinstall the 12.04
defaults like Unity and do a full repair on the OS.  I want to use the terminal.  What code should I use to do this.

---

### Post by Mark Phelps on 2013-06-26
As far as I know, there is no command line option for doing a reinstallation; instead, you have to use dpkg and reinstall selective packages.

The Ubiquity installer runs as a GUI, and I'm not aware of any way to run it in the terminal.

If you simply want the Unity desktop back, you could simply reinstall the ubuntu-desktop package.

---

### Post by snowpine on 2013-06-26
Try:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
```

to update your system and reinstall all the default components of Ubuntu Unity Desktop.

---

