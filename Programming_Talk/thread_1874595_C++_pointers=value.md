---
title: "C++ pointers=value"
date: 2011-11-03
forum: Programming Talk
---

### Post by dep0 on 2011-11-03
Hi. I was writing a pretty simple program using pointers and i was wondering if it's ok to write the following, and if it is what the result will be.On the other hand if it is not ok, why is it wrong? (I don't suggest running it cause i guess it will probably crash)

```
include<iostream>
using namespace std;
int main()
{
 int *p;
 p=1000;
 cout << p;
 return 0;
}
```

---

### Post by Zugzwang on 2011-11-03
Three things:

[LIST=1]
[*]If you post code here, make sure it compiles. Yours doesn't with GCC 4.4. (If you use a special C++ dialect, please say so) - You have to change add a "#" at the beginning of the first line. Also, "p=1000;" is not allowed - you will need to typecast the value "1000" first. So I assume that you intend this line to mean something like "p = (int*)1000;"
[*]Don't be afraid of your program crashing! The Linux kernel will protect all other processes. (Ok, I have to admit that if you run a program as root, then in theory, the program is allowed to do very nasty stuff (which this program doesn't)). The thing to be afraid of is your program not crashing when you are doing something that has undefined behaviour.
[*]What you are doing in your program is to send a pointer to "std::cout". This has defined behaviour: the pointer address itself is printed, typically in hexadecimal form. As you are never dereferencing your pointer in this program, no crash can/will occur. 
[/LIST]

---

### Post by cgroza on 2011-11-03
This kind of code is useful sometimes. For example in writing hardware drivers, where you have to access some known locations in memory.

But making a pointer point to a random byte in memory is rarely useful. And if that byte is not part of your program's memory, you will probably get a segfault.

---

### Post by Zugzwang on 2011-11-03
> **cgroza said:**
> And if that byte is not part of your program's memory, you will probably get a segfault.

...but only when you dereference the pointer. :-)

---

### Post by 3Miro on 2011-11-03
This will simply print the number 1000 in hexadecimal form.

A more interesting example would be to print:

```
cout << *p;
```

Then you will take the 4 bytes addressed by 1000, 1001, 1002 and 1003, put them together and print them as if they were one integer. Actually this should probably segfault as you shouldn't be allowed to read from memory that belongs to other programs. Depending on how you set the pointers, you may be able to read from some part of your program.

Reading from a random location in memory can be useful for system drivers or hacker attacks.

---

### Post by dep0 on 2011-11-03
Well i am really sorry for the wrong code, i was in a hurry.
I asked some friends and professors as well.
Most of them said that it's "forbidden" to access some part of the memory if you're not sure were it is located and what is written there.
So you say i am able to compile and run this code and the linux kernel will protect me from serious damage?
I will try the "cout << *p;" comand soon.

---

### Post by gsmanners on 2011-11-03
> **dep0 said:**
> Hi. I was writing a pretty simple program using pointers and i was wondering if it's ok to write the following, and if it is what the result will be.On the other hand if it is not ok, why is it wrong?

