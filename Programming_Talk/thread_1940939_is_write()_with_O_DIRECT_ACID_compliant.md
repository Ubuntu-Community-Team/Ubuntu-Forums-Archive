---
title: "is write() with O_DIRECT ACID compliant?"
date: 2012-03-14
forum: Programming Talk
---

### Post by nuliknol on 2012-03-14
My database engine writes records of 64 bytes by issuing write() syscall of the entire disk block. The device is opened with O_DIRECT mode. For example third record within a block starts at byte 128 and ends at position 192, when I do an UPDATE the entire disk block (which is by default 512 bytes) is written.


  My question is, can I calim ACID compliance if I am writing the record over itself every time UPDATE occurs? Usually database engines do this in 2 steps by writing modified disk block to another (free) place and then updating an index to new block with one (atomic) write immediately after first write returned success. But I am not doing this, I am overwriting current data with new one expecting the write to be successful. Does my method has any potential problems? Is it ACID compliant? What if the hardware writes only half of the block and my record is exactly in the middle? Or does the hardware already does the 2 step write process I described , but at block level, so I don't need to repeat the same in software?


  (note: no record is larger than physical disk block (512 bytes by default) and fsync goes after each write(), this is for Linux only)

---

