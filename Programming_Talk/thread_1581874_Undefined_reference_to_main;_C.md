---
title: "Undefined reference to main; C"
date: 2010-09-25
forum: Programming Talk
---

### Post by Kareta on 2010-09-25
Getting this error in eclipse ```

**** Clean-only build of configuration Debug for project dice roller ****

make clean 
rm -rf  ./diceroller.o  ./diceroller.d  lol
 

**** Build of configuration Debug for project dice roller ****

make all 
Building file: ../diceroller.c
Invoking: GCC C Compiler
gcc -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"diceroller.d" -MT"diceroller.d" -o"diceroller.o" "../diceroller.c"
Finished building: ../diceroller.c
 
Building target: dice roller
Invoking: GCC C Linker
gcc  -o"dice roller"  ./diceroller.o   
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [dice roller] Error 1
```

Here's the code:```
/*
 * 13-sided Die Roller.
 */

#include <stdio.h>

int main(void){

    int w;

    int x=0;
    int y;
    int z;

    printf("Press 1 to run program\n");

    printf("Press 2 to cancel.\n");

    printf("Press 3 for more information.\n");
    scanf("%d", &y);

    switch(y){

    case 1:
    printf("Enter number of times you would like to roll:");
    scanf("%d", &w);
    srand(time(NULL));
    while(x<w){
    printf("%d\n", 1+rand()%13);
    x++;
    }
    break;
    case 2:
    printf("Program terminated.");
    break;
    case 3:
    printf("This program will roll a 13 sided die once.\n\n");
    switch(z){
    default:
        printf("Press 1 to run program:");
        scanf("%d", &z);
        if(z == 1){

            printf("Enter number of times you would like to roll:");
                scanf("%d", &w);
                srand(time(NULL));
                while(x<w){
                printf("%d\n", 1+rand()%13);
                x++;
        }
        }
        else
        {
            printf("Please enter a correct argument:");
        }
        break;
    }
    break;
    default:
    printf("Please enter a correct argument.");
    break;
    }
    return 20;
}
```

---

### Post by jon zendatta on 2010-09-25
```
return 0;
```

---

### Post by Bachstelze on 2010-09-25
The code compiles and runs fine here. You have a lot of layout issues, though. Your indentation is terrible, and what's with the switch(z) with only a default case? And return 20?

---

### Post by worksofcraft on 2010-09-25
include following at head of your file:
```

#include <time.h> // time
#include <stdlib.h> // srand

```

I compile and run it like this:
```


$> g++ dice13.c
$> ./a.out
Press 1 to run program
Press 2 to cancel.
Press 3 for more information.
1
Enter number of times you would like to roll:4
3
9
5
2
$>

```

p.s. oh yeah I forgot to mention I named it dice13.c instead of diceroller but that shouldn't make any difference.

---

### Post by Kareta on 2010-09-25
Sorry, I'm just a beginner >.>. 

Thanks a lot for the help though, I appreciate it, still trying to get it to compile.

---

### Post by Bachstelze on 2010-09-25
> **Kareta said:**
> Sorry, I'm just a beginner >.>. 

Thanks for the criticism though,

Then  I suggest you really start working on your code layout, especially indentation.  Otherwise, you'll make a lot of people hate you. ;)

---

### Post by worksofcraft on 2010-09-25
> **Kareta said:**
> Sorry, I'm just a beginner >.>. 

Thanks a lot for the help though, I appreciate it, still trying to get it to compile.

I saw you were using all that make malarchy... IMO it can get too much to take on board when you start. Did you try the simple g++ command? The program that creates is called a.out but it's easy enough to rename.

---

### Post by pbrane on 2010-09-25
For a simple single file program it may be easier to compile on the command line:
```

gcc -W -Wall -o diceroller diceroller.c

```

this will create an executable called **diceroller**. The **-W -Wall** will print all warnings as well, you should fix all warnings, and of course errors too. Add a **-g** and you will create an executable with debug info. Then you can learn how to run it in **gdb** debugger.

---

### Post by Kareta on 2010-09-26
When compiling from the command line do I have to specify a file location? 

Where does that fit in the syntax?

---

### Post by worksofcraft on 2010-09-26
> **Kareta said:**
> When compiling from the command line do I have to specify a file location? 

Where does that fit in the syntax?

oh... yes you should make the folder where your source files are be the current working directory otherwise you have to give the path to each file.

e.g. put the source files on your Desktop then you open a command line prompt and type

cd ~/Desktop

now the Desktop folder will be the current working directory and so the compiler will look there first for the source files.

Note that when you come to run your program the shell does not look in current folder first so you have to give it the path. Hence ./a.out to run a file called a.out

so if you put it all on Desktop then those commands should be:

cd ~/Desktop
g++ diceroller.c
./a.out

p.s. ~ means your home directory, . means the current working directory and .. is the directory above it. Directories are sometimes also called "folders" because that's what they call them on Microsoft systems. Also pbrane's advice is a lot more correct than mine because you should probably use the C compiler and not the C++ compiler to compile C programs, but they both will compile your program.

---

