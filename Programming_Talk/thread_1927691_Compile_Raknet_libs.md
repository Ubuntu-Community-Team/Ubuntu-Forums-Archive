---
title: "Compile Raknet libs"
date: 2012-02-18
forum: Programming Talk
---

### Post by Pierrick584 on 2012-02-18
Greetings, i have been trying to build the Raknet 4.036 library from source (they only distribute sources)

From their readme, they recommand a g++ command, and a cmake, both doesnt work, tried to add the source directory in a codeblock project, give me tons of warning, no error, no binary output :(  Anyone got suggestion? (if anyone happend to have the lib, just sending me the binary would be awesome too)

---

### Post by Pierrick584 on 2012-02-19
Bump... Still having issue. 
to add some details, i have google'd a bit about compiling shared library with g++, seems like it involve a -shared argument (maybe more procedure that i missed)

So i tried to add this to their command
```
pierrick@pcroom-linux:~/Desktop/raknet/Source$ g++ -shared -m64 -pthread -g *.cpp
/usr/bin/ld: /tmp/ccZs6BZZ.o: relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/tmp/ccZs6BZZ.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
pierrick@pcroom-linux:~/Desktop/raknet/Source$ g++ -shared -pthread -g *.cpp/usr/bin/ld: /tmp/ccGrBMi9.o: relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/tmp/ccGrBMi9.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
pierrick@pcroom-linux:~/Desktop/raknet/Source$ g++ -shared -pthread -g *.cpp^C
pierrick@pcroom-linux:~/Desktop/raknet/Source$ g++ -shared -m64 -lpthread -g *.cpp
/usr/bin/ld: /tmp/ccKi20UM.o: relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/tmp/ccKi20UM.o: could not read symbols: Bad value
collect2: ld returned 1 exit status

```

---

### Post by Bachstelze on 2012-02-19
We can't readily download this software, so can you at least post the readme? You probably shouldn't run g++ directly.

---

