---
title: "i cant install irrklang in ubuntu"
date: 2011-05-26
forum: Programming Talk
---

### Post by gentle5 on 2011-05-26
[CENTER][SIZE=3][COLOR=Black]Hi
[/COLOR][/SIZE][LEFT][SIZE=3][COLOR=Black]download irrklang but i didn't know how install or how compile [/COLOR][/SIZE]
[/LEFT]
[SIZE=3][COLOR=Black]
[/COLOR][/SIZE][LEFT][SIZE=3][COLOR=Black] i went to .../bin/linux-gcc [/COLOR][/SIZE]
[SIZE=3][COLOR=Red][COLOR=Black] and found libirrklang.so -pthread[/COLOR][/COLOR][/SIZE]
[SIZE=3][COLOR=Red][COLOR=Black] and i wrote in the terminal g++ libirrklang.so [/COLOR][/COLOR][/SIZE]
[SIZE=3][COLOR=Red][COLOR=Black] but show below[/COLOR][/COLOR][/SIZE]
usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/../../../crt1.o: In function `_start':
(.text+0x18 ): undefined reference to `main'
collect2: ld returned 1 exit status[/LEFT]
[SIZE=3][COLOR=Red][COLOR=Black] 

can you help me :([/COLOR]
[/COLOR][/SIZE][/CENTER]

---

### Post by Zugzwang on 2011-05-26
It appears as if the downloadable archive of Irrklang already contains the library in compiled form. Thus, there is nothing to compile. Go to the directory of an example and hit "make" there to compile the example instead.

---

### Post by gentle5 on 2011-05-26
thanks [Zugzwang]("http://ubuntuforums.org/member.php?u=403348")
examples   working now 
but i wrote in (my file) >>sound.cpp<<
#include <irrKlang.h>

when i wrote in the terminal g++ sound.cpp
show below

sound.cpp:12:22: fatal error: irrKlang.h: No such file or directory
compilation terminated.

what's the problem...
how compile it ...

---

### Post by Zugzwang on 2011-05-26
> **gentle5 said:**
> 
what's the problem...
how compile it ...

You will need to provide the compiler with information on where to find the include files for IrrKlang and the linker with information on where to find the libraries to link against.

Have a look at the file "Makefile" in the directories in the examples, which takes care of telling this to the compiler. I suggest that you look up what a "Makefile" is on google and use such Makefiles for your own projects as well. You can take one provided with an example and modify it for your own project.

---

### Post by gentle5 on 2011-05-26
thank you very Much

ok now i know how to compile it 

 i compile the file and create file.exe 

 when i launch file.exe
show below

irrKlang sound library version 1.3.0
Using ALSA driver
Could not open sound file: 01.mp3
hello



why could not open sound file??
can you help me


i wrote this

 #include <iostream>
 #include <irrKlang.h>
 
using namespace std;
 int main()
 {

        irrklang::ISoundEngine* engine = irrklang::createIrrKlangDevice();
       
        if (!engine) return 1; // could not start engine

        engine->play2D("01.mp3"); // play some mp3 file
       
       cout<<"hello\n";

        std::cin.get(); // wait until user presses a key
 
        engine->drop(); // delete engine
        return 0;
 }

---

### Post by gentle5 on 2011-05-26
ok it's work know thank you very much

---

