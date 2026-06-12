---
title: "Puzzling bug"
date: 2007-12-12
forum: Programming Talk
---

### Post by Auria on 2007-12-12
Hi,

I'm writing a project in C++ and am meeting a totally puzzling bug. Since this bug seems very particular to my application and not easy to isolate, I do not really expect an answer but would like to seek advice on how you would debug that.

The bug seems to be memory corruption. I tried using gdb, but it only shows the crash that happens as a result of the corruption and not where the corruption itself occurs.

I have a pointer *Track* track* that is part of the object and suddenly becomes corrupted.

```

for(int i=1; i<size; i++)
{
                 Note* current = track->getNote(candidates[i]);
		 relocator.rememberNote( current );
                    
		fret.push_back( track->getNoteFret(candidates[i]) );
					string.push_back( track->getNoteString(candidates[i]) );
					
{
		Action::ShiftString action( base_string-i-track->getNoteString(candidates[i]) , candidates[i]);
					action.setParentTrack(track);
					action.perform();
// here 'track' is okay
}
// here 'track' is 0

}

```

now it seems like the pointer is corrupted because object "action" is destroyed. But its destructor, and the destructor of its base class, are emty. And, if I create the object on the heap, and do not delete it, "track" is still corrupted, albeit a bit later and apparently randomly.

I then tried Valgrind. First, it very often gives me kernel panics where i need to shut down my computer... second, once it did not crash but also did not seem to get the corruption itself, only the result of the corruption...

I would also like to point out i use many std::vector's in these classes, maybe there is something i could have forgotten?

so now the big question... how would you go about debugging that?? :-s
thanks

---

### Post by stroyan on 2007-12-13
I would use gdb and put a watchpoint on the value of "track" as an address.
Then either letting it free run or single stepping at the assembly instruction level
would show the exact source line or instruction that overwrote "track".
The code that overwrites "track" may not be a guilty party.  But it will at least
be a big clue as to what went wrong.

Here is a small example that you can use to get a feel for this debugging tactic.
The watchpoint is set as a hex constant instead of "token" or "*&token" so that
the expression "watch *(char **)0xbf97f884" will be valid to gdb even when
executing in code that has no definition for "token" or even no debuggable
source code.
```
$ cat strtok.c 
#include <string.h>
#include <stdio.h>
main()
{
        char string[] = "wor\nds sepa,rat\ned by spa\nces -- and, punc:tuation!";
        char* pString = string;
        // const char delimiters[] = "\n";
        // char delimiters = '\n';
        char *token;
        char *null = NULL;

        token = strsep (&pString,"\n");  /* token => "words" */
        while((token=strsep(&pString,"\n"))!=NULL){
                printf("%s\n",token);
        }
}
$ gdb
(gdb) b main
Breakpoint 1 at 0x8048415: file strtok.c, line 4.
(gdb) r
Starting program: /home/mike/a.out 

Breakpoint 1, main () at strtok.c:4
4       {
(gdb) p/a &token
$1 = 0xbf97f884
(gdb) watch *(char **)0xbf97f884
Hardware watchpoint 2: *(char **) 3214407812
(gdb) c
Continuing.
Hardware watchpoint 2: *(char **) 3214407812

Old value = 0x0
New value = 0xbf97f88c "wor"
main () at strtok.c:13
13              while((token=strsep(&pString,"\n"))!=NULL){


```

---

### Post by Auria on 2007-12-13
Hi,

first of all thanks for your intro to watchpoints, it's a technique that's worth learning ;)

ufortunately it gets even more puzzling for me, because i get something like "Watchpoint deleted in thread 1, The program has left the block in which its expression is valid." before the wrong bit happens. So what does this mean, the object i'm working in is deleted before its execution is done?

I'll continue searching but would appreciate any input.
thanks

---

### Post by iharrold on 2007-12-13
are you passing in track as a const thus ensuring it isn't manipulated?  

Also, it sounds like a scope issue... though I cannot see why.

---

### Post by Auria on 2007-12-13
No, track is not cons, it is a member of a class. The error happens in a child of that class

BUT... i found another bug. it was a bit of code that didn't do what it was supposed to do. Upon fixing this bit of code, this thread's bug magically disappeared :confused: I have no clue why the bug disappeared, but it did so for now it's ok :)

thanks everyone anyway

---

### Post by stroyan on 2007-12-13
"The program has left the block in which its expression is valid." 
It sounds like you used a watchpoint based on a symbol such as "watch track".
If you use a watchpoint based on a hex address then the expression should remain valid.
It would look like this (with a different hex address value.)
(gdb) p/a &track
$1 = 0xbf97f884
(gdb) watch *(void **)0xbf97f884

---

### Post by Auria on 2007-12-13
> **stroyan said:**
> "The program has left the block in which its expression is valid." 
It sounds like you used a watchpoint based on a symbol such as "watch track".
If you use a watchpoint based on a hex address then the expression should remain valid.
It would look like this (with a different hex address value.)
(gdb) p/a &track
$1 = 0xbf97f884
(gdb) watch *(void **)0xbf97f884

ok thanks i'll keep that in mind. Sounds like i'll need to leave the comforts of my IDE and learn gdb from terminal :)

---

