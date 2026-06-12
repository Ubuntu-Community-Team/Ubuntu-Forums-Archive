---
title: "ext4 as a database?"
date: 2011-09-04
forum: Programming Talk
---

### Post by Lars Pensjö on 2011-09-04
Background:

[LIST=1]
[*]Application with several millions of objects.
[*]Objects vary in size from 300 bytes to 32000 bytes.
[*]Every object is identified by a unique 24 byte key.
[*]There is only one application, but many threads that access the data.
[*]Approximately 100 read operations for every write.
[/LIST]

Any suggestions on how to best manage this data? Currently, it is all saved as individual files in one single directory, with the file name as a representation of the key. But I don't know how well ext4 scales with the number of files.

An obvious answer might be MySQL. I would guess it is slower than ext4 for a "small" umber of objects.

I suppose ext4 has 4kB blocks, which means there is a waste. If this waste is only in space, not in time, then the trade-off is acceptable.

---

