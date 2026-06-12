---
title: "delete partition created after a wrong dd command"
date: 2016-10-30
forum: New to Ubuntu
---

### Post by eduario on 2016-10-30
I was trying to create a bootable usb with the dd command but I made a mistake in the target parameter and a new partition was created and I cant manage to deleted.

I try with GParted but when i right click the delete option it is graied out,

any help welcome,

thanks


[IMG]https://s11.postimg.org/vz1wxqjhv/Screenshot_from_2016_10_30_11_52_40.png[/IMG]

---

### Post by HermanAB on 2016-10-30
First of all, note that gparted in the picture is pointing to your local HDD, not the external USB device.

As for an external device, zero the first part of the device using dd, then gparted will think that it is new, eg:
dd if=/dev/zero of=/dev/sdb bs=1M count=1

After that, you can run gparted and it should work without an issue.

---

### Post by Bucky Ball on 2016-10-30
> **HermanAB said:**
> As for an external device, zero the first part of the device using dd, then gparted will think that it is new, eg:
dd if=/dev/zero of=/dev/sdb bs=1M count=1

Making absolutely positive that sdb is your USB device before going anywhere near this command, of course. Looks like things went pear-shaped once already. I'd avoid dd in future and use something safer. They don't call dd 'data destroyer' for nothing. :| Be careful, please. :)

---

