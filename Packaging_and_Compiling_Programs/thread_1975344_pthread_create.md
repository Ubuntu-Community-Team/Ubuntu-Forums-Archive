---
title: "pthread_create ?"
date: 2012-05-07
forum: Packaging and Compiling Programs
---

### Post by debutant10 on 2012-05-07
Hello,

 I am trying to install scotch without using synaptic.

 At some point in the compile/link process, I get the following 
message:

```

gcc -O3 -DCOMMON_FILE_COMPRESS_GZ -DCOMMON_PTHREAD -DCOMMON_RANDOM_FIXED_SEED -DSCOTCH_RENAME -DSCOTCH_RENAME_PARSER -DSCOTCH_PTHREAD -Drestrict=__restrict -I../../include -I../libscotch acpl.c -o acpl -L../../lib -lscotch -lscotcherrexit -lz -lm -lrt ../../lib/libscotch.a(common_file_compress.o):common_file_compress.c:function _SCOTCHfileCompress: error: undefined reference to 'pthread_create' ../../lib/libscotch.a(common_file_uncompress.o):common_file_uncompress.c:function _SCOTCHfileUncompress: error: undefined reference to 'pthread_create' ../../lib/libscotch.a(common_file_uncompress.o):common_file_uncompress.c:function _SCOTCHfileUncompress: error: undefined reference to 'pthread_detach'
```could somebody tell me in which library/package I can find these references ?

Thank you.

---

### Post by MadCow108 on 2012-05-07
add -pthread after gcc

---

### Post by debutant10 on 2012-05-09
Yes !
Thanks a lot.

---

