---
title: "Compiling FBX SDK and WxWidgets together"
date: 2008-07-17
forum: Packaging and Compiling Programs
---

### Post by TamisLaan on 2008-07-17
Hello! 

i am a novice programmer and i am having troubles compiling 2 SDK together:

MakeFile:

```
all:
	g++ -DK_PLUGIN -DK_FBXSDK -m64			`wx-config --cxxflags` 	 	-I/usr/local/FBX/include -I/usr/local/FBX/include/kbaselib -I/usr/x86_64-linux-gnu/avr/include			-I/usr/include/wx-2.8 				-c ./sources/*.cpp 
	
	g++ -m64  -o"main" ./*.o -L/usr/local/FBX/lib -lm -lstdc++ -lpthread -ldl -lfbxsdk_gcc4_amd64
```



Error Console:

```
make -f ./makefile.mk all 
g++ -DK_PLUGIN -DK_FBXSDK -m64			`wx-config --cxxflags` 	 	-I/usr/local/FBX/include -I/usr/local/FBX/include/kbaselib -I/usr/x86_64-linux-gnu/avr/include			-I/usr/include/wx-2.8 				-c ./sources/*.cpp 
g++ -m64  -o"main" ./*.o -L/usr/local/FBX/lib -lm -lstdc++ -lpthread -ldl -lfbxsdk_gcc4_amd64
./main.o: In function `wxThreadHelperThread::~wxThreadHelperThread()':
main.cpp:(.text._ZN20wxThreadHelperThreadD0Ev[wxThreadHelperThread::~wxThreadHelperThread()]+0x1d): undefined reference to `wxThread::~wxThread()'
./main.o: In function `wxThreadHelperThread::~wxThreadHelperThread()':
main.cpp:(.text._ZN20wxThreadHelperThreadD1Ev[wxThreadHelperThread::~wxThreadHelperThread()]+0x1d): undefined reference to `wxThread::~wxThread()'
./main.o: In function `wxTransform2D::InverseTransform(wxRect2DInt*) const':
main.cpp:(.text._ZNK13wxTransform2D16InverseTransformEP11wxRect2DInt[wxTransform2D::InverseTransform(wxRect2DInt*) const]+0x74): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
./main.o: In function `wxTransform2D::Transform(wxRect2DInt*) const':
main.cpp:(.text._ZNK13wxTransform2D9TransformEP11wxRect2DInt[wxTransform2D::Transform(wxRect2DInt*) const]+0x74): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
./main.o:(.rodata._ZTV20wxThreadHelperThread[vtable for wxThreadHelperThread]+0x18): undefined reference to `wxThread::TestDestroy()'
./main.o:(.rodata._ZTI20wxThreadHelperThread[typeinfo for wxThreadHelperThread]+0x10): undefined reference to `typeinfo for wxThread'
collect2: ld returned 1 exit status
make: *** [all] Error 1
```


I hope someone can make sense out of all this techno. :guitar:

thanks in advance, tamis.

---

### Post by WW on 2008-07-18
g++ is not finding the wx library.  Shouldn't there be an option in the second g++ command to link the wx libraries in your main program?  Try adding this option
```

`wx-config --libs`

```
to that command.

---

### Post by TamisLaan on 2008-07-18
> **WW said:**
> g++ is not finding the wx library.  Shouldn't there be an option in the second g++ command to link the wx libraries in your main program?  Try adding this option
```

`wx-config --libs`

```
to that command.

Wow your my hero! hehe.
I don't know why but before i compiled WxWidgets without any wx libs and it compiled fine.

strange that now all of the sudden i do need libs.

=D>=D>=D>=D>=D>=D>=D>=D> thanks Allot !!!!!!!

---

