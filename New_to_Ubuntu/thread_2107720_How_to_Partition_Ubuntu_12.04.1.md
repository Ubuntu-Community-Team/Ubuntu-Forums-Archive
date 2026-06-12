---
title: "How to Partition Ubuntu 12.04.1"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by coolecho on 2013-01-22
Hello,

How do I configure partitions 12.04.1 with the manual tool during install? I have a 1TB drive. I had Ubuntu 12.10 but have to wipe and reinstall 12.04.1. 

In 12.10 I had partitions:
ext4    /boot    500MB
ext4    /          15000MB
ext4    /home    50000MB
swap              4000MB

Thanks

---

### Post by audiomick on 2013-01-22
That should work fine. I don't think you need an extra /boot partition, though. I don't have one on any of my installs. If you don't make an extra partition, that will be on the / partition.

How much RAM do you have? The relevance is that the hibernate function needs swap = RAM in GiB to function properly. I generally make the swap a little larger than my RAM, as I don't have any problems with drive space. If you know you don't need hibernate to work, you could probably shrink the swap down to a GB or so without any problems, if you really need the couple of GB for storage space.

---

### Post by coolecho on 2013-01-22
OK so leave /boot out then?
I have 8GB of RAM. What do you mean "swap = RAM in GiB"?
In my case I think I'd need swap 8000MB which is 8GB?

Thanks!

---

### Post by audiomick on 2013-01-22
EDIT: somehow, I managed a double post. The contents that were here are in the next post, plus the links I was looking for.

---

### Post by audiomick on 2013-01-22
GiB
[http://en.wikipedia.org/wiki/GiB]("http://en.wikipedia.org/wiki/GiB")

It is almost the same as GB, but not quite.

Yes, if you want to be able to hibernate, then you should make your swap
8000MB = 8GB. As I said, I make mine a little larger. For 8GB, I would probably make 8.2GB swap or so. But as I said, I have more drive space than I need.

If you know you don't need to hibernate, you can definitely make your swap smaller. With 8GB of RAM, 1GB of swap is almost certainly more than enough for everything other than hibernation. Only if you do a lot of really intensive Video editing or something else like that which uses a lot of RAM would you need much swap.

It is up to you, really. As much as anything, it is a matter of how you want to use your available drive space. If you have plenty of drive space, you can happily make your swap large. If your drive space is at a premium, you might think twice about using 7GB for swap that you may never use.

Here is some stuff to look at
[https://help.ubuntu.com/community/PartitioningSchemes]("https://help.ubuntu.com/community/PartitioningSchemes")

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

