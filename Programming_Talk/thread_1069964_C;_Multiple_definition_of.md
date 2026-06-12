---
title: "C; Multiple definition of"
date: 2009-02-14
forum: Programming Talk
---

### Post by OutOfReach on 2009-02-14
Hey there, I've just started screwing around with multiple file programs.
So I'll get to the point, I keep getting these errors that say 'multiple definition of ----' ---- being a variable name. Here is the output of *make*:
```

cc    -c -o recommendations.o recommendations.c                                                                                
cc    -c -o main.o main.c                                                                                                      
cc    -c -o questions.o questions.c                                                                                            
gcc recommendations.o main.o questions.o -o KomputerBuilder                                                                    
main.o:(.rodata+0x18): multiple definition of `CPUS_STRING'                                                                    
recommendations.o:(.rodata+0x18): first defined here                                                                           
main.o:(.rodata+0x40): multiple definition of `VIDEOCARDS_STRING'                                                              
recommendations.o:(.rodata+0x40): first defined here                                                                           
main.o:(.rodata+0x78): multiple definition of `MOTHERBOARDS_STRING'                                                            
recommendations.o:(.rodata+0x78): first defined here                                                                           
main.o:(.rodata+0xb0): multiple definition of `HDDS_STRING'                                                                    
recommendations.o:(.rodata+0xb0): first defined here                                                                           
questions.o:(.rodata+0x18): multiple definition of `CPUS_STRING'                                                               
recommendations.o:(.rodata+0x18): first defined here                                                                           
questions.o:(.rodata+0x40): multiple definition of `VIDEOCARDS_STRING'                                                         
recommendations.o:(.rodata+0x40): first defined here                                                                           
questions.o:(.rodata+0x78): multiple definition of `MOTHERBOARDS_STRING'                                                       
recommendations.o:(.rodata+0x78): first defined here
questions.o:(.rodata+0xb0): multiple definition of `HDDS_STRING'
recommendations.o:(.rodata+0xb0): first defined here
questions.o: In function `questionsStartSequence':
questions.c:(.text+0x1a): undefined reference to `askCPU'
questions.c:(.text+0x23): undefined reference to `askVideoCard'
questions.c:(.text+0x2c): undefined reference to `askHardDrive'
collect2: ld returned 1 exit status
make: *** [KomputerBuilder] Error 1


```

The Makefile:
```

SRC = recommendations.c main.c questions.c
OBJ = recommendations.o main.o questions.o
PROG = KomputerBuilder

$(PROG): $(OBJ)
	gcc $(OBJ) -o $(PROG)

$(OBJ): $(SRC)

```

main.c:
```

#include <stdio.h>
#include "Computer.h"

int main(void)
{
    printf("Welcome to %s version %i.%i!\n", PROGRAM_NAME, PROGRAM_VERSION_MAJOR, PROGRAM_VERSION_MINOR);
    printf("Let's get started...\n");
    Computer userComputer;
    
    questionsStartSequence(&userComputer);
}

```

questions.c:
```

#include <stdio.h>
#include "Computer.h"


void questionsStartSequence(Computer *userComp)
{
    askMotherboard(userComp);
    askCPU(userComp);
    askVideoCard(userComp);
    askHardDrive(userComp);
}

void askMotherboard(Computer *userComp)
{
    printf("%s\nWhat is your motherboard? ", MOTHERBOARDS_STRING);
    scanf("%i", userComp->userMotherboard);
}

```

recommendations.c:
```

#include <stdio.h>
#include "Computer.h"

void videoCardRecommend(Computer userComp)
{
    if (userComp.userVideoCard == nvidia)
    {
        printf("Video Card: NVidia; I recommend searching online if this card is compatible, if it is make sure to use the propietary drivers!\n");
    }
    else if (userComp.userVideoCard == intel_integrated)
    {
        printf("Video Card: Intel; No recommendations; Intel video cards usually work perfectly with Linux.\n");
    }
    else if (userComp.userVideoCard == ati)
    {
        printf("Video Card: ATI; I recommend getting a different brand (Intel/NVidia), ATI video cards don't usually have good support on Linux.\n");
    }
    else
    {
        printf("Video Card: <unknown>\n");
    }
}

void motherboardRecommend(Computer userComp)
{
    if (userComp.userMotherboard == intel_motherboard)
    {
        printf("Motherboard: Intel; Remember not to buy an AMD processor, Intel motherboards are made for Intel CPU's.\n");
    }
    else if (userComp.userMotherboard != intel_motherboard || userComp.userMotherboard != evga || userComp.userMotherboard != asus)
    {
        printf("Motherboard: <unknown>\n");
    }
    else
    {
        printf("Motherboard: %s; No recommendations.\n", (userComp.userMotherboard == evga) ? "EVGA" : ( (userComp.userMotherboard == intel_motherboard) ? "Intel" : "ASUS" ) );
    }
}

void hardDriveRecommend(Computer userComp)
{
    printf("Hard Drive: %s; Remember to check online about the hard drive's power management.\n", (userComp.userHardDrive == western_digital) ? "Western Digital" : ( (userComp.userHardDrive == seagate) ? "Seagate" : "Intel" ) );
}

void processorRecommend(Computer userComp)
{
    printf("CPU: %s; Remember to buy motherboards with compatible sockets for this type of CPU.\n", (userComp.userCPU == intel) ? "Intel" : "AMD");
}

```

