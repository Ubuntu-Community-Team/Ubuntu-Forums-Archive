---
title: "HOWTO: Kubuntu automount problem (workaround)"
date: 2005-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-11-16
If your problem is the following [http://bugzilla.ubuntu.com/show_bug.cgi?id=18211]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18211")
you might want to try this workaround (until the bug is fixed)

Right click on a free space of the desktop and select

Create new/Link to device/DVD-Rom Device (or Harddisk device, etc.)

write the name of the link in the "General" page (e.g. "pioneer" or "burner", etc.)

click on the Device section:
you will see a text field. Click on the arrow located at its right and select the name of the peripheral according to how it is named in your /etc/fstab (e.g. "/dev/hdc")

Then click ok

Double click on your new link on the desktop

Et voila, your peripheral will mount.

---

