---
title: "NTFS external drives copying delayed"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by Pas_sa on 2014-07-11
When I copy paste to my 32GB NTFS formatted USB key, it copies really fast (60mbps). But the USB hasn't done anything yet. It copies "for real" slowly in the background, the 60mbps was just copying from one spot on my SSD to another.

I can't take out the USB or even request it to be unmounted until the light on it stops flashing (and I know it's actually finished copying).

What setting for ntfs-3g do I need to change for this to fix? It seems to happen when I'm copying from an internal NTFS partition on the SSD.

---

### Post by TheFu on 2014-07-11
file systems use buffers to get a command to complete for the UI ASAP.  Buffers are system-wide and use excess RAM.  Use the **free -m** command to see them in action.  This is usually the desired behavior.

Actually, the 60Mbps copy was loading buffers, not copying somewhere else, until the buffers are filled. IME, the writes begin on the target FS very quickly.  Which options are being used for the mount?  delay_mtime may help.  In theory, files are written in 4K chunks according to the manpage.

You can unplug the USB drive if you like, but file system corruption should be expected.
[http://www.tuxera.com/support/](http://www.tuxera.com/support/) is listed as the support team location.

---

### Post by oldfred on 2014-07-11
The NTFS driver will always be slower than any native Linux format. 

If you have to have the flash drive compatibile with other Windows systems, some flash drives are faster than others. But again format used may change results.

       pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

