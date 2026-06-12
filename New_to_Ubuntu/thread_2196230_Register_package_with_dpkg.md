---
title: "Register package with dpkg"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by colingbian on 2013-12-28
Hi,

I wanted to install eclipse juno on Ubuntu (apt-get installs an older version of eclipse). I downloaded the archive from the eclipse website and extracted it into the **/opt** folder, and then created a symlink in the **/usr/local/bin** folder.

Eclipse runs fine, but the problem is that dpkg doesn't know about it (e.g. **apt-get remove eclipse** doesn't work).

Is there a way to tell dpkg that I've manually installed a package?

Thanks in advance for your help.

---

### Post by sisco311 on 2013-12-28
You can use checkinstall to install the package. See: [uhelp]community/CheckInstall[/uhelp]

---

### Post by Dennis N on 2013-12-28
As far as I know, there is no way to do that. You need to install from a .deb file for it to be manageable. Otherwise, you are the package manager. 

Sometimes there is an uninstall script included with the non-deb package to remove it. Otherwise, you would just delete the program's folder and contents manually and any links to it that you made to get rid of it.

Use the repositories whenever possible. Easier and safer.

---

### Post by colingbian on 2013-12-29
Thanks for your answers. I gather that I'd have to create a .deb file myself and install it from that.

---

### Post by steeldriver on 2013-12-29
You may be able to use 'alien' to automate the creation of a deb from the tarball - however I don't know how reliable it is, you should look at sisco311's suggestion using checkinstall

---

### Post by sisco311 on 2013-12-29
checkinstall works with any command. Something like:
```

sudo checkinstall --pkgname eclipse \
--pkgversion 4.3.1 \
--pkgarch amd64 \
--pkglicense EPL \
--requires default-jre \
sh -c 'tar xfvz eclipse-standard-kepler-SR1-linux-gtk-x86_64.tar.gz -C /opt/ && ln -s /opt/eclipse/eclipse /usr/local/bin/eclipse'
```

should create  a .deb package

---

### Post by steeldriver on 2013-12-29
^^^ ah thanks for that, I hope the OP comes back and sees it - I will edit my previous post since I'm not sure how reliable alien is

---

