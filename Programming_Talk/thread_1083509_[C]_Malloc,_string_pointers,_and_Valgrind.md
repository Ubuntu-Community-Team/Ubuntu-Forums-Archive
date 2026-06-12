---
title: "[C] Malloc, string pointers, and Valgrind"
date: 2009-03-01
forum: Programming Talk
---

### Post by OutOfReach on 2009-03-01
So as my first 'project' I decided to make a Tic Tac Toe game. I have a problem, though. I created a typedef consisting of a struct, consisting of a character pointer and an enum. In a seperate file I try to allocate space with it (with malloc()) and at the end of the program I free it.
When I execute it, it executes fine but it says 'Aborted' at the end. So I installed Valgrind and investigated, here is it's output:
```

$ valgrind --tool=memcheck --leak-check=full --track-origins=yes ./TicTacToe                                                                                   
==20053== Memcheck, a memory error detector.                                                     
==20053== Copyright (C) 2002-2008, and GNU GPL'd, by Julian Seward et al.                        
==20053== Using LibVEX rev 1878, a library for dynamic binary translation.                       
==20053== Copyright (C) 2004-2008, and GNU GPL'd, by OpenWorks LLP.                              
==20053== Using valgrind-3.4.0, a dynamic binary instrumentation framework.                      
==20053== Copyright (C) 2000-2008, and GNU GPL'd, by Julian Seward et al.                        
==20053== For more details, rerun with: -v                                                       
==20053==                                                                                        
Enter your name: OutOfReach                                                                      
==20053== Conditional jump or move depends on uninitialised value(s)                             
==20053==    at 0x4C24099: strlen (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)       
==20053==    by 0x4E6D9FD: vfprintf (in /lib/libc-2.9.so)                                        
==20053==    by 0x4E73C39: printf (in /lib/libc-2.9.so)                                          
==20053==    by 0x4006D1: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                  
==20053==  Uninitialised value was created by a stack allocation                                 
==20053==    at 0x400538: (within /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                   
==20053==                                                                                        
==20053== Conditional jump or move depends on uninitialised value(s)                             
==20053==    at 0x4C240A8: strlen (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)       
==20053==    by 0x4E6D9FD: vfprintf (in /lib/libc-2.9.so)                                        
==20053==    by 0x4E73C39: printf (in /lib/libc-2.9.so)                                          
==20053==    by 0x4006D1: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                  
==20053==  Uninitialised value was created by a stack allocation                                 
==20053==    at 0x400538: (within /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                   
==20053==                                                                                        
==20053== Conditional jump or move depends on uninitialised value(s)                             
==20053==    at 0x4E956F5: _IO_file_xsputn@@GLIBC_2.2.5 (in /lib/libc-2.9.so)                    
==20053==    by 0x4E6D0CC: vfprintf (in /lib/libc-2.9.so)                                        
==20053==    by 0x4E73C39: printf (in /lib/libc-2.9.so)                                          
==20053==    by 0x4006D1: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                  
==20053==  Uninitialised value was created by a stack allocation                                 
==20053==    at 0x400538: (within /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                   
==20053==                                                                                        
==20053== Conditional jump or move depends on uninitialised value(s)                             
==20053==    at 0x4E95710: _IO_file_xsputn@@GLIBC_2.2.5 (in /lib/libc-2.9.so)                    
==20053==    by 0x4E6D0CC: vfprintf (in /lib/libc-2.9.so)                                        
==20053==    by 0x4E73C39: printf (in /lib/libc-2.9.so)                                          
==20053==    by 0x4006D1: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                  
==20053==  Uninitialised value was created by a stack allocation                                 
==20053==    at 0x400538: (within /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                   
==20053==                                                                                        
==20053== Syscall param write(buf) points to uninitialised byte(s)                               
==20053==    at 0x4EE9B40: __write_nocancel (in /lib/libc-2.9.so)                                
==20053==    by 0x4E95809: _IO_file_write@@GLIBC_2.2.5 (in /lib/libc-2.9.so)                     
==20053==    by 0x4E95489: new_do_write (in /lib/libc-2.9.so)                                    
==20053==    by 0x4E957A4: _IO_do_write@@GLIBC_2.2.5 (in /lib/libc-2.9.so)                       
==20053==    by 0x4E955E5: _IO_file_xsputn@@GLIBC_2.2.5 (in /lib/libc-2.9.so)                    
==20053==    by 0x4E6A25E: vfprintf (in /lib/libc-2.9.so)                                        
==20053==    by 0x4E73C39: printf (in /lib/libc-2.9.so)                                          
==20053==    by 0x4006D1: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                  
==20053==  Address 0x401f006 is not stack'd, malloc'd or (recently) free'd                       
==20053==  Uninitialised value was created by a stack allocation                                 
==20053==    at 0x400538: (within /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                   
Hello OutOfReach! Let's get started!                                                             
---                                                                                              
---                                                                                              
---                                                                                              
==20053==                                                                                        
==20053== Invalid free() / delete / delete[]                                                     
==20053==    at 0x4C2261F: free (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)         
==20053==    by 0x4006E4: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)                  
==20053==  Address 0x7ff000460 is on thread 1's stack                                            
==20053==                                                                                        
==20053== ERROR SUMMARY: 23 errors from 6 contexts (suppressed: 9 from 1)
==20053== malloc/free: in use at exit: 10 bytes in 1 blocks.
==20053== malloc/free: 1 allocs, 1 frees, 10 bytes allocated.
==20053== For counts of detected errors, rerun with: -v
==20053== searching for pointers to 1 not-freed blocks.
==20053== checked 68,480 bytes.
==20053==
==20053==
==20053== 10 bytes in 1 blocks are definitely lost in loss record 1 of 1
==20053==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==20053==    by 0x4008E6: askPlayerName (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)
==20053==    by 0x4006AC: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)
==20053==
==20053== LEAK SUMMARY:
==20053==    definitely lost: 10 bytes in 1 blocks.
==20053==      possibly lost: 0 bytes in 0 blocks.
==20053==    still reachable: 0 bytes in 0 blocks.
==20053==         suppressed: 0 bytes in 0 blocks.

```

