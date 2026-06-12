---
title: "avahi-discover without GTK api's"
date: 2011-06-07
forum: Programming Talk
---

### Post by infant_coder on 2011-06-07
Hi,

I am trying to port avahi-discover to an embedded device which discovers services on local network. But avahi-discover uses GTK.

I am trying to write avahi-discover module without using GTK. Even the first version of avahi-discover has GTK in it. 

Any help would be appreciated.

---

### Post by Petrolea on 2011-06-07
You want to remove its GUI and make it a terminal application? That can cause a lot of trouble if it is a complex application (replacing buttons, printing and formating text...).

But I believe there should be a text-based alternative for this somewhere.

---

### Post by epages on 2011-07-05
You may also try avahi-browse

---

