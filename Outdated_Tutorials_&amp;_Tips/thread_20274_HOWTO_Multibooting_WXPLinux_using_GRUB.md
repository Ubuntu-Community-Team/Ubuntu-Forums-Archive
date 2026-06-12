---
title: "HOWTO: Multibooting WXP/Linux using GRUB"
date: 2005-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Pse on 2005-03-15
I've already seen the other WXP/GRUB howto here, but I got around to solve this problem in a much easier way. You should try it as well:

1) Make sure your WXP partition is bootable (check its flags using a Partition Manager).
2) Edit your menu.lst file to look like this for the WXP entry:
```

root (hd0,2)
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
Savedefault
makeactive
chainloader +1
```

Where "hd0,2" is your WXP partition. You should make sure that partition is bootable by itself by doing a "FIXBOOT" from the recovery console of WXP. DO NOT do a "FIXMBR" or you'll erase GRUB from your MBR.

Here's the deal. Apparently, WXP needs to "believe" it's on the first partition of the first disk to correctly boot using the chainloader mechanism of GRUB. The "map" command of GRUB allows you to map certain devices to others, effectively making Windows think it's on hd0,0.

If your WXP partition is on a second harddisk and the aforementioned procedure doesn't work, please try mapping your WXP partition to "hd1,0" (first partition of your second harddrive) or the drive where it's installed.

*IMPORTANT:* Note the space between (hd0,2) and (hd0,0) in both "map" lines. There's only ONE space, no more, no less.

---