C and C++ allow you to do lots of crazy things (which is why a lot of programs crash if they aren't too terribly robust). What you *should* be doing in C++ is using methods and classes rather than relying on pointers and values. That will make it safer and easier to read for the next poor slob who has to change your code. :)

---

### Post by karlson on 2011-11-03
> **dep0 said:**
> Most of them said that it's "forbidden" to access some part of the memory if you're not sure were it is located and what is written there.

Ummmmmm....  No.  The OS implements guards against accessing by one process memory allocated to another process.  Trying to read or write to that location would likely cause a Segmentation Violation.

---

### Post by karlson on 2011-11-03
> **gsmanners said:**
> C and C++ allow you to do lots of crazy things (which is why a lot of programs crash if they aren't too terribly robust). What you *should* be doing in C++ is using methods and classes rather than relying on pointers and values. That will make it safer and easier to read for the next poor slob who has to change your code. :)

In homework you may not have a choice...

---

### Post by cgroza on 2011-11-03
> **Zugzwang said:**
> ...but only when you dereference the pointer. :-)
Yes. Why would one create a pointer and not dereference it at some point?

---

### Post by 3Miro on 2011-11-03
If you read or write to memory that doesn't belong to your program, then the Linux kernel (or Windows for that matter), should detect that and kill your program. If you read and write to random memory, you may or may not hit a place that belongs to your program. You may end up reading some other data or even op-code from your own program. Either way, it is not something that you would want to do.

If you want to try cool things with pointers, try the following:
```
#include<iostream>
using namespace std;
int main()
{
 int A[3] = {0, 1, 2};
 int *p = a;
 cout << *p << endl;
 p++;
 cout << *p << endl;
 p = &(a[1]);
 cout << *p << endl;
 p++;
 cout << *p << endl;
 return 0;
}
```

You can try to replace p++ with p+=2.

---

### Post by ARooster on 2011-11-04
> **dep0 said:**
> Well i am really sorry for the wrong code, i was in a hurry.
I asked some friends and professors as well.
Most of them said that it's "forbidden" to access some part of the memory if you're not sure were it is located and what is written there.
So you say i am able to compile and run this code and the linux kernel will protect me from serious damage?
I will try the "cout << *p;" comand soon.

Well, no matter what, you're not trying to change anything at that memory location. However I'd say in C++ programming there is rarely a need to directly enter a memory address (except perhaps when writing a device driver).

However, do try out your programs. If the code compiles run it and see what it does. What's the worst that can happen? Worst case scenario you will have to reboot your computer.

---

### Post by dep0 on 2011-11-05
Yes, i don't think i'll need it right away.
I was just curious to see what happens, and i was just little afraid to compile that after others (not on ubuntu forum) told me it's that's it's forbiden and that me computer will crash.

---

### Post by gsmanners on 2011-11-05
Walking on random memory could cause a crash if you didn't have memory protection, which is a new feature of that cutting edge 80286 CPU (it also blew people's minds with 16 bits rather than having to put up with 8 bits). :P

By the mid-90s, most OSes could utilize memory protection so that the worst thing that might happen would be a "memory protection fault" or something similar. I think Mac OS was the last OS to implement this feature.

---

### Post by ofnuts on 2011-11-05
> **dep0 said:**
> Yes, i don't think i'll need it right away.
I was just curious to see what happens, and i was just little afraid to compile that after others (not on ubuntu forum) told me it's that's it's forbiden and that me computer will crash.A properly designed operating system (Linux and other Unices, Windows (at least the NT family: XP, Vista, 7...), OSX and others) doesn't crash if a program does something stupid.

---

