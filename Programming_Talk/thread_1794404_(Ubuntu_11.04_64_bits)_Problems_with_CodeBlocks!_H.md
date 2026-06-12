---
title: "(Ubuntu 11.04 64 bits) Problems with CodeBlocks! Help!"
date: 2011-07-01
forum: Programming Talk
---

### Post by fedez on 2011-07-01
First thanks to all!
I am really noob with this...
Last two days I was trying to do a proper installation to run Codeblocks in Ubuntu Natty but I couldn't =0(. 
These issues are: 

When I compile and run this code, 

 
```
# Include <iostream> 
using namespace std; 
int main () 
{ 
int n; 
while (n! = 0) {cout <<"Enter a no."; cin>> n; 
if (n> = 7) {cout <<n <<"is greater than or equal to 7." <<Endl;}} 
return 0; 
} 
```


will not let me enter numbers, ie runs and ends without me having interacted with the program, the only thing displayed on the terminal is: 
Process Returned 0 (0x0) execution time: 0.002 s 
Press ENTER to continue. 

The other problem I have is that when I run the file from the ntfs partition that I use to keep my things, shows me permission denied, at this time does not give me the option to compile and run (build and run). 
instead on Windows 7, the program runs flawlessly and I can interact, enter the numbers and makes its execution normally. 

So I need help!!! to make a good install and configuration for Codeblocks 10.5 on Ubuntu 11.04 64-bit. 
Followed several tutorials for installing Codeblocks in Ubuntu  but most are outdated and I couldn't find a tutorial in noob mode for me!

REALLY SORRY FOR MY BAD ENGLISH!.
THANKS TO US, AND GOOGLE TRADUCTOR AND BABEL FISH!.
HELP MEEE!!!.

---

### Post by Seq on 2011-07-01
Some of your code got messed up somewhere and the formatting was causing invalid syntax. ("# Include" vs "#include", "! =" vs "!=", etc)

Anyway, the program was running as intended. You created an int called 'n'. The memory backing it is wiped before being handed over, thus your default value is 0 which then skips your loop.

Try giving it a value.

```
#include <iostream> 
using namespace std; 
int main ()  
{   
    int n**=-1**; 
    while (n != 0)
    {   
        cout <<"Enter a no.";
        cin>> n;  
 
        if (n >= 7)
        {   
            cout << n << "is greater than or equal to 7." << endl;
        }   
    }   
    return 0;  
}
```

As for NTFS, you can't set the execute bit on your compiled output, thus the system will not run it. Simple as that.

---

### Post by fedez on 2011-07-01
Thanks Seq!!!, i tried with your code and is working!!!, i was thinking that the problem was of Codeblocks... 
Also this original code is working in Windows 7 but not in Ubuntu:

```
#include <iostream>
using namespace std;
int main ()
{
    int n;
    while (n!=0) {cout<<"Enter a no.:";cin>>n;
                 if (n>=7) {cout<<n<<", is greather than or equal to 7."<<endl;} }
    return 0;
}
```

---

### Post by Zugzwang on 2011-07-01
> **fedez said:**
> Thanks Seq!!!, i tried with your code and is working!!!, i was thinking that the problem was of Codeblocks... 
Also this original code is working in Windows 7 but not in Ubuntu:


This is because your code has undefined behavior in it: You never initialize "n". It looks like the line in which you declare "n" should have been something like "int n=1;" Undefined behaviour means that everything can happen in such a case (within the possibilities), including that the program works as intended.

As a note, in Ubuntu there is a powerful tool for detecting such problems (apart from the debugger): valgrind. Here is an example. I saved the file as "/tmp/test.cpp" and ran the following in a terminal:

```

me@here:/tmp$ g++ -g test.cpp -o test
me@here:/tmp$ valgrind --tool=memcheck ./test
==9141== Memcheck, a memory error detector
==9141== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==9141== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==9141== Command: ./test
==9141== 
==9141== Conditional jump or move depends on uninitialised value(s)
==9141==    at 0x400979: main (test.cpp:6)
==9141== 
==9141== 
==9141== HEAP SUMMARY:
==9141==     in use at exit: 0 bytes in 0 blocks
==9141==   total heap usage: 0 allocs, 0 frees, 0 bytes allocated
==9141== 
==9141== All heap blocks were freed -- no leaks are possible
==9141== 
==9141== For counts of detected and suppressed errors, rerun with: -v
==9141== Use --track-origins=yes to see where uninitialised values come from
==9141== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 4 from 4)

```

---

### Post by NovaAesa on 2011-07-01
These sorts of errors can also be easily picked up by using the -Wall option in the compiler (it means "turn all warnings on"). Your can probably add these in the build options for CodeBlocks (I don't use codeblocks myself so I wouldn't know where to find the option).

I would always recommend using -Wall, it can warn you about all sorts of mistakes that you might make.

---

### Post by Pierrick584 on 2011-07-01
Even though it has been kinda well explained, as i am quite of a beginner with a good ammount of theorical knowledge, i think you could learn a bit more explained that way...


If you do not give a value to your variable, As Zugz said, everything can happend, it is beacause you kinda create a memory slot at a memory adress, but if you do not fill it, it can contain data that were previously avaible at the memory adress that is used for your variable, or it can also just initialise a random value automaticaly, such behavior can variate depending of the compiler, so, can be different from windows to linux, or can just be different beacause of the application you previously runned.


Hope i were clear enough, and that i dint made misstake by explaining something. Good luck

---

### Post by zobayer1 on 2011-07-02
> **Pierrick584 said:**
> Even though it has been kinda well explained, as i am quite of a beginner with a good ammount of theorical knowledge, i think you could learn a bit more explained that way...


If you do not give a value to your variable, As Zugz said, everything can happend, it is beacause you kinda create a memory slot at a memory adress, but if you do not fill it, it can contain data that were previously avaible at the memory adress that is used for your variable, or it can also just initialise a random value automaticaly, such behavior can variate depending of the compiler, so, can be different from windows to linux, or can just be different beacause of the application you previously runned.


Hope i were clear enough, and that i dint made misstake by explaining something. Good luck

Depends on where you allocate it, if it is on heap, i.e. global, or it is a static one, then it will be automatically initialized to 0, but if it is an auto variable, i.e. local one, that will contain garbage, which you can see, but doing so is not a good practice, as you can't be sure about the value.

---

### Post by fedez on 2011-07-04
Guys, thanks for yours tips. I will keep that in mind for the next excercises.  Have a nice day.

---