Here is the typedef-struct that I'm using for the player name ,etc it is located in my header file:
```

typedef struct {
                    char *name;
                    enum POINT_CHOICES symbol;
} Player;

```

main.c:
```

#include <stdio.h>
#include <stdlib.h>
#include "TicTacToe.h"

int main(void)
{
    Player user;
    int playerNameResult = askPlayerName(&user);
    if (playerNameResult == -1)
    {
        return 1;
    }
    printf("Hello %s! Let's get started!\n", user.name);
    clearBoard();
    displayBoard();
    free(user.name);
    return 0;
}

```

and player.c:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "TicTacToe.h"


int askPlayerName(Player *player)
{
    /* Not the best code in the world, but it'll do. */
    char tmpStr[21];
    printf("Enter your name: ");
    fgets(tmpStr, 20, stdin);
    tmpStr[strlen(tmpStr)-1] = '\0';    /* Gets rid of the newline character. */
    player->name = (char *) malloc(strlen(tmpStr));  /* Allocates space for the number of characters required */
    if (player->name == NULL)
    {
        PDEBUG("[player.c][Func askPlayerName] malloc returned NULL, returning...\n");
        return -1;
    }
    player->name = tmpStr;   /* Finally, we assign the input string to the player name. */
    return 1;
}

```

I am suspecting it is a problem with the askPlayerName() function, then again why would it give the free() error?
Thanks.

---

### Post by Arylon on 2009-03-01
This is the problem.```
player->name = tmpStr;   /* Finally, we assign the input string to the player name. */
``` as it is a pointer assignment.

use this to copy the string to player name.```
strcpy(player->name, tmpStr);   /* Finally, we assign the input string to the player name. */
```

---

### Post by OutOfReach on 2009-03-01
Thanks, it got rid of some errors but valgrind still reports:
```

