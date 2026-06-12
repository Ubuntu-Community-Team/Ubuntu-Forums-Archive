---
title: "find file offset using data block number"
date: 2009-05-09
forum: Programming Talk
---

### Post by veda87 on 2009-05-09
i am working on ext2 file system.... the data blocks that are allocated for a file are present in respective offsets.... 
knowing the file offset, we can find the data block present in the offset....
likewise, given the file and the data block number, can we find the offset of the data block within the file...

for example, for a file

 ```
            offset      datablock number
               0              1571
               1              1572
               2              1573
               .                .
               .                .
```

given, the data block number say 1573 and the file, i should get the offset as 2....

can anyone tell me a function that performs this operation.....

---

