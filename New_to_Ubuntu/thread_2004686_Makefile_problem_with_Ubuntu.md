---
title: "Makefile problem with Ubuntu"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by rangarajub on 2012-06-16
Hi,

I am trying to switch my development environment from a Fedora 10 Machine to an Ubuntu Machine. I am using Ubuntu 10.10 the Maverick Meerkat version. Everything is fine except one problem with running my Makefile. The Makefile has a statement like

BUILD_AREA_N_RFS_PREP:
          mkdir -p $(TOPDIR)/build/{toolchain/$(PROJECT_NAME),host_utils,projects/$(PROJECT_NAME),rootfs/$(PROJECT_NAME),images/$(PROJECT_NAME)}

But these directories are not getting created unless I modify this as multiple statements like

    mkdir -p $(TOPDIR)/build/toolchain/$(PROJECT_NAME)
    mkdir -p $(TOPDIR)/build/host_utils
    mkdir -p $(TOPDIR)/build/projects/$(PROJECT_NAME)
    mkdir -p $(TOPDIR)/build/rootfs/$(PROJECT_NAME)
    mkdir -p $(TOPDIR)/build/images/$(PROJECT_NAME)

The same problem occurred with another file which has  complex statement like the one above which worked when I split it to multiple statements. Can someone suggest what I need to do to make with the Makefile as it is. This is becoming irksome as I need to justify this change to the Linux team who are using Fedora :(

Thank you very much.
bhupathi

---

### Post by steeldriver on 2012-06-16
if I had to take a wild stab at this I would guess it's something to do with dash being the default /bin/sh in Ubuntu - you could try relinking /bin/sh to bash, i.e.


```
sudo ln -sf bash /bin/sh
```you can always revert it after with

```
sudo ln -sf dash /bin/sh
```

---

