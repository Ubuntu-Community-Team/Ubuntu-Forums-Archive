---
title: "wireless internet connection."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Staff on 2008-05-25
i have a netgear usb installed under ndiswrapper.

the command:

ndiswrapper -l

shows:

net111V2           driver installed, hardware present

I have the drivers and have blacklisted a few things.

I think the problem is connecting now that i have everything installed. I followed a tutorial for instlaling the drivers expecting to just be able to open Firefox and google (i've changed my homepage to this) would load. It didn't.
:/

what happens now?

thanks.
x

---

### Post by bsell on 2008-05-25
Try ```
sudo modprobe ndiswrapper
```

---

### Post by Staff on 2008-05-25
ok, i did.
firefox still won't load google.
i'm gonna try rebooting, but is there anything else?
and please say whether i should be able to load internet pages after doing what you say.
(: (:
thanks.
x

---

### Post by bsell on 2008-05-25
> **Staff said:**
> ok, i did.
firefox still won't load google.
i'm gonna try rebooting, but is there anything else?
and please say whether i should be able to load internet pages after doing what you say.
(: (:
thanks.
x
I can't guarantee Internet connectivity :)

I have a Netgear WG111v2 USB NIC I use on my old laptop. Ubuntu has a native driver for it. I had to use ndiswrapper with other distros, but not with Ubuntu.

---

### Post by Staff on 2008-05-25
ok, google still doesn't load.
im lost!
i dont understand, ive been trying to get it to work for ages. 
firefox says server not found.
do i need to connect to a server + how do i do that?
x

---

