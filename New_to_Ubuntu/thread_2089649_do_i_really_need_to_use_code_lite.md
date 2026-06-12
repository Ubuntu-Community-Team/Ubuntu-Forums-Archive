---
title: "do i really need to use code lite"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by mike acker on 2012-11-29
do i really need to use code lite to compile c

or could i *please* just have a script, e.g.

```
cl factoring.c
```

---

### Post by Vaphell on 2012-11-29
no, you don't need any IDE to compile c/c++
codelite manages projects and offers convenience, but under the hood it still calls the command line compiler. You can do the same by hand.

try ```
gcc factoring.c -o factoring
```

---

### Post by mike acker on 2012-11-30
> **Vaphell said:**
> no, you don't need any IDE to compile c/c++
codelite manages projects and offers convenience, but under the hood it still calls the command line compiler. You can do the same by hand.

try ```
gcc factoring.c -o factoring
```

yea! thanks!!

all I do is some small programs to solve little stuff; I don't need the Project Manager

You would think I could have a "Misc" project with a half dozen little programs in it but I havn't been able to get that to work.  apparently a "Project" or "Workspace" means 1 and only 1 main function.

---

### Post by mike acker on 2012-11-30
......mmmm that's not all there is to this
```

mike@Acker4:~/Desktop/c_scrap_lib$ cpp hello5.cpp -o hello5
mike@Acker4:~/Desktop/c_scrap_lib$ ls
Box_Problem_Directory  HelloWorld              sample
comment for bruce.txt  Pole_Problem            updating samba.txt
hello5                 Pole_Problem_Directory  updating samba.txt~
hello5.cpp             Pole_Problem.mk         vet schedule.ggb
mike@Acker4:~/Desktop/c_scrap_lib$ ./hello5
bash: ./hello5: Permission denied
mike@Acker4:~/Desktop/c_scrap_lib$ ll hello5
-rw-rw-r-- 1 mike mike 17747 Nov 30 14:48 hello5
mike@Acker4:~/Desktop/c_scrap_lib$ sudo chmod 711 hello5
mike@Acker4:~/Desktop/c_scrap_lib$ ll hello5
-rwx--x--x 1 mike mike 17747 Nov 30 14:48 hello5*
mike@Acker4:~/Desktop/c_scrap_lib$ ./hello5
./hello5: line 33: extern: command not found
./hello5: line 39: typedef: command not found

```one thing i've been noticing: 12.04 is different from 10.04 and so procedures for 10.04 may not be the same on 12.04

this is probably because the program didn't compile
```

#include <stdio.h>

 main();

 main()
 { puts("Hello World Version 5");
   return;
 }

```probably because it didn't find stdio.h

---

### Post by steeldriver on 2012-11-30
```
gcc
```not 

```
cpp
```... and you probably want 'printf' not 'puts'

```
#include <stdio.h>

int main()
{ 
   printf("Hello World Version 5\n");
   return 0;
}
```

---

### Post by mike acker on 2012-11-30
yep, gcc works better; must have had a cpp short in my brain!

interesting it will not accept the classic form:

the prototype statement:
```

 main();

```is equivalent to
```

 void main(void);

```naturally having declared no return value
```

 return;

```should be accepted to end the function

how did the COBOL people infiltrate Kernigan & Ritchie's work ?

needless to say the main() function *should* return a value; normally 0 for successful execution.  I never understood that although it's like System/360 in that regard, rc=0 means no errors detected... where as in  C 0==false and !=0 = true ....

thanks for the help; i think I'm good to go now!!
~~~
amendment

I did and apt-get install for cpp  should i remove that now ?

---

### Post by steeldriver on 2012-11-30
Glad you got it working - cpp is a preprocessor, it's part of the gcc 'compiler collection' so don't remove it - but not usually called on its own

It's not necessary to declare (prototype) your main function, the definition itself is sufficient - AFAIK it's not compulsory to return a value from 'main' either - but it's considered good programming practice

Also by convention most people stick to '.c' as a suffix for pure C files and use '.cpp' for true C++

If you want to try a C++ 'hello world' you can do that like

```
#include <iostream>

int main(void)
{
    std::cout << "Hello world!" << std::endl;
    return 0;
}

```You would build *that* with g++ instead of gcc, e.g.

```
g++ -o hello hello.cpp
```

Have fun :)

---

### Post by mike acker on 2012-11-30
thanks

I did remove the cpp and it took out more than i expected -- so i had to put it back and gcc as well

all seems ok though

after some experiments I find it does not want to let me declare 
```

 
 void main();


```-- or return -- with no value.  this is a good thing really; I don't remember this as having been a restriction earlier... but then i'm only a recent refugee from that other software company

i find now i can edit my "C" source using my BlueFish editor.  If I can find a way to get BlueFish to issue the compile statement that would be pretty cool

playing a little more the compiler did allow me to have a null return value on a subordinate function
```

#include <stdio.h>

 int main();
 void rat_fun();

 int main()
 { puts("Hello World Version 5a");
  rat_fun();
   return 0;
 }

 void rat_fun()
 { puts("Rats are not fun");
   return;
 }

```thanks for the help

---

