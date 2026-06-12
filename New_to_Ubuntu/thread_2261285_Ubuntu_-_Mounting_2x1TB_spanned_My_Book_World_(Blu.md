---
title: "Ubuntu - Mounting 2x1TB spanned My Book World (Blue Rings) Hard disks for Access"
date: 2015-01-17
forum: New to Ubuntu
---

### Post by Dominic_Fernandes on 2015-01-17
I am new to Ubuntu. My WD My Book World (Blue Rings) - network access - enclosure is not detecting on the network. The hard disks were in span data mode. I connected them to my Ubuntu machine but am not able to see them. Can I get some directions on how to take off the data from the hard disks.

---

### Post by oldfred on 2015-01-17
Span data mode, sound like something proprietary. 
What does WD say it is?

If a standard RAID, you may just need to add RAID drivers.

Perhaps someone that has a WD will reply, but if proprietary then there may not be anyone who knows?

---

### Post by DuckHook on 2015-01-17
WD uses either an outright proprietary partition/file system or a very obscure one for all of their MyBook-type NAS products. They are not the only ones who do so. HP did the same and a few others, but knowing this is common industry practice doesn't help you. You are not the first person who has tried to salvage data from a failed proprietary NAS. I think you would be better off contacting WD and asking them what steps they recommend. They may have techs with the right combo of HW/SW who can help you recover the data. Barring that, I don't know how to help. There are forensics-type labs who can recover just about any magnetic-based info, but they charge an arm and a leg.

Did you make backups of the data or was the NAS the one and only copy?

For what it's worth, please see [this]("http://ubuntuforums.org/showthread.php?t=2260282&p=13208430#post13208430") recent thread for similar issue and comments.

---

