---
title: "changing the data block number...."
date: 2009-03-06
forum: Programming Talk
---

### Post by veda87 on 2009-03-06
I am working on linux-2.6.26 on ext2 file system.... for a file, i_data (present in the inode structure) contains the pointer to the data blocks. i need to change the pointer to point an another data block...

for example, if i_data[0] is pointing to a data block (say, 4130), i need to change it to point 3267 data block...

can anyone suggest me to how to proceed with this.....

---

