---
title: "dr memory -- can't make it run"
date: 2013-07-12
forum: Programming Talk
---

### Post by allynm on 2013-07-12
Hi everyone,

I have been playing around with Valgrind, and as many of you know, it works pretty well.  Got interested in alternatives and discovered quickly Dr. Memory.  

```

mark@mark-HP-ProBook-4525s:~/asm$ drmemory.pl ./callmallock
~~Dr.M~~ WARNING: using debug Dr. Memory since release not found
~~Dr.M~~ WARNING: using debug DynamoRIO since release not found
Failed to exec /usr/local/dynamorio/bin32/drrun -debug -dr_home /usr/local/dynamorio -client /usr/local/drmemory/bin/bin32/debug/libdrmemory.so 0 -logdir `/home/mark/asm`   -logdir /home/mark/asm/dynamorio -ops -disable_traces -bb_single_restore_prefix -max_bb_instrs 256  /home/mark/asm/callmallock
```

The first line shows the call to drmemory.  As nearly as I can determine, the various libraries are called.  Nevertheless, on the fourth line you can see that it doesn't manage to call drrun.  Can anyone suggest what might be going wrong?

Thanks,
Mark Allyn

---

