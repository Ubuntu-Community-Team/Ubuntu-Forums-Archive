---
title: "Black screen with messages ??? Dell Inspiron"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by luc_provost on 2014-01-31
Starting up pc gives folowing blackscreen:

 2.320542 Kernel panic - not syncing:VFS : unable to mount root fs on unknown-block (0,0)
 2.320636 Call Trace:
 2.320681 c15961eb   ? print+0x2d/0x2f
 2.320725 c15960b9   panic +0x5c/0x161
 2.320769 c1880b69  mount_block_root+0xb9/0x14
 2.320814  c115447c  ? sys_mknod+0x2c/0x30
 2.320857 c1880d74  mount_root+0x59/0x5f
 2.320899 c1880ec8  prepare_namespace+0x14e/0x192
 2.320942 c1145005  ? sys_access+0x25/0x30
 2.320986 c18808dd kernel_init+0x15b/0x160
 2.321029 c1880782 ? start_kernel+0x358/0x358
 2.321073 c15b393e  kernel_thread_helper+0x6/0x10

What happend?? I tried several times to restart...but every time same messages...

---

