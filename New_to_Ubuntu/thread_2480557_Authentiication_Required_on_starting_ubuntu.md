---
title: "Authentiication Required on starting ubuntu"
date: 2022-11-02
forum: New to Ubuntu
---

### Post by kostn70jl on 2022-11-02
Hi complete Linux and Ubuntu noob.
Just made my new installation  the latest Ubuntu desktop.
On first open, the system asked me to set a default keyring and so I put a random pass that thankfully I kept it written.
After that each time I start my pc (without my userpass required) the system asks me in  a window 

Authentication Required
 An application wants access to the keyring
"Default keyring", but  it is locked 
it has a field to  put in  the password and below a "Cancel"  or "Unlock" buttons.

If I press Cancel it does  not let me access  my pc if I put in the password the  system  is operational
Why it  this happening  and how do I get  rid of it ?
THANK YOU

---

### Post by TheFu on 2022-11-02
If you enable automatic logins, then multiple things that require access to credentials don't happen automatically, so the OS still needs access to keys to unlock some resources.  It is easier to just login with a password, IME.

[https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/) explains a few types of keyrings.

[https://www.fosslinux.com/2561/how-to-disable-keyring-in-ubuntu-elementary-os-and-linux-mint.htm](https://www.fosslinux.com/2561/how-to-disable-keyring-in-ubuntu-elementary-os-and-linux-mint.htm) explains how to make them non-obtrusive.

---

### Post by kostn70jl on 2022-11-02
Worked just fine.
Thanks for your advice and your time.

---

