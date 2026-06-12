---
title: "Installing a new HDD"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-08-22
Hello Everyone
                            I'm installing a new 500GB HDD. I'm dual booting Ubuntu 12.04 and CENTOS 6.4. Is there a way to have both OS's access this HDD?


Thank YOU

---

### Post by nerdtron on 2013-08-22
You are dual booting centOS and Ubuntu on a single hard drive? And then you are adding another physical drive?
I don't see any problem with that. Turn off the computer and plug in the hard drive. Boot into each OS and see if they could detect it (and it should be).
The only problem here I think is the different mount paths used by ubuntu and centos. Or if you are using LVM, that's another story.

---

### Post by coffeecat on 2013-08-22
If you create ext3/4 partitions in the new HD and entries in /etc/fstab in both OSs to mount them you will be able to access the partition(s) from both. However, there is one potential problem that may create a complication.

The UID of the first created user account in Ubuntu is 1000. Fedora, from which Red Hat and ultimately Centos is derived, used to make the UID of the first user 500, but it has been 1000 for a year or two now. As Red Hat/Centos is never based on the latest version of Fedora, it's possible that your user account in Centos has a UID of 500, in which case you will have to sort out your permissions, perhaps with a custom usergroup in both OSs. If your Centos UID is 1000, then ignore the foregoing. Quickest way to check is from the terminal in both:

```
id
```

---

