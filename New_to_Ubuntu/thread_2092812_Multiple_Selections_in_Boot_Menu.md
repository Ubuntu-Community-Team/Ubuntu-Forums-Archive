---
title: "Multiple Selections in Boot Menu"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by StatusFresh on 2012-12-08
Why do I have 4 different options for choosing the Ubuntu I want to load? The disk management in my Windows doesn't show any new partitions besides a 6 GB one but there 2 regular ubuntu options and 2 recovery, and how would I get rid of the unnecessary ones? 

[[IMG]http://img594.imageshack.us/img594/8964/20121208215423.jpg[/IMG]]("http://imageshack.us/photo/my-images/594/20121208215423.jpg/")

---

### Post by Dennis N on 2012-12-08
You have two entries for each kernel that has been (and still is) installed. Old kernels are not automatically removed by kernel upgrades. 

Normally you don't boot using the recovery mode.

You can use a tool like Ubuntu tweak to remove older kernels.

---

### Post by StatusFresh on 2012-12-08
Thank you, appreciate it

---

### Post by Paqman on 2012-12-09
> **Dennis N said:**
> 
You can use a tool like Ubuntu tweak to remove older kernels.

Yep, or something like Synaptic Packager Manager. Uninstalling old kernels removes them from the list.

---

