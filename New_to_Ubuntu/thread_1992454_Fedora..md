---
title: "Fedora."
date: 2012-05-31
forum: New to Ubuntu
---

### Post by dep0 on 2012-05-31
Hi. Is it possible to change from ubuntu 10.04LTS to the latest distrubution of fedora without having to burn the iso image?

---

### Post by Cheesemill on 2012-05-31
Short answer, No :(

Long answer, Yes. But it's complicated and a lot of unnecessary work when you can use a CD or USB and be installed in minutes.
It would be a clean installation anyway so there is no benefit in doing what you're asking.

---

### Post by deadflowr on 2012-05-31
Here's what I would call part one to the long answer cheesemill was alluding to:

[http://ubuntuforums.org/showthread.php?t=1549847]("http://ubuntuforums.org/showthread.php?t=1549847")

Part two would involve doing a regular clean install, as fedora and ubuntu are built differently. One uses the yum/rpm(fedora)packaging system, the other runs the apt/debian packaging system(ubuntu).

You'd be better off just burning it like normal, as Cheesmill said, It can be very complicated.

---

### Post by Cheesemill on 2012-05-31
> **deadflowr said:**
> Here's what I would call part one to the long answer cheesemill was alluding to:

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

Part two would involve doing a regular clean install, as fedora and ubuntu are built differently. One uses the yum/rpm(fedora)packaging system, the other runs the apt/debian packaging system(ubuntu).

You'd be better off just burning it like normal, as Cheesmill said, It can be very complicated.

I'd call that part 2.

First you need a separate partition on your drive to install Grub 2 and the ISO onto, otherwise you would be trying to install over the partition that contains the ISO you are booted from - Catch 22. As you cannot mess with the partitions on a running system you would have to do something like repurposing your swap partition to create a space for the temporary Grub 2 files and Fedora ISO.

---

### Post by deadflowr on 2012-05-31
> **Cheesemill said:**
> I'd call that part 2.

First you need a separate partition on your drive to install Grub 2 and the ISO onto, otherwise you would be trying to install over the partition that contains the ISO you are booted from - Catch 22. As you cannot mess with the partitions on a running system you would have to do something like repurposing your swap partition to create a space for the temporary Grub 2 files and Fedora ISO.

Exactly, it seems like too much of a hassle to load and install a system you might not even like.

---

### Post by idoitprone on 2012-05-31
> **dep0 said:**
> Hi. Is it possible to change from ubuntu 10.04LTS to the latest distrubution of fedora without having to burn the iso image?

You can virtualize fedora in kvm, virtualbox, or qemu

there will be a performance penalty

---

