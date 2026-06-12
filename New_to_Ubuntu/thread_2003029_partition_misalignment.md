---
title: "partition misalignment"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by nerdinator on 2012-06-13
I have a new Dell XPS laptop which had Windows 7 installed in it. 
It also had a default extra partition for "Dell Utility".
I installed Ubuntu in it on an Extended Partition along with windows and specified the logical partitions myself (for /,/home and swap).
Now when I open Disk Utility , it shows this "Partition misaligned by 512 bytes" error for the Dell Utility partition and "Partition misaligned by 1024 bytes" for the entire Extended partition where Ubuntu is installed.
Deleting the extended partition and re-installing Ubuntu may solve the problem of misalignment in the extended partition. 
But how about the Dell Utility partition?

If I re-install Windows 7 Dell Utility wouldn't be a part of the re-install. So that may not solve it either.
How do I fix this?

Note: The extended partition I made contains an NTFS logical partition for holding data accessible by both OSes(basically a personal data partition).

Thank you

---

### Post by nerdinator on 2012-06-16
Sorry to bring this up again,
but now I deleted all my Ubuntu partitions and recreated them using GParted via the LiveCD.
I re-installed Ubuntu.
The issue of 1024 byte misalignment with the **whole extended partition** is solved.

**But**,the misalignment with the Dell Utility partition is still there.

---

### Post by nerdinator on 2012-06-16
**To sum up**, I have a laptop with Windows 7 and Ubuntu installed.
When I open Disk Utility in Ubuntu, I find that there is a **partition misalignment of 512 bytes with the Dell Utility partition**.
How do I fix it?
The warning message says that there could be poor performance due to this.
Is it true?

---

