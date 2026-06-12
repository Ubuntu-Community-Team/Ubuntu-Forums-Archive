---
title: "Question about nvidia drivers"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-04-27
If you enable nvidia drivers through the hard ware manager does that go and get the actual nvidia drivers or does that just enable a generic driver? Because I was trying to play CSS through Wine and it seemed like the card wasn't performing liek it does on windows...and ive heard from people that css runs better in ubuntu than windows...so im just curious..do i need to go get the nividia drivers and install them myself or did ubuntu do it for me?

---

### Post by hackle577 on 2008-04-27
Ubuntu should do it for you using the Restricted Drivers Manager.

---

### Post by mikewhatever on 2008-04-27
> **dtrot55 said:**
> If you enable nvidia drivers through the hard ware manager does that go and get the actual nvidia drivers or does that just enable a generic driver? Because I was trying to play CSS through Wine and it seemed like the card wasn't performing liek it does on windows...and ive heard from people that css runs better in ubuntu than windows...so im just curious..do i need to go get the nividia drivers and install them myself or did ubuntu do it for me?

Ubuntu should download the driver and dependencies and set everything up.

---

### Post by kavon89 on 2008-04-27
> **hackle577 said:**
> Ubuntu should do it for you using the Restricted Drivers Manager.

Actually, some people have reported problems with 8.04 and Nvidia drivers, myself included. In the Restricted Drivers Manager, the box would be checked on but it's "Not in use" for nvidia-new.

I think some have said that installing nvidia-glx-new from the package manager fixes the issue. I went through another method to get mine working properly.


But, if you can get CSS running I bet your 3D is working fine...

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=22999](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=22999)

Check the AppDB page for CSS performance fixes in the HowTo section.

---

### Post by master5o1 on 2008-04-27
Generic for all nvidia cards for use on Linux, I believe.

---

