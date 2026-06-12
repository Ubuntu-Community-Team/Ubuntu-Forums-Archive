---
title: "Get devtype of paritition with dbus and udisks2"
date: 2017-04-28
forum: Programming Talk
---

### Post by pinkmanjessie on 2017-04-28
Hi,
I need to get (list) only the partitions that would usually show up in the left side panel of a file manager.
However my request to dbus retrieves many other objects. For example out of these 4 items:
/dev/sda
/dev/sda1
/dev/sda2
/dev/ram0
only "/dev/sda1" and "/dev/sda2" are what I need.

To filter the items I need to check the DEVTYPE=partition and skip the ones with DEVTYPE=disk.
I figured it out with the "udevadm" utility (see [2]) and looking at the output for /dev/sda vs /dev/sda1, but it seems one can't get the DEVTYPE with dbus/udisks2 - is it true?

I'm using Qt5, C++, udisks2, dbus.

[1]
[https://udisks.freedesktop.org/docs/latest/gdbus-org.freedesktop.UDisks2.Block.html#gdbus-property-org-freedesktop-UDisks2-Block.Configuration](https://udisks.freedesktop.org/docs/latest/gdbus-org.freedesktop.UDisks2.Block.html#gdbus-property-org-freedesktop-UDisks2-Block.Configuration)

[2] Example:
[FONT=monospace][COLOR=#000000]# udevadm info --query=all --name=/dev/sda
And:
[/COLOR][/FONT][COLOR=#000000][FONT=monospace]# udevadm info --query=all --name=/dev/sda1

[/FONT][/COLOR][FONT=monospace][COLOR=#000000]EDIT: worked around by deducing from the /dev/sdXYZ string and from its volume size.
[/COLOR]
[/FONT]

---

