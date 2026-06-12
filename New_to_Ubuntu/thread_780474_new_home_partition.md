---
title: "new /home partition"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by skyjacker on 2008-05-03
I have re-partitioned my hd so that I can have a separate /home.
Here are my old partitions 
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         490        4137    29302560    7  HPFS/NTFS
/dev/hda2               1         489     3927861    b  W95 FAT32
/dev/hda3            4138        9565    43600410   83  Linux
/dev/hda4            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap /, 

and here are my new ones,
 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         490        4137    29302560    7  HPFS/NTFS
/dev/hda2               1         489     3927861    b  W95 FAT32
/dev/hda3            4138        6814    21503002+  83  Linux
/dev/hda4            6892        9729    22796235    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris
/dev/hda6            6892        9565    21478842   83  Linux

I want my /home on hda6 but have not been able to get it there. So far all that is on it is Lost/Found. Can someone please help?? 

I'm pretty sure this will involve the Terminal, and I am not to familar with the terms, so I need it as simple as possible.

---

### Post by jken146 on 2008-05-03
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) should help.

---

### Post by skyjacker on 2008-05-03
> **jken146 said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) should help. I followed this procedure and when I got to this section
sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new
I recieved an error message that "new" already existed. The rest of it apparantly did not work... HELP please!!!

---

