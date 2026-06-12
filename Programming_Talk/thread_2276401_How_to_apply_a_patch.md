---
title: "How to apply a patch"
date: 2015-05-02
forum: Programming Talk
---

### Post by shahin on 2015-05-02
Hi 
I ran into an issue when I tried to compile an instance of the Linux kernel. I actually tried to do cross compilation. The errors I saw were: 

```
sansari@ubuntu:~/WORKING_DIRECTORY$ make modules
scripts/kconfig/conf --silentoldconfig Kconfig
sound/soc/codecs/audience/Kconfig:40:warning: type of 'SND_SOC_ES_SLIM' redefined from 'boolean' to 'tristate'
sound/soc/codecs/audience/Kconfig:43:warning: type of 'SND_SOC_ES_I2C' redefined from 'boolean' to 'tristate'
sound/soc/codecs/audience/Kconfig:44:warning: choice value used outside its choice group
sound/soc/codecs/audience/Kconfig:41:warning: choice value used outside its choice group
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: `include/generated/mach-types.h' is up to date.
  CC      arch/arm/kernel/asm-offsets.s
  GEN     include/generated/asm-offsets.h
  CALL    scripts/checksyscalls.sh
  CC [M]  drivers/scsi/scsi_wait_scan.o
  Building modules, stage 2.
  MODPOST 1 modules
ERROR: "__aeabi_unwind_cpp_pr0" [drivers/scsi/scsi_wait_scan.ko] undefined!
ERROR: "__aeabi_unwind_cpp_pr1" [drivers/scsi/scsi_wait_scan.ko] undefined!
ERROR: "scsi_complete_async_scans" [drivers/scsi/scsi_wait_scan.ko] undefined!
ERROR: "wait_for_device_probe" [drivers/scsi/scsi_wait_scan.ko] undefined!
make[1]: *** [__modpost] Error 1
make: *** [modules] Error 2
```


I found the following fix: 

```
---
diff --git a/drivers/scsi/Kconfig b/drivers/scsi/Kconfig
diff --git a/drivers/scsi/scsi_scan.c b/drivers/scsi/scsi_scan.c
index 0949145..a67f315 100644
--- a/drivers/scsi/scsi_scan.c
+++ b/drivers/scsi/scsi_scan.c
@@ -181,10 +181,8 @@ int scsi_complete_async_scans(void)
        return 0;
 }

-#ifdef MODULE
 /* Only exported for the benefit of scsi_wait_scan */
 EXPORT_SYMBOL_GPL(scsi_complete_async_scans);
-#endif

 /**
  * scsi_unlock_floptical - unlock device via a special MODE SENSE command
```

But I did not know enough about patch to be able to use it. What I got out of it was that two files are to be updated; Kconfig and scsi_scan.c. Is that right? I did not understand how to apply the change suggested. I did look online and read about patch. I even posted on another site. They suggested to implement version control before applying the patch. My question is how do I apply the above change? I do realize I have a number of errors above, and I have to figure out how to address the rest of them.

---

### Post by terrypearson on 2015-05-05
This is fairly basic and you 'could' read the file and do it manually. The three minuses mean that a line is removed, the three pluses mean a line is added.

Since it looks like you are using git, here is a tutorial on git patches... 
[http://rypress.com/tutorials/git/patch-workflows](http://rypress.com/tutorials/git/patch-workflows)

---

### Post by shahin on 2015-05-05
Thank you so much. It turned out that once I cleaned my build environment, and ran make again, the error went away. I certainly appreciate the git patch tutorial. I need a refresher.

---

