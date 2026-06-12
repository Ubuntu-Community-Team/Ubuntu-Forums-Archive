---
title: "gpg errors"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by beew on 2011-12-04
It used to be that when you add a ppa to your sources list the gpg key is automatically added as well, but it seems that the mechanism is broken recently so that you get a gpg error every time to add a ppa and have to fix it manually, it is getting rather annoying.

I am wondering if anyone has any idea what is going on, has there been some changes, or just a bug?

---

### Post by Soulcage on 2011-12-04
I always use ```
sudo add-apt-repository
``` so I don't have to worry about it.

---

### Post by beew on 2011-12-04
Yes, that would import the gpg key, but so should just adding the apt-line to synaptic. It did before.

---

