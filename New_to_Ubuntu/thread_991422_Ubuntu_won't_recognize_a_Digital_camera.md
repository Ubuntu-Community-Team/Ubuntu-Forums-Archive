---
title: "Ubuntu won't recognize a Digital camera"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by nu2this2 on 2008-11-23
I have an older model Olympus digital camera that uses the old fashioned connector that goes to a serial port on my Dell laptop. When I try to dl photos, nothing happens. It is as though the camera is not connected to the PC.

I have a newer Olympus DSLR that uses a usb port and I have no problems with that. Is there any way to get Ubuntu to "see" my other camera?

Thanks for any help :):)

---

### Post by ibuclaw on 2008-11-23
You may require setserial installed to configure it.


Although, first, try this out. (Best way I can think of checking to see if it has detected it).

Open a term and type in:
```
dmesg | grep tty
```
Then insert your serial cable connected to the camera and try the dmesg command again to see if there are any changes to the output.

Regards
Iain

---

### Post by nu2this2 on 2008-11-24
Thank you,

I'll give it a try.

---

### Post by philinux on 2008-11-24
> **nu2this2 said:**
> I have an older model Olympus digital camera that uses the old fashioned connector that goes to a serial port on my Dell laptop. When I try to dl photos, nothing happens. It is as though the camera is not connected to the PC.

I have a newer Olympus DSLR that uses a usb port and I have no problems with that. Is there any way to get Ubuntu to "see" my other camera?

Thanks for any help :):)

If all else fails you can get a serial to usb adapter.

---

