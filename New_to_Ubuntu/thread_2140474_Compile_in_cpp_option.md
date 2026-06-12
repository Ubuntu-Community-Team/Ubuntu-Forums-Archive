---
title: "Compile in cpp option"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by coolecho on 2013-04-29
Hello,

I'm trying to compile a c++ program in Ubuntu. I am reading "The Linux Development book". It says that there are gcc options such as:

-x c (lowercase c) C language selection
-x c++ C++ file
-x objective-c Objective C
-x assembler Assembler file
-x f77 Fortran file
-x java Java language file


However I am getting errors using "gcc testcpp.cpp -x c++ -o test" , or "gcc testcpp.cpp -o test".

/tmp/ccYT4GjM.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

I guess these options don't apply for Ubuntu?? Is there a better reference book for Ubuntu programming?

Thanks

---

### Post by steeldriver on 2013-04-29
To compile C++ it's preferable to explicitly invoke g++ rather than gcc

```
g++ testcpp.cpp -o test
```

If you really wanted to compile C++ with gcc at a minimum you would need to specify the stdc++ library:

```
gcc testcpp.cpp -o test **-lstdc++**
```

AFAIK the -x option is used to tell the compiler what language your source file contains - which is redundant if you are using the .cpp suffix. For example if you had a C++ source file but called it test.txt then:

```

/Documents/forums$ gcc **test.txt** -o test -lstdc++
test.txt: file not recognized: File format not recognized
collect2: ld returned 1 exit status
/Documents/forums$ 
/Documents/forums$ gcc **-x c++ test.txt** -o test -lstdc++
/Documents/forums$ 
/Documents/forums$ ./test
Hello World!
/Documents/forums$ 

```

You can check the manual page for all the command line options

```
man gcc
```

---

### Post by coolecho on 2013-04-30
Works great! 
Forgot the "./testcpp.cpp" to run it, but figured it out.
I found other info for compile with errors "g++ -Wall -W -Werror test.cpp -o testcpp"

Thanks

---

