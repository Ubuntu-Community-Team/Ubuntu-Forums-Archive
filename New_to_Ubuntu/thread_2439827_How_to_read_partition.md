---
title: "How to read partition ?"
date: 2020-04-02
forum: New to Ubuntu
---

### Post by sanko50 on 2020-04-02
[COLOR=#000000][FONT=Verdana]What does /dev/xvda1 mean ?
[/FONT][/COLOR]OS : [COLOR=#000000]AWS EC2 Amazon Linux 2[/COLOR]

[COLOR=#000000][FONT=Verdana]Can I say it is a partition 1 in xvda disk in the device ?[/FONT][/COLOR]

---

### Post by QIII on 2020-04-02
I believe that nomenclature to be particular to Xen hypervisors and it represents the first partition of a Xen virtual block device.

Is this on a cloud such as AWS or the like?

---

### Post by sanko50 on 2020-04-02
yes. this is in AWS EC2 Amazon Linux 2
Can you please  reply to the original post ?

---

### Post by CelticWarrior on 2020-04-02
> **sanko50 said:**
> Can you please  reply to the original post ?

I believe he already did. Maybe you should ask for additional information directly to the service provider instead in a dedicated Ubuntu forum?

---

### Post by sanko50 on 2020-04-02
> **CelticWarrior said:**
> I believe he already did. Maybe you should ask for additional information directly to the service provider instead in a dedicated Ubuntu forum?

I could not understand it.


that [COLOR=#000000]Xen hypervisors  are hard to understand. He asked  a query , whether it is AWS or not. ..Is the answer still is a "YES"  ?
[/COLOR]

---

### Post by TheFu on 2020-04-02
> **sanko50 said:**
> I could not understand it.


that Xen hypervisors  are hard to understand. He asked  a query , whether it is AWS or not. ..Is the answer still is a "YES"  ?

Seems like the answer was as clear and complete as possible.  Use google to look up any terms you don't understand like "xen  hypervisor" and read until it makes sufficient sense.   Honestly, that part really isn't too important.  There are multiple different hypervisors commonly in use on VPS providers today.  Depending on the virtual disk controller used by each hypervisor, the virtual disk device names can change slightly.

The original question used an ambiguous term "read" - that could be *read by a human* or *read by assorted programs*.  it could mean "understand" or "parse" too.  English isn't always exact.

Google found this: [https://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme](https://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme)
but I’m not certain it provides information  you seek.   xvda is just a specific storage type.  vda is commonly seen for KVM hypervisors.

---

### Post by sanko50 on 2020-04-02
> **TheFu said:**
> Seems like the answer was as clear and complete as possible.  Use google to look up any terms you don't understand like "xen  hypervisor" and read until it makes sufficient sense.   Honestly, that part really isn't too important.  There are multiple different hypervisors commonly in use on VPS providers today.  Depending on the virtual disk controller used by each hypervisor, the virtual disk device names can change slightly.

The original question used an ambiguous term "read" - that could be *read by a human* or *read by assorted programs*.  it could mean "understand" or "parse" too.  English isn't always exact.

Google found this: [https://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme](https://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme)
but I&#8217;m not certain it provides information  you seek.   xvda is just a specific storage type.  vda is commonly seen for KVM hypervisors.

Thanks for the post.

You are confusing me with arguments.

Simple Question is :

[COLOR=#000000][FONT=Verdana] /dev/xvda1  = > [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Can I refer it as a partition 1 in xvda disk in the device ( OS is AWS Amazon Linux 2) ....  YES/NO ?

question is about nomenclature and convention.

Period.

Anyway, forget it. There is no clear answer here, I'll check it out.[/FONT][/COLOR]

---

### Post by QIII on 2020-04-02
I gave you a clear answer:

I believe that nomenclature to be particular to Xen hypervisors and it represents the first partition of a Xen virtual block device.  If you did not understand the answer, it would have been quite simple to say that.  I'd have been happy to explain further.

The query was a a fact-finding, open-ended question that might have led to more detailed discussion that might be helpful to you.

---

### Post by TheFu on 2020-04-03
[https://askubuntu.com/questions/166083/what-is-the-dev-xvda1-device](https://askubuntu.com/questions/166083/what-is-the-dev-xvda1-device) (from 7 yrs ago) says that it is a storage device for a really old version of Xen. Amazon switched to using KVM many years ago, which would use different device names, typically vda or sda.

xvda1 could be called the first partition of xvda and that is probably the most likely answer, but without seeing the disk partition layout, nobody can really say, since "first" could mean "first created" even if it is located on the end of the disk device ... in the last position. Partition numbers are based on creation order, not placement on the storage devices.

**sudo parted -lm**  would be helpful to see the layout and other devices.
**more /etc/os-release** would be helpful too - the "pretty name"

There aren't always answers that are perfectly clear in the world.

---

### Post by sanko50 on 2020-04-04
> **TheFu said:**
> [https://askubuntu.com/questions/166083/what-is-the-dev-xvda1-device](https://askubuntu.com/questions/166083/what-is-the-dev-xvda1-device) (from 7 yrs ago) says that it is a storage device for a really old version of Xen. Amazon switched to using KVM many years ago, which would use different device names, typically vda or sda.

xvda1 could be called the first partition of xvda and that is probably the most likely answer, but without seeing the disk partition layout, nobody can really say, since "first" could mean "first created" even if it is located on the end of the disk device ... in the last position. Partition numbers are based on creation order, not placement on the storage devices.

**sudo parted -lm**  would be helpful to see the layout and other devices.
**more /etc/os-release** would be helpful too - the "pretty name"

There aren't always answers that are perfectly clear in the world.

Thanks a lot. that cleared a lot of doubt.  

Thanks again for your time.

---

