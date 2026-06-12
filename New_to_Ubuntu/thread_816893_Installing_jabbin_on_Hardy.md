---
title: "Installing jabbin on Hardy"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Lelouch on 2008-06-03
When I try to install jabbin2beta (.deb) I get an error saying that libssl0.9.7 is required!

Anyway, I installed libssl0.9.8 (since it is the only version available for hardy), but I still get this error!

Where can I find libssl0.9.7 for hardy?

Thanks,

---

### Post by PinkFloyd102489 on 2008-06-03
libssl was updated because of the security hole. Using an older version would pose a risk to your system.

---

### Post by prshah on 2008-06-03
> **Lelouch said:**
> When I try to install jabbin2beta (.deb) I get an error saying that libssl0.9.7 is required!
Anyway, I installed libssl0.9.8 (since it is the only version available for hardy), but I still get this error!


You can test a forced install with this:```
sudo dpkg --dry-run --ignore-depends --install jabbin2beta.deb
```; of course please replace "jabbin2beta" with the correct filename.

I'd suggest informing the "jabbin"s about the changed ssl dependency.

---

### Post by SanskritFritz on 2008-08-11
Here is how i did it:

```
sudo dpkg --ignore-depends libssl0.9.7 --install jabbin_2.0beta2-1baltix1_i386.deb
cd /usr/lib/
sudo ln libssl.so.0.9.8 libssl.so.0.9.7
sudo ln libcrypto.so.0.9.8 libcrypto.so.0.9.7
```

---

