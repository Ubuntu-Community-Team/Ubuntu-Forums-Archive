---
title: "Enlarge a partition without data loss"
date: 2024-07-27
forum: New to Ubuntu
---

### Post by we-hintze on 2024-07-27
Is it possible to enlarge a partition without loosing the data on it? Searching the web I found nothing helpful. But I'm a novice, so it may be I didn’t understand well.

(I want to replace the SSD in my computer with a larger one. So I cloned the SSD with clonezilla, but now the news SSD with 4 TB has just a pasrtition with 250 GB...)

---

### Post by tea for one on 2024-07-27
> **we-hintze said:**
> Is it possible to enlarge a partition without loosing the data on it? Searching the web I found nothing helpful. But I'm a novice, so it may be I didn’t understand well.
Yes, it is possible to enlarge a partition without losing data.
Gparted (among others) will do this.
But, you should only attempt this if you have a restorable _backup_ of the data.

---

### Post by oldfred on 2024-07-27
Better to see some details.
sudo parted -l
lsblk -f

New drive must be gpt partitioned, if old drive was MBR, that could be an issue.

---

### Post by we-hintze on 2024-07-27
Thank you for the quick answers!

I don&#8217;t know if it is MBR. It is possible. How can I find this out? The problem is: I enlarged the partition already once ans lost all the data. I could restore them eaysily but don&#8217;t want to repeat this too often... ;)

---

### Post by we-hintze on 2024-07-27
Aha. On my Mac (with extFS) it shows »Partitionstabelle: GUID«. Does this say something? If this is wrong I can reformat the disc and restore the data. In this case: What is the right option?

---

### Post by we-hintze on 2024-07-27
Thanks again to both of you. The problem has been solved. I don't know exactly why or how, but the SSD is now correctly partitioned without any loss of data. (Some problems just go away when you talk to someone about them...)

---

