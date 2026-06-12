---
title: "How to suppress terminated message when killall is used to kill several processes"
date: 2015-09-30
forum: Programming Talk
---

### Post by newcfd on 2015-09-30
There are following error messages when killall is used to kill several processes

  exit status of rank 8: killed by signal 9 
forrtl: error (78): process killed (SIGTERM)
Image              PC                Routine            Line        Source             
libpthread.so.0    00007F7478FE8340  Unknown               Unknown  Unknown
libc.so.6          00007F72B9D5F3F7  Unknown               Unknown  Unknown


How to suppress them?  I tried -q and it does not work.

---

### Post by tgalati4 on 2015-10-01
```
sudo killall processname > /dev/null
```

If you are trying to kill system processes, then you may get errors from other libraries that are not happy about that.  What process are you trying to kill?

Why do you need to use *killall*?

---

