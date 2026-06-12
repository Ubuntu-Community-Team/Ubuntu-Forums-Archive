---
title: "Seamonkey, 14.04"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by juliusagustus on 2014-04-18
No matter what I try, I cannot get seamonkey to run. When I run Seamonkey via the terminal I get this error 
"XPCOMGlueLoad error for file /home/thomas/seamonkey/libxul.so:libdbus-glib-1.so.2: cannot open shared object file: No such file or directory
Couldn't load XPCOM."
or when I install it, it won't open. I am on Ubuntu 14.04 trying to use seamonkey 2.25. Thank you!

---

### Post by vasa1 on 2014-04-18
Are you on 32- or 64-bit? Which version of Seamonkey did you install?

Edit: I'm on 64-bit so I ran ```
aria2c "ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.25/contrib/seamonkey-2.25.en-US.linux-x86_64.tar.bz2"
```
then unpacked in *~/Seamonkey* using the *Extract here* option in my file manager. I prefer having Seamonkey installed in my home folder.

---

### Post by juliusagustus on 2014-04-18
> **vasa1 said:**
> Are you on 32- or 64-bit? Which version of Seamonkey did you install?

Edit: I'm on 64-bit so I ran ```
aria2c "ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.25/contrib/seamonkey-2.25.en-US.linux-x86_64.tar.bz2"
```
then unpacked in *~/Seamonkey* using the *Extract here* option in my file manager. I prefer having Seamonkey installed in my home folder.
I am on 64 bit. I will give your thing a try!
I have the extracted version of it but I still get that error when I try to run it.
Edit 2: I got seamonkey working.

---

