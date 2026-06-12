---
title: "Which should I install first?"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by AmandaLovatt on 2013-05-16
I just installed Ubuntu 12.04.2 64bit and ran an update. Now what's left is do some configuring and I'm good to go, but I'd like to know if the order bellow could cause some conflicts:

(All this after updating the recently installed system)

* Install Ubuntu Restricted Extras
* Install ia32-libs (required for Steam to run)
* Install the graphics driver.

Does the order matter?

---

### Post by DuckHook on 2013-05-16
The order does not matter, but I would recommend doing the video driver first, if only to save yourself some trouble if it doesn't work and you need to reinstall the OS. Video drivers are the most ornery, or have potential to be, anyways. The other stuff normally installs without issues.

---

### Post by Megaptera on 2013-05-17
> **DuckHook said:**
> The order does not matter, but I would recommend doing the video driver first, if only to save yourself some trouble if it doesn't work and you need to reinstall the OS. Video drivers are the most ornery, or have potential to be, anyways. The other stuff normally installs without issues.

Plus one to that, driver first ....

---

### Post by Bucky Ball on 2013-05-17
I'd personally go Restricted Extras first then check 'Additional Drivers' and see if there is something in there for the graphics. Enable it, probably restart and then install whatever else you need.

Please run this in a terminal:
```

sudo lshw -C Display
```

... then post the output here. That will tell us what the graphics card is and whether there are drivers already installed and will give some idea of the smooth or rough path you are about to embark on.

---

