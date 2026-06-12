---
title: "How do I reinstall a package?"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by maverickbane on 2013-06-16
Hi guys. I'm pretty new to Linux and Ubuntu, so please go easy...

I recently installed shellinabox via apt-get and it's been running fine, until I noticed that when using Firefox 15 or above, certain keys don't register, for which I need to update a file in the installation package (vt100.js) and reinstall. I have downloaded the package from GitHub and edited it, but how do I install it?

Can I just configure, make and make install the downloaded package which is the same version without removing the version installed via apt-get?

Thanks in advance :o)

---

### Post by MidnightGrey on 2013-06-16
Since you've edited the version you pulled from Git, it is no longer the same version as the one you obtained from apt-get.
The safest option would to be just remove the package first, before installing your local version.
You can reverse apt-get installs by using:
```
sudo apt-get remove shellinabox
```

---

