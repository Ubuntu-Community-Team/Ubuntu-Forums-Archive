---
title: "makefile -D option"
date: 2013-05-13
forum: Packaging and Compiling Programs
---

### Post by MaWiSo on 2013-05-13
I have a project with multiple .cpp and .h files. I have a file called Globals.h which is included in all .cpp files. 
Now when compiling this file i use some -D options. these options affect all files not just Globals.h.

in my makefile i had to use the same -D options when compiling every file. of course when removing those options some undefined errors arise.
this means every time i change one of these options i have to recompile the whole project.
Is there a way that would let me compile ONLY Globals.h with these options ??

this is a part from my makefile:
lines that create Globals.o :
```


Globals.o : $(GlobalsLib) $(GlobalsInc)    g++ -c -Wall $(CodeDefined) $(UserDefined) $(GlobalsLib) -std=c++0x -o Globals.o
```

$(GlobalsLib) and $(GlobalsInc)are pathes to files Globals.h and Globals.cpp
$(CodeDefined) and $(UserDefined) are -U and -D options this code is for creating another .o file:```

NT_FFT_Decomp.o : $(GlobalsLib) $(GlobalsInc) $(NT_DecompLib) $(NT_DecompInc)      g++ -c -Wall $(CodeDefined) $(UserDefined) $(NT_DecompLib) -std=c++0x -o NT_FFT_Decomp.o
```
$(NT_DecompLib) $(NT_DecompInc) are also pathes to files.Notice that I had to add the same options in the g++ command.is there anyway around that ??

---

