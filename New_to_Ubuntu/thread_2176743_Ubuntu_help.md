---
title: "Ubuntu help"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by christian3 on 2013-09-25
Hello there everyone. I have been having a lot of problems since  installing Ubuntu. I had Ubuntu as well as windows installed on my  laptop. I began having issues in windows, and so I tried to do a system  recovery, but for some reason it was unsuccesful. I was forced to make  Ubuntu my only operating system. I was wondering what I should now do  with the partitions on my hard drive. I have attached a picture of what  the partitions look like at the moment[ATTACH=CONFIG]246511[/ATTACH] Please let me know what I need to do with all of this disk space. As I said ubuntu is the only operating system I have now, so I want to set things up to use it effectively. Thanks for the help

---

### Post by UltimateCat on 2013-09-26
Before you installed Ubuntu did you shrink your Windows partition?

Looking at all of those partitions I see that you still have one of your Windows NTFS partitions which is the /dev/sda3-
I suspect that the /dev/sda1 is Windows but I don't know with certainty--
There may be a way to recover your Windows but I don't know how to sorry-

You have 3 unallocated one 412.28 Gb, a 200 megabytes and an addition unallocated 105.34 megabytes--

Not sure how that happened--

What do you want to do with all of the extra space that you have?
Do you want to install another OS?

If you wanted to you could take the unallocated space, partition it and just use it as storage.

You could click on the 200 MB and delete it and it will be added to the 412.28 GB unallocated and do the same for the 105.34-
There are a few options. If this was my partition table I would re-partition it because 11 GB is a bit much for a swap partition.
Generally folks make their swap 1 or 2 GB--

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by christian3 on 2013-09-27
If I could, I would love to have windows 7 back on this computer. If I  reload windows on here, will I be able to have all four partitions that  are associated with windows? The reason this whole fiasco went down with  the system recovery was because I could not access my BIOS settings in  windows after deleting the HP_TOOLS partition. If I reload windows, I  want to have the HP_TOOLS partitions so that I can change BIOS settings  as I have no clue how to mess with the BIOS in Ubuntu.

---

