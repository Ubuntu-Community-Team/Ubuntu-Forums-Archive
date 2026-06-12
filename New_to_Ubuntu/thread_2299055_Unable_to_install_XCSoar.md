---
title: "Unable to install XCSoar"
date: 2015-10-15
forum: New to Ubuntu
---

### Post by john_smith32 on 2015-10-15
I am trying to install a program in Ubuntu 15.04 that requires libjpeg62-turbo.

This is not part of the 15.04 package so the install fails.

Can I get and install this library or will it interfere with the package (libjpeg62) already installed?

Thanks,
John

---

### Post by sandyd on 2015-10-16
What software are you

Debian has [libjpeg62-turbo]("https://packages.debian.org/sid/libjpeg62-turbo"). It mentions that the source package is called libjpeg-turbo.

So, back to Ubuntu, I find another [libjpeg-turbo]("https://launchpad.net/ubuntu/+source/libjpeg-turbo")

Debian seems to have moved to libjpeg62-turbo in favor of libjpeg-turbo8. No idea if they are compatible.

I did some edits to test it out:
* Note, commands that are in sudo must be run as sudo to preserve file ownership when extracting/repacking
```

wget http://download.xcsoar.org/releases/6.8.2/LINUX/xcsoar_6.8.2_amd64.deb
mkdir tmp
sudo dpkg-deb -R xcsoar_6.8.2_amd64.deb tmp
sudo nano tmp/DEBIAN/control

```

Here, I replaced libjpeg62-turbo with libjpeg-turbo8 and saved the file with control+x

```

sudo dpkg-deb -b tmp/ xcsoar_6.8.2-new_amd64.deb
sudo rm -rf tmp/
sudo chown $(whoami):$(whoami) xcsoar_6.8.2-new_amd64.deb

```

You now have a file named xcsoar_6.8.2-new_amd64.deb that you can try to install.

I would attach one to this post for you, but it seems to be a tad too large.

---