### Post by F.G. on 2011-11-05
so i just saw this thread and though i let people know that the other day i wrote a toy program (either in c or c++, can't remember) which makes a pointer to a fixed array and iterates it out of bounds, printing out the variable it points at a as char and int, and also printing out it's memory location.

i compiled and ran this program in Windows 7.

it seems that the result was (iterating up, and down seperately) that iterating down would produce garbage (the previous program variables, etc) and that a permission prevention mechanism of some kind (seg-fault type error) prevented me from going all the way down to 0x0 (i assume that the beginning of the memory is kernel/os stuff and this is why).

iterating up however was basically fine. initially garbage, then toward the top end of the memory started to read out the Windows copyright text (eg Windows 7 genuine (C) Microsoft Corporation somedate-somedate etc..)
before finally getting to the end (so there is a secret about Windows i imagine not many other people know).

i should point out that in neither instance did the machine crash, which indicated to me that rather than expanding the allocated memory used for the program it quite probably did just got to illegal memory addresses.

---

### Post by ofnuts on 2011-11-05
> **F.G. said:**
> so i just saw this thread and though i let people know that the other day i wrote a toy program (either in c or c++, can't remember) which makes a pointer to a fixed array and iterates it out of bounds, printing out the variable it points at a as char and int, and also printing out it's memory location.

i compiled and ran this program in Windows 7.

it seems that the result was (iterating up, and down seperately) that iterating down would produce garbage (the previous program variables, etc) and that a permission prevention mechanism of some kind (seg-fault type error) prevented me from going all the way down to 0x0 (i assume that the beginning of the memory is kernel/os stuff and this is why).

iterating up however was basically fine. initially garbage, then toward the top end of the memory started to read out the Windows copyright text (eg Windows 7 genuine (C) Microsoft Corporation somedate-somedate etc..)
before finally getting to the end (so there is a secret about Windows i imagine not many other people know).

i should point out that in neither instance did the machine crash, which indicated to me that rather than expanding the allocated memory used for the program it quite probably did just got to illegal memory addresses.Your program only had to access to user-space memory. Memory towards 0x0000 is usually unavailable (for historical reasons, in the segmented 286 memory architecture, the first 64K segment (mapped to 0x000000-0x00FFFF) didn't exist, and in current page oriented architecture, the first 4K page may not exist). I have seen some Unices in the past where the address 0x0000000 was initialized to 0x00000000. This meant that in C, testing a string for null and or empty was the same... this worked OK until you ported the code to other systems (Windows & OS/2) where reading 0x00000000 would cause a memory fault.

---

### Post by F.G. on 2011-11-05
yeah, that what i thought about the user/kernel space. iterating through the user space seems to be something you shouldn't be able to do, unless through the memory allocated to your program (i would have though).

also i thought that the copyright thing was kind of interesting.

---

### Post by Liiiim on 2011-11-05
I might be wrong, but isn't the kernel mapped to the upper memory of each process's memory space?  So it would kind of make sense that as you worked your way up eventually you would get to a Windows-related string.

---

### Post by dep0 on 2011-11-05
> **F.G. said:**
> yeah, that what i thought about the user/kernel space. iterating through the user space seems to be something you shouldn't be able to do, unless through the memory allocated to your program (i would have though).

also i thought that the copyright thing was kind of interesting.
Indeed this thing with the copyright was interesting as well as fun!
Can i do something similar with ubuntu?

---

### Post by F.G. on 2011-11-05
i think if you tried to run a similar program on linux you'd get a segfault (as a result of the tighter access security).

if you mean make ubuntu by default write some stuff on the unused bits in memory, i don't know? sounds way too complicated for me.

---

### Post by Liiiim on 2011-11-05
Running a similar program in Linux does not result in a segfault, at least not before it starts printing some strings out (mostly environment variables it seems).

---

### Post by cgroza on 2011-11-05
I tried something like that. It printed lots of garbage but at a point I could see environmental variables such as the PATH.
Here it is:
```

#include <stdio.h>

int main(void)
{
    char c = 'a';
    char* p = &c;
    for(p; ; p++) printf("%c ", *p);
    return 0;
}

```

---

### Post by nvteighen on 2011-11-06
> **cgroza said:**
> I tried something like that. It printed lots of garbage but at a point I could see environmental variables such as the PATH.
Here it is:
```

#include <stdio.h>

int main(void)
{
    char c = 'a';
    char* p = &c;
    for(p; ; p++) printf("%c ", *p);
    return 0;
}

```

This is because that "PATH" is actually argv[0], which is part of the program's stack. The fact that you haven't declared as an argument in main's signature doesn't mean it's not there (it just means you cannot access it using that name).

---

### Post by dep0 on 2011-11-06
> **cgroza said:**
> I tried something like that. It printed lots of garbage but at a point I could see environmental variables such as the PATH.
Here it is:
```

#include <stdio.h>

int main(void)
{
    char c = 'a';
    char* p = &c;
    for(p; ; p++) printf("%c ", *p);
    return 0;
}

```
Sorry if my question is pretty stupid but when does this thing stop?

---

### Post by cgroza on 2011-11-06
> **dep0 said:**
> Sorry if my question is pretty stupid but when does this thing stop?
The kernel will stop it eventually with a segfault.

---