And finally, Computer.h:
```

/* The header file for a small practice exercise for
 * Chapter 15 of Programming in C.
 * February 13, 2009; 7:13 PM. */

enum CPU { intel=1, amd };
enum videoCard { intel_integrated=1, nvidia, ati };
enum motherboard { evga=1, gigabyte, asus, intel_motherboard };
enum hardDrive { western_digital=1, seagate, intel_hdd };

typedef struct {
                    enum CPU userCPU;
                    enum videoCard userVideoCard;
                    enum motherboard userMotherboard;
                    enum hardDrive userHardDrive;
} Computer;

/* ---------------------------- VARIABLES ---------------------------------------- */
const char * const CPUS_STRING = "\t1. Intel\n\t2. AMD";
const char * const VIDEOCARDS_STRING = "\t1. Intel\n\t2. NVidia\n\t3. ATI";
const char * const MOTHERBOARDS_STRING = "\t1. EVGA\n\t2. Gigabyte\n\t3. ASUS\n\t4. Intel";
const char * const HDDS_STRING = "\t1. Western Digital\n\t2. Seagate\n\t3. Intel";

/* ---------------------------- DEFINITIONS -------------------------------------- */
#define PROGRAM_NAME "KomputerBuiler"
#define PROGRAM_VERSION_MAJOR 0
#define PROGRAM_VERSION_MINOR 1

/* ---------------------------- PROTOTYPES --------------------------------------- */
void videoCardRecommend(Computer userComp);
void motherboardRecommend(Computer userComp);
void hardDriveRecommend(Computer userComp);

void questionsStartSequence(Computer *userComp);
void askMotherboard(Computer *userComp);
void askCPU(Computer *userComp);
void askVideoCard(Computer *userComp);
void askHardDrive(Computer *userComp);

```

What am I doing wrong? I've searched google and I have come up with lots of different answers but I don't really know what to do.
Thanks.

---

### Post by mike_g on 2009-02-14
You might have to add header guards to stop stuff being defined more than once. IIRC something like:
```

#ifndef PROGRAM_NAME
#include "Computer.h"
#endif
```

---

### Post by jpkotta on 2009-02-14
You should have such a thing in each header file, but it should be specific for each header.
```
#ifndef __COMPUTER_H__
#define __COMPUTER_H__

/* contents of computer.h .... */

#endif /* __COMPUTER_H__ */

```

You need to make it header specific.  It's called making the header [idempotent]("http://en.wikipedia.org/wiki/Idempotent").

---

### Post by dwhitney67 on 2009-02-14
You need to declare these as static, so that only one copy is created.  So for each, just preface each statement with the keyword "static".

```

const char * const CPUS_STRING = "\t1. Intel\n\t2. AMD";
const char * const VIDEOCARDS_STRING = "\t1. Intel\n\t2. NVidia\n\t3. ATI";
const char * const MOTHERBOARDS_STRING = "\t1. EVGA\n\t2. Gigabyte\n\t3. ASUS\n\t4. Intel";
const char * const HDDS_STRING = "\t1. Western Digital\n\t2. Seagate\n\t3. Intel";

```

P.S.  Don't forget to implement these functions!
```

questions.c:(.text+0x18): undefined reference to `askCPU'
questions.c:(.text+0x23): undefined reference to `askVideoCard'
questions.c:(.text+0x2e): undefined reference to `askHardDrive'

```

---

### Post by OutOfReach on 2009-02-14
> **mike_g said:**
> You might have to add header guards to stop stuff being defined more than once. IIRC something like:
```

#ifndef PROGRAM_NAME
#include "Computer.h"
#endif
```

> **jpkotta said:**
> You should have such a thing in each header file, but it should be specific for each header.
```
#ifndef __COMPUTER_H__
#define __COMPUTER_H__

/* contents of computer.h .... */

#endif /* __COMPUTER_H__ */

```

You need to make it header specific.  It's called making the header [idempotent]("http://en.wikipedia.org/wiki/Idempotent").
Right, how could I forget this.


> **dwhitney67 said:**
> You need to declare these as static, so that only one copy is created.  So for each, just preface each statement with the keyword "static".

```

const char * const CPUS_STRING = "\t1. Intel\n\t2. AMD";
const char * const VIDEOCARDS_STRING = "\t1. Intel\n\t2. NVidia\n\t3. ATI";
const char * const MOTHERBOARDS_STRING = "\t1. EVGA\n\t2. Gigabyte\n\t3. ASUS\n\t4. Intel";
const char * const HDDS_STRING = "\t1. Western Digital\n\t2. Seagate\n\t3. Intel";

```

P.S.  Don't forget to implement these functions!
```

questions.c:(.text+0x18): undefined reference to `askCPU'
questions.c:(.text+0x23): undefined reference to `askVideoCard'
questions.c:(.text+0x2e): undefined reference to `askHardDrive'

```

Yes! This is what got rid of those errors, I thank you.

---

### Post by jimi_hendrix on 2009-02-14
pure curiousity:

why use suns compiler?

---

### Post by jespdj on 2009-02-14
> **jimi_hendrix said:**
> why use suns compiler?
Sun's compiler? Why do you think the OP uses Sun's compiler?

---

### Post by OutOfReach on 2009-02-14
> **jimi_hendrix said:**
> pure curiousity:

why use suns compiler?

Am I? :s

---

### Post by jimi_hendrix on 2009-02-14
i miss read...first thing i saw was cc (sun's compiler's name)

---

### Post by jpkotta on 2009-02-14
cc is the default compiler.  It is almost certainly aliased to gcc.
```
$ readlink -f $(which cc)
/usr/bin/gcc-4.3

```

---

### Post by nvteighen on 2009-02-15
> **jimi_hendrix said:**
> i miss read...first thing i saw was cc (sun's compiler's name)
cc was the name of the original UNIX compiler. Then, derivative OSs used that as a convention... (Sun (Open)Solaris, for example, which is a true UNIX system).

---

