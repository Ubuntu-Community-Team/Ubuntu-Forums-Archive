---
title: "trying to install the fglrx driver for an ATI x1300"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by herbert tamayo on 2008-06-18
Hi,I have an ATI Radeon X1300 series, Few months ago I tried to install the apropiated driver for my video card, not from the repos, I had to do it manually. So after read several howtos and some post I didn't work.

Recently I knew that there are an update for the driver, so, I tried to do it again from scatch, but I found the next error:

```

0. I uninstalled the previous version of the driver (apt-get remove fglrx-driver fglrx-kernel-src fglrx-control) and then I create the new deb packages and I installed them.

```

```

1. #module-assistant prepare generated the next: "build-essential is already installed 0 packages for install, 0 for remove, 0 update"

```

```

2. #module-assistant build fglrx: "fglrx-kernel-2.6.17-2-686 will be uninstalled .... 1 packages for uninstall"

```

```

3. #module-assistant install fglrx : "it can be installed because it exists..."

```

4. If I do glxinfo | grep direct: the answer is no

5. all these steps were didwith the X-server off
   
So, it seems that the previous module is still in the kernel, but the output of module-assistant prepare said that it doesn't necessary to reinstall it.

All right, my questions are:
1. how can I bringing up from the kernel the previous fglrx module?

2.  if that doesn't work, how can I remove totally that fglrx module?

thanks a lot

---

### Post by bufsabre666 on 2008-06-18
open a terminal applications->accessories->terminal

```
sudo apt-get update && sudo apt-get install envyng-core envyng-gtk
```

then when thats done

applications->system tools-envyng

and install the ati drivers from there, it configures it for you and has fairly recent drivers, not the most recent but you hardly need the most recent

---

