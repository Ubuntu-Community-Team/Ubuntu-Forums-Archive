---
title: "error in eclipse"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-08-14
I am getting this error when try to run old android application which was working before,

I have a new ubuntu environment which is ubuntu 12 live

here is the error:
Failed to get the adb version: Cannot run program "/media/309AFD059AFCC87C/ubuntu live drive program files/android-sdk-linux/platform-tools/adb": java.io.IOException: error=13, Permission denied from '/media/309AFD059AFCC87C/ubuntu live drive program files/android-sdk-linux/platform-tools/adb' - exists=true


any advice...?

---

### Post by sandyd on 2012-08-15
Post output of
```

ls -l /media/309AFD059AFCC87C/ubuntu live drive program files/android-sdk-linux/platform-tools/

```
```

cd /media/309AFD059AFCC87C/ubuntu live drive program files/android-sdk-linux/platform-tools/
umask
```

---

