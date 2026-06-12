---
title: "question about Partimage"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by aam-aadmi on 2008-07-01
Hi all,

I have a question about using partimage to save my current partition as an image and then later restoring the partition from the saved image.

The size of my current partition is 20GB; so the image file of my partition will be 20GB. Later, I plan to restore this partition on another computer. The partition to which I plan to copy this image file is 40 GB. 

My question is this: when I copy the image file (size 20GB) to the new partition (size 40 GB), will I lose the extra 20GB in my new partition?

I ask this question because I read the following in the webpage for partimage: "The partition to restore must have the same size as the saved partition. If the partition is smaller than the original one, the operation will fail. If it is bigger, space can be lost."

[http://www.partimage.org/Partimage-manual_Usage#How_to_restore_a_partition_from_an_image_file](http://www.partimage.org/Partimage-manual_Usage#How_to_restore_a_partition_from_an_image_file)

Aam-aadmi

---

### Post by drs305 on 2008-07-01
I use partimage regularly but have not tried putting an image on a larger partition. First, if you use partimage on a 20GB partition, there is a good chance the image will be much less than 20GB. Partimage won't copy empty areas. 

To the point of your question. If you restore the partition image to a larger partition, it very well could reduce the size of the new partition. At that point, however, you could use gparted to expand that partition into any empty space remaining to restore it to its original size.

---

### Post by kuja on 2008-07-01
With regards to it losing space, if it's a typical linux partition (ext3, xfs, &c) you can "grow" the filesystem to fit the partition afterwards.

---

