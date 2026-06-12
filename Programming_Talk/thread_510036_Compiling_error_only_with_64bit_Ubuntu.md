---
title: "Compiling error only with 64bit Ubuntu"
date: 2007-07-26
forum: Programming Talk
---

### Post by hiruzzolo on 2007-07-26
Hi.. I was trying to compile Avetana for linux, a third-part software that implements the java api for bluetooth in linux with bluez. I have this problem compiling it in 64bit ubuntu.. In this file, it gives me an error:
```
g++ -shared -lbluetooth -I /usr/lib/jvm/java-6-sun-1.6.0.00/include -I /usr/lib/jvm/java-6-sun-1.6.0.00/include/linux BlueZ.cpp -o /home/roby/pippo/libavetanaBT.so 
BlueZ.cpp: In function ‘jint Java_de_avetana_bluetooth_stack_BlueZ_createService(JNIEnv*, _jclass*, _jobject*)’:
BlueZ.cpp:1412: error: cast from ‘ServiceHandle*’ to ‘jint’ loses precision
make[1]: *** [libavetanaBT.so] Error 1
make[1]: Leaving directory `/home/roby/avetana/c'
make: *** [csource] Error 2

```
and in that line the code is like this:
```
return (jint)srh;
```

The funny thing is that in ubuntu 6.10 i386 it doesn't have this problem, because I have tested it on my old pc.. Why does it have a compiling error only with 64bit? How can I do to solve it? I would prefer to use my new pc and to not downgrade it to i386

---

### Post by hod139 on 2007-07-26
What is srh?  Is it a long or a double?

---

### Post by hiruzzolo on 2007-07-26
ServiceHandle *srh = (ServiceHandle *)malloc (sizeof (ServiceHandle)); -> this is the declaration of srh

---

### Post by hod139 on 2007-07-26
I'm slightly confused why you would be casting a ServiceHandle pointer to an int, but that is your problem.  In a 64 bit machine, pointers are 64 bits, but ints are still 32.  On a 32 bit machine, pointers are 32 bits and ints are 32 bits.

---

### Post by hiruzzolo on 2007-07-27
It's not code written by me, that's the problem.. Anyway, I'll write to them about this!

---

