---
title: "Cloning HDD to SSD for use in laptop with different Firmware?"
date: 2020-06-21
forum: New to Ubuntu
---

### Post by aia12 on 2020-06-21
Hi all, 

I have an old lenovo Laptop running linux and BIOS and 500gb HDD, and a more modern HP laptop using windows and UEF with 1TB HDD. I. I am attempting to clone my linux HDD to a new SSD, and then replace the windows HDD in the more modern laptop with the SSD.

i cloned the HDD via partitions as the SSD is smaller than the HDD (240GB) , but now the new SSD does not boot on either laptop. 

Is it possible to simply replace the HDD on windows laptop with new linux SSD directly or do i need to install specific drivers first, and why is the cloned SSD refusing to boot on either laptop?  UUID is the same. 

Thank you very much for any help

---

### Post by GhX6GZMB on 2020-06-21
You've chosen the most difficult way of doing this, with limited prospect of success.

A new install with a backup of your user files is the easy and safe way to go in such a situation, believe me: been there, tried that.

---

### Post by oldfred on 2020-06-21
+1 on ml9104's suggestion.

UEFI and BIOS are not really compatible.
You may be able to change new UEFI system to work in the now 35 year old BIOS/MBR configuration. And Linux is typically pretty good about having correct drivers. But you may have to boot in recovery mode to uninstall incorrect driver's first.

Lot easier to just do a new UEFI install to HP on SSD. See link in my signature below.
Then restore your info from your standard backup. You do have backups of all your important data?
And good way to test that your backup is complete as you still have old drive to refer to.

If both systems are on same network, relatively easy to rsync data from old system to new system.

---

