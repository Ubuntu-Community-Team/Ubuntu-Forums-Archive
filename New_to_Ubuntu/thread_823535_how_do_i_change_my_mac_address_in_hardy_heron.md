---
title: "how do i change my mac address in hardy heron?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by guest_user on 2008-06-09
when i do ifconfig "interface" hw ether "mac address" after ifconfig "interface" down it says invalid argument or something like that, what's wrong?

---

### Post by BlackDragonBE on 2008-06-09
Cheers

---

### Post by guest_user on 2008-06-09
pls read first post, that was what i did and it says invalid argument. i am using atheros card and the interface is wifi0. the process works for ath0 but not wifi0

---

### Post by hyper_ch on 2008-06-09
shouldn't it be 
```

hwaddress

```?

---

### Post by rampageoberon on 2008-06-09
This should be helpful

[http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html](http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html)

Edit: yes, it is hwaddress not hw

---

### Post by guest_user on 2008-06-09
so should it be ifconfig "interface" hwaddress ether "mac address" or ifconfig "interface" hwaddress "mac address" ?

thanks in advance, its strange because it always worked with hw ether...this is the first time

---

### Post by RSingh on 2008-06-09
did you try with a sudo?

---

### Post by guest_user on 2008-06-09
> **RSingh said:**
> did you try with a sudo?

the error was invalid argument not permission denied, see first post, and yes i was root when i did that

---

### Post by guest_user on 2008-06-09
ok so i tried hwaddress but it gave me unknown host error, what's wrong?

---

