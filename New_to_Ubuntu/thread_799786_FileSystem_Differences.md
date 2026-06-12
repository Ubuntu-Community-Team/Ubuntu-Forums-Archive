---
title: "FileSystem Differences"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by takuhii on 2008-05-19
I was wondering, I use EXT3, but is there a better filesystem for Linux, and what are the differences between all the filesystems available?

Can GRUB easily convert between these filesystems without losing my data?

Is EXT4 any good??

sorry for all the n00b questions

---

### Post by Tatty on 2008-05-19
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) This might help you out :)

I wouldnt recommend ext4 if you want a stable system as it is still in development, so there are no guarantees that your data is safe.  Although its looking like it will be a good successor to ext3 when it eventually comes out.

I have not experimented with other filesystems myself, but i believe XFS is good for large files (eg mythtv recordings) and reiserfs is useful if you have lots of small files.

I dont believe you can "convert" a filesystem to another, but im no expert on filesystems so dont take my word for it.

---

