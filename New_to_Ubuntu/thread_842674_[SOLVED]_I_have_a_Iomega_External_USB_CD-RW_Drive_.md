---
title: "[SOLVED] I have a Iomega External USB CD-RW Drive that I'm trying to get to work."
date: 2008-06-27
forum: New to Ubuntu
---

### Post by whoscheesemine on 2008-06-27
Does anyone have any tips on how to get this Iomega External USB CD-RW Driver to work for me? I've googled around, and all I've found is other people trying to get theirs to work, and I also found this page about a developmental driver or something, but there wasn't a download link for it. Any help would be appreciated greatly.

EDIT - Well, if anyone else has this same problem, just go to the synaptic package manager, type in the word 'USB' and download the 2 or 3 different packages that have that in the beginning of their names, restart, and it will magically work.

---

### Post by steve_q on 2008-12-01
Wish you would've provided the individual package names for those of us who're bothered by clutter.

Glad you solved this, however.  :)

Found this post while looking for a means to allow Ibex to talk (willingly) to my Iomega USB portable HD...  trying it now...

// edit1
When I left the device attached during boot, my system would hang prior to installing these 2 packages:
- usbview
- usbmount

After I installed them it would not, however, recognize that there was a USB storage device attached when I went hunting for a device to mount..

After I read the description for usbmount, which says:
[quote=usbmount desc.]USBmount is intended as a lightweight solution which is independent of
a desktop environment. Users which would like an icon to appear when an
USB device is plugged in should use the **pmount** and **hal** packages
instead.[/quote]
I decided I'd try pmount, as hal is updated and already installed.

Still no mounting goin' on, but it now recognizes that a USB storage device is present.

... the saga continues ....

---

