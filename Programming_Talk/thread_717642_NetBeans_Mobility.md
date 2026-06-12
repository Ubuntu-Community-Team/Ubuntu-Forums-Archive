---
title: "NetBeans Mobility"
date: 2008-03-07
forum: Programming Talk
---

### Post by nimeshchandran on 2008-03-07
hello guys i installed jdk 1.6, netbeans 6.0.... i tried running a small j2me program...its is building fine but when i try to run i get the following errors...

```
Starting emulator in execution mode
java.io.IOException: java.io.IOException: No such file or directory
   at java.lang.PosixProcess.<init>(libgcj.so.81)
   at java.lang.Runtime.execInternal(libgcj.so.81)
   at java.lang.Runtime.exec(libgcj.so.81)
   at java.lang.Runtime.exec(libgcj.so.81)
   at com.sun.kvem.environment.JVM.run(Unknown Source)
   at com.sun.kvem.environment.EmulatorInvoker.runEmulatorOtherVM(Unknown Source)
   at com.sun.kvem.environment.EmulatorInvoker.runEmulator(Unknown Source)
   at com.sun.kvem.environment.ProfileEnvironment$KVMThread.runEmulator(Unknown Source)
   at com.sun.kvem.environment.ProfileEnvironment$KVMThread.run(Unknown Source)
Caused by: java.io.IOException: No such file or directory
   at java.lang.PosixProcess.nativeSpawn(libgcj.so.81)
   at java.lang.PosixProcess.spawn(libgcj.so.81)
   at java.lang.PosixProcess$ProcessManager.run(libgcj.so.81)
```

what to do.... help guys...

---

### Post by Zugzwang on 2008-03-07
Since there appears a "libgcj" in the error message which does not belong to Sun's Java environment, please make sure that when running the program, it's not the GNU Java stuff that tries to execute your program. Try:
```

sudo update-java-alternatives

```
Also try to execute your program from the command line directly to check whether the problem exists there as well.

---

### Post by nimeshchandran on 2008-03-07
hmmm i tried something else and it worked...i downloaded the wireless toolkit and installed it... i changed the default j2me platform in the netbeans to the newly installed one and now it works just fine....

---

