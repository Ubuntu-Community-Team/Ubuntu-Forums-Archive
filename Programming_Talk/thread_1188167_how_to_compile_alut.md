---
title: "how to compile alut??"
date: 2009-06-15
forum: Programming Talk
---

### Post by abhilashm86 on 2009-06-15
i need to run an c progrm which contains alut.h, so how to compile it, when i try following, 
```

abhilash@abhilash:~/Desktop/lesson1$ gcc main.cpp -lglut alut
gcc: alut: No such file or directory
main.cpp: In function ‘ALboolean LoadALData()’:
main.cpp:73: warning: ‘alutLoadWAVFile’ is deprecated (declared at /usr/include/AL/alut.h:113)
main.cpp:73: warning: ‘alutLoadWAVFile’ is deprecated (declared at /usr/include/AL/alut.h:113)
main.cpp:75: warning: ‘alutUnloadWAV’ is deprecated (declared at /usr/include/AL/alut.h:116)
main.cpp:75: warning: ‘alutUnloadWAV’ is deprecated (declared at /usr/include/AL/alut.h:116)

```
how to compile this program??

---

### Post by Bachstelze on 2009-06-15
> **abhilashm86 said:**
> i need to run an c progrm which contains alut.h, so how to compile it, when i try following, 
```

abhilash@abhilash:~/Desktop/lesson1$ gcc main.cpp -lglut alut
gcc: alut: No such file or directory
main.cpp: In function ‘ALboolean LoadALData()’:
main.cpp:73: warning: ‘alutLoadWAVFile’ is deprecated (declared at /usr/include/AL/alut.h:113)
main.cpp:73: warning: ‘alutLoadWAVFile’ is deprecated (declared at /usr/include/AL/alut.h:113)
main.cpp:75: warning: ‘alutUnloadWAV’ is deprecated (declared at /usr/include/AL/alut.h:116)
main.cpp:75: warning: ‘alutUnloadWAV’ is deprecated (declared at /usr/include/AL/alut.h:116)

```
how to compile this program??

Those are just warnings, the program should have compiled fine. What makes you think it didn't?

Also, what is this "alut" on the command-line supped to be here for? As it is, it is ignored.

---

### Post by abhilashm86 on 2009-06-15
> **HymnToLife said:**
> Those are just warnings, the program should have compiled fine. What makes you think it didn't?

Also, what is this "alut" on the command-line supped to be here for? As it is, it is ignored.

well even i thinked like you before, but see this, i downloaded alu, thats required for handling audio devices, and also there's a inbuilt function which is not able for program to access, 
see this when i take out alu
```

abhilash@abhilash:~/Desktop/lesson1$ gcc main.cpp -lglut 
main.cpp: In function ‘ALboolean LoadALData()’:
main.cpp:73: warning: ‘alutLoadWAVFile’ is deprecated (declared at /usr/include/AL/alut.h:113)
main.cpp:73: warning: ‘alutLoadWAVFile’ is deprecated (declared at /usr/include/AL/alut.h:113)
main.cpp:75: warning: ‘alutUnloadWAV’ is deprecated (declared at /usr/include/AL/alut.h:116)
main.cpp:75: warning: ‘alutUnloadWAV’ is deprecated (declared at /usr/include/AL/alut.h:116)
/tmp/cc05VtwK.o: In function `KillALData()':
main.cpp:(.text+0x16): undefined reference to `alDeleteBuffers'
main.cpp:(.text+0x2a): undefined reference to `alDeleteSources'
main.cpp:(.text+0x2f): undefined reference to `alutExit'
/tmp/cc05VtwK.o: In function `SetListenerValues()':
main.cpp:(.text+0x4c): undefined reference to `alListenerfv'
main.cpp:(.text+0x60): undefined reference to `alListenerfv'
main.cpp:(.text+0x74): undefined reference to `alListenerfv'
/tmp/cc05VtwK.o: In function `LoadALData()':
main.cpp:(.text+0x92): undefined reference to `alGenBuffers'
main.cpp:(.text+0x97): undefined reference to `alGetError'
main.cpp:(.text+0xdb): undefined reference to `alutLoadWAVFile'
main.cpp:(.text+0x105): undefined reference to `alBufferData'
main.cpp:(.text+0x125): undefined reference to `alutUnloadWAV'
main.cpp:(.text+0x139): undefined reference to `alGenSources'
main.cpp:(.text+0x13e): undefined reference to `alGetError'
main.cpp:(.text+0x172): undefined reference to `alSourcei'
main.cpp:(.text+0x191): undefined reference to `alSourcef'
main.cpp:(.text+0x1b0): undefined reference to `alSourcef'
main.cpp:(.text+0x1cd): undefined reference to `alSourcefv'
main.cpp:(.text+0x1ea): undefined reference to `alSourcefv'
main.cpp:(.text+0x20b): undefined reference to `alSourcei'
main.cpp:(.text+0x210): undefined reference to `alGetError'
/tmp/cc05VtwK.o: In function `main':
main.cpp:(.text+0x2a1): undefined reference to `alutInit'
main.cpp:(.text+0x2a6): undefined reference to `alGetError'
main.cpp:(.text+0x310): undefined reference to `alSourcePlay'
main.cpp:(.text+0x31f): undefined reference to `alSourceStop'
main.cpp:(.text+0x32e): undefined reference to `alSourcePause'
collect2: ld returned 1 exit status


```

therfore a.out is not generated in this case.............

---

### Post by Habbit on 2009-06-15
You seem to need to _link_ against the alut library, just like you do with glut. Try adding -lalut to the compilation command line

---

### Post by abhilashm86 on 2009-06-15
> **Habbit said:**
> You seem to need to _link_ against the alut library, just like you do with glut. Try adding -lalut to the compilation command line

yes it compiled fine.........first time i tried this alut and was confusion whether to use alu or alut.......well thanks

---

