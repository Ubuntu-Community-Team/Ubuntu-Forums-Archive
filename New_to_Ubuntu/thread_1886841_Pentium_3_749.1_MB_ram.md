---
title: "Pentium 3 749.1 MB ram"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by walney_boy on 2011-11-25
Hi All

Managed to load on Ubuntu 11.10 onto an old (2000) Dell machine -XPS T500 PIII with 749.1 MB ram and 38.9 GB hard drive. 

It's working!! but would I be better off loading an earlier version of Ubuntu as the machine is so old? If so how would I go about it?

Many thanks

Walney_boy

---

### Post by Penguinnerd on 2011-11-25
Yeah, that would be a little slow with the default Ubuntu.

Don't use an old version. Use an alternate desktop environment. (Lubuntu or Xubuntu for a lightweight install)

I would strongly recommend Lubuntu. Just go to [http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/) and download the Intel x86 image, and install it the same way you did before.

---

### Post by MG&amp;TL on 2011-11-25
+1 for Lubuntu.

---

### Post by TenPlus1 on 2011-11-25
+1 for Lubuntu 11.10

also add "vm.swappiness = 10" to end of /etc/sysctl.conf

---

### Post by snowpine on 2011-11-25
No need to reinstall; you can install LXDE (the Lubuntu desktop environment) through the Software Center. :)

[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by walney_boy on 2011-11-25
Hi All

Thanks for the replies.

Snowpine I have installed LXDE (I think?!)

I ran the large command in the terminal window to remove ubuntu. Most of the icons went from the left hand side menu. Do I need to re-boot for the Lubuntu to take effect?? I've tried shutting down from the top right icon but system stays live.

Thanks

Walney_boy

---

### Post by snowpine on 2011-11-25
Log out and then you can  select the LXDE session from the login screen.

---