$ valgrind ./TicTacToe                                 
==22133== Memcheck, a memory error detector.                                              
==22133== Copyright (C) 2002-2008, and GNU GPL'd, by Julian Seward et al.                 
==22133== Using LibVEX rev 1878, a library for dynamic binary translation.                
==22133== Copyright (C) 2004-2008, and GNU GPL'd, by OpenWorks LLP.                       
==22133== Using valgrind-3.4.0, a dynamic binary instrumentation framework.               
==22133== Copyright (C) 2000-2008, and GNU GPL'd, by Julian Seward et al.                 
==22133== For more details, rerun with: -v                                                
==22133==                                                                                 
Enter your name: OutOfReach                                                               
==22133== Invalid write of size 1                                                         
==22133==    at 0x4C2411F: strcpy (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==22133==    by 0x400955: askPlayerName (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)  
==22133==    by 0x4006EC: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)           
==22133==  Address 0x517b03a is 0 bytes after a block of size 10 alloc'd                  
==22133==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==22133==    by 0x400926: askPlayerName (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)  
==22133==    by 0x4006EC: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)           
==22133==                                                                                 
==22133== Invalid read of size 1                                                          
==22133==    at 0x4C240A4: strlen (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==22133==    by 0x4E6D9FD: vfprintf (in /lib/libc-2.9.so)
==22133==    by 0x4E73C39: printf (in /lib/libc-2.9.so)
==22133==    by 0x400711: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)
==22133==  Address 0x517b03a is 0 bytes after a block of size 10 alloc'd
==22133==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==22133==    by 0x400926: askPlayerName (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)
==22133==    by 0x4006EC: main (in /home/x51/Code/C/Tic-Tac-Toe/TicTacToe)
Hello OutOfReach! Let's get started!
---
---
---
==22133==
==22133== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 9 from 1)
==22133== malloc/free: in use at exit: 0 bytes in 0 blocks.
==22133== malloc/free: 1 allocs, 1 frees, 10 bytes allocated.
==22133== For counts of detected errors, rerun with: -v
==22133== All heap blocks were freed -- no leaks are possible.

```

But it looks like the free() function works now. And it still says 'Aborted' at the end of execution:
```

$ ./TicTacToe
Enter your name: OutOfReach
Hello OutOfReach! Let's get started!
---
---
---
**Aborted**

```

---

### Post by Arylon on 2009-03-01
Okay I think that's because strlen returns the number of characters in the string, but you need to allocate one extra char for the string terminator. Try this.```
    player->name = (char *) malloc(strlen(tmpStr)+1);  /* Allocates space for the number of characters plus one for the NULL terminator */
```

---

### Post by monkeyking on 2009-03-01
compile with -g
that should tell you which line is causing the problem

---

### Post by nvteighen on 2009-03-01
Arylon has it right. strlen() won't count the \0 character, so you'll be allocating one place less than needed.

---

### Post by OutOfReach on 2009-03-01
Aha, thanks guys. 
But can anyone explain to me why I need to use strcpy() like Arylon suggested instead of the pointer assignment?

---

### Post by Can+~ on 2009-03-01
> **OutOfReach said:**
> Aha, thanks guys. 
But can anyone explain to me why I need to use strcpy() like Arylon suggested instead of the pointer assignment?

Let's take a look:

```

player->name = (char *) malloc(strlen(tmpStr));
//*snip*
player->name = tmpStr;
```

First you've got:

```
player->name ---------> [Empty space of memory]
tmpStr ---------------> [Temporary space of memory that will be flushed when out of scope]
```

If you do pointer assignment, you'll get:

```
player->name ---------> [Temporary space of memory that will be flushed when out of scope]
tmpStr ---------------> [Temporary space of memory that will be flushed when out of scope]
unused ---------------> [Empty space of memory]
```

We had this discussion on another post with LeoDragonheart, the thing is that local variables die when the local scope dies, so when you do *pointer = local_memory_address, as soon as the function ends, the pointer will be pointing to a memory address that will be replaced, so you should copy the value, not the position.

Then, when you tried to free the memory address, it was already free, raising an error, and also leaving a Memory leak, as some space is still abandoned.

---

### Post by OutOfReach on 2009-03-01
> **Can+~ said:**
> Let's take a look:

```

player->name = (char *) malloc(strlen(tmpStr));
//*snip*
player->name = tmpStr;
```

First you've got:

```
player->name ---------> [Empty space of memory]
tmpStr ---------------> [Temporary space of memory that will be flushed when out of scope]
```

If you do pointer assignment, you'll get:

```
player->name ---------> [Temporary space of memory that will be flushed when out of scope]
tmpStr ---------------> [Temporary space of memory that will be flushed when out of scope]
unused ---------------> [Empty space of memory]
```

We had this discussion on another post with LeoDragonheart, the thing is that local variables die when the local scope dies, so when you do *pointer = local_memory_address, as soon as the function ends, the pointer will be pointing to a memory address that will be replaced, so you should copy the value, not the position.

Then, when you tried to free the memory address, it was already free, raising an error, and also leaving a Memory leak, as some space is still abandoned.
Oh I see now. Thanks for the clarification Can+~. :) Still getting used to this kind of stuff.

---

