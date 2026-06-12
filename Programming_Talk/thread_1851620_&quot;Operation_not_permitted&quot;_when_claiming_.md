---
title: "&quot;Operation not permitted&quot; when claiming USB interface"
date: 2011-09-28
forum: Programming Talk
---

### Post by bcrowell on 2011-09-28
This may be more of a linux question than a programming question. I have an open-source project [https://github.com/bcrowell/freelab](https://github.com/bcrowell/freelab) that interfaces to some hardware used in school lab courses through USB. About 6 months ago I got it working on a bunch of machines in my classroom that are running lucid. Recently I replaced several of those machines with new ones, again installing lucid. Now when I try to run my program on the new machines as a normal user, it fails to claim the USB interface:

```
/usr/lib/ruby/1.8/usb.rb:401:in `usb_claim_interface': Operation not permitted - usb_claim_interface (Errno::EPERM) from /usr/lib/ruby/1.8/usb.rb:401:in `claim_interface' from ./vernier.rb:246:in `initialize' from -e:1:in `new' from -e:1
```

I don't get the error when I run the program as root, but I do get it if I run as a user with admin privileges.

This is an error from a ruby USB library, and you can see my code at the github link above. However, I don't think the problem is really specific to ruby or to my code. I think what is probably happening is that some recent change to lucid must have tightened up the permissions for accessing USB devices. Probably if I do an apt update on the older machines, the software will break on them as well. I think I just need to figure out how to grant these permissions, but so far I haven't been able to figure out how to do that.

Can I do it by just adding the user accounts to a certain group in /etc/group?

Googling led me to think that maybe this has something to do with udev, which I know nothing about. I tried making a file called

```
/etc/udev/rules.d/vernier.rules
```

with the following contents

```
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="08f7", SYSFS{idProduct}=="0001", MODE="0666"
```

and then doing

```
udevadm control --reload-rules
```

as root. This didn't help.

Thanks in advance for any suggestions.

---

### Post by slavik on 2011-09-29
user with admin priv != root

user with administrative privileges is allowed to have things run for them as root. it is not the same as being root. and the error means exactly that, you are not root. :)

---

### Post by bcrowell on 2011-09-29
Hi, Slavik,

Thanks for your reply. Yes, I already understood that an admin user was not the same as a root user. However, this works on older versions of lucid for *any* user, including an ordinary user who is not root and not an admin. I just need to figure out how to make it work on the newly updated version of ubuntu. I.e., I need to figure out how to grant the privileges that now seem not to be granted by default.

-Ben

---

### Post by bcrowell on 2011-09-30
Bump.

---

