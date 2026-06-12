---
title: "How to rename a device?"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by lemmingrebel on 2012-07-19
I have a mounted hard drive that has a ridiculously complex name (not sure where the name came from).

I'd like to rename it, preferably through the GUI, but I'd settle for Terminal commands.

---

### Post by NikTh on 2012-07-19
Hi,
you can set a Label from within Gparted . 

Install (if you don't have it) , open gparted and right click on device > change label.
Thanks

---

### Post by lemmingrebel on 2012-07-19
> **NikTh said:**
> Hi,
you can set a Label from within Gparted . 

Install (if you don't have it) , open gparted and right click on device > change label.
Thanks

I don't see "Change Label" under the "Device" tab ...

---

### Post by Rsjc741 on 2012-07-19
Go into Disk Utility from Applications -> Accessories -> Disk Utility

From there, select your drive volume (left hand side) and select the option "Edit Parition".

Don't mess with any boot flags or file system indicators, just input the name you want into the text box and press accept.

This should prevent you from installing other software (that does the same thing)

Gparted however, is a great HDD recovery tool when it's booted into.

---

### Post by NikTh on 2012-07-19
> **lemmingrebel said:**
> I don't see "Change Label" under the "Device" tab ...

Check out "partition" tab. You will see Label .

---

