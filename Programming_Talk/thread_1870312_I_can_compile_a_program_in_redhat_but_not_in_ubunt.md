---
title: "I can compile a program in redhat but not in ubuntu"
date: 2011-10-27
forum: Programming Talk
---

### Post by shevin on 2011-10-27
guys
I wrote a code for an assignment, I can compile it on the university's redhat server
but it gives me this error on ubuntu


g++ -lpthread telephoneGame.cpp -o telephoneGame
```
/tmp/ccQBQKsY.o: In function `main':
telephoneGame.cpp:(.text+0x27a): undefined reference to `pthread_create'
telephoneGame.cpp:(.text+0x2b2): undefined reference to `pthread_join'
collect2: ld returned 1 exit status

```

---

### Post by cguy on 2011-10-27
You need to link the pthread library. Add "-lpthread" to your "gcc" command.

---

### Post by Zugzwang on 2011-10-27
> **shevin said:**
> g++ -lpthread telephoneGame.cpp -o telephoneGame


Try putting "-lpthread" at the end of the line - the order of parameters might be important here.

---

### Post by shevin on 2011-10-27
> **Zugzwang said:**
> Try putting "-lpthread" at the end of the line - the order of parameters might be important here.

still no luck ! the thing is, the gcc on both computers are same versions but one is redhat and one is ubuntu ...whats wrong ?

---

### Post by karlson on 2011-10-27
> **shevin said:**
> still no luck ! the thing is, the gcc on both computers are same versions but one is redhat and one is ubuntu ...whats wrong ?

Try running 
```

gcc -pthread TelephoneGame.cpp -o TelephoneGame -lpthread

```

You may have to compare gcc specs files to find the differences between the two.

---

### Post by MadCow108 on 2011-10-27
placing -lpthread at the end or using -pthread must solve the issue.
see e.g. for a similar problem
[http://ubuntuforums.org/showthread.php?t=1869838](http://ubuntuforums.org/showthread.php?t=1869838)

caused by ld --as-needed now default in ubuntu 11.10

---

### Post by shevin on 2011-10-31
> **MadCow108 said:**
> placing -lpthread at the end or using -pthread must solve the issue.
see e.g. for a similar problem
[http://ubuntuforums.org/showthread.php?t=1869838](http://ubuntuforums.org/showthread.php?t=1869838)

caused by ld --as-needed now default in ubuntu 11.10

if u looka t my first post , I had put -lpthread , but still in redhat it compiled very well and not in ubuntu ...anyway I changed my code , and now my new code compiles in both

---

### Post by MadCow108 on 2011-10-31
> **shevin said:**
> if u looka t my first post , I had put -lpthread , but still in redhat it compiled very well and not in ubuntu ...anyway I changed my code , and now my new code compiles in both

your first post is _wrong_, you must put the -lpthread to the end of the command line (or use -pthread).
yes that is important in ubuntu 11.10.

---

### Post by shevin on 2011-11-20
> **MadCow108 said:**
> your first post is _wrong_, you must put the -lpthread to the end of the command line (or use -pthread).
yes that is important in ubuntu 11.10.


I tried with both -lpthread and -pthread , in the begining, in the end, alone or with combination of both .
 and still get these errors in ubuntu :

> 
telephoneGame.cpp: In member function ‘void Sentence::imperfectlyTransmit()’:
telephoneGame.cpp:126:26: error: ‘rand’ was not declared in this scope
telephoneGame.cpp: In function ‘void* child(void*)’:
telephoneGame.cpp:289:17: error: ‘rand’ was not declared in this scope
telephoneGame.cpp: In function ‘int main(int, const char**)’:
telephoneGame.cpp:353:35: error: ‘atoi’ was not declared in this scope
telephoneGame.cpp:360:41: error: ‘atoi’ was not declared in this scope
telephoneGame.cpp:363:22: error: ‘srand’ was not declared in this scope
telephoneGame.cpp:396:12: error: ‘EXIT_SUCCESS’ was not declared in this scope




but in redhat it compiles beautifuly !


what is wrong with ubuntu ?

---

### Post by Bachstelze on 2011-11-20
Nothing is wrong with Ubuntu. Something is wrong with your posts, though: we need the ***_entire_*** error message, not just bits and pieces.

---

### Post by gateway67 on 2011-11-20
> **shevin said:**
> I tried with both -lpthread and -pthread , in the begining, in the end, alone or with combination of both .
 and still get these errors in ubuntu :

Include stdlib.h in your code.

---

