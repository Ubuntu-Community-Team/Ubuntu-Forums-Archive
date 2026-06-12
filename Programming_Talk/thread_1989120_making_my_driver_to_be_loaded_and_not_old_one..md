---
title: "making my driver to be loaded and not old one."
date: 2012-05-28
forum: Programming Talk
---

### Post by RichardUK on 2012-05-28
Hi, bit of a noob question I think.

I have a USB serial device that out of the box loads as a ACM device. But this is wrong as the manufacturer was a little naughty and did not change the USB chips ID from the devkit they used. And so the wrong driver is now loaded. It is an old chip that is not a full serial device. So using UDEV to load in the serial driver did not work. I have written my own serial driver that handles the missing functionality.

Now here is my noob question.

Is it possible without having to add udev rules to get my driver used instead of the ACM one?  Been goggling but just getting lost in the wave of info.

Many thanks. :)

---

### Post by Bachstelze on 2012-05-28
Have you tried blacklisting the wrong one?

---

### Post by RichardUK on 2012-05-29
No not tried black listing yet, did cross my mind but was not sure about it. Would you expect this would be the norm when you are 'replacing' a driver?

---

### Post by roelforg on 2012-05-30
> **RichardUK said:**
> No not tried black listing yet, did cross my mind but was not sure about it. Would you expect this would be the norm when you are 'replacing' a driver?
It's the norm, blacklisting prevents that driver from being loaded.

---

