---
title: "[ C++ ] Runtime error - std::out_of_range .. Any ideas ?"
date: 2009-08-17
forum: Programming Talk
---

### Post by credobyte on 2009-08-17
Ok, I'm trying to read a file which contains the following line/-s and cut off the "PATH: " part:
```
PATH: /usr/bin
PATH: /usr/sbin
```C++ code ( the part which causes this error ):
```
getline(configfile, line);
string strp = line.substr(5, line.length()); 
envtable.push_back(strp);
```Error at runtime ( compilation went smoothly ):
```
terminate called after throwing an instance of 'std::out_of_range'
  what():  basic_string::substr
Aborted
```What could be the reason and how do I fix it ?

---

### Post by Zugzwang on 2009-08-17
The code you posted should work if used in isolation. Use valgrind ("valgrind --tool=memcheck ./your_program") to check if something already goes wrong earlier in the execution of your program.

---

### Post by credobyte on 2009-08-17
> **Zugzwang said:**
> The code you posted should work if used in isolation. Use valgrind ("valgrind --tool=memcheck ./your_program") to check if something already goes wrong earlier in the execution of your program.

```
==24673== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
==24673== malloc/free: in use at exit: 13 bytes in 1 blocks.
==24673== malloc/free: 17 allocs, 16 frees, 12,847 bytes allocated.

==24673== LEAK SUMMARY:
==24673==    definitely lost: 0 bytes in 0 blocks.
==24673==      possibly lost: 13 bytes in 1 blocks.
==24673==    still reachable: 0 bytes in 0 blocks.
==24673==         suppressed: 0 bytes in 0 blocks.
```

Weird that .. it works when compiled with Win32 g++ ( tried on VirtualBox ). Any ideas ?

[COLOR=Gray]P.S. - problem temporary solved by replacing substr with erase.[/COLOR]

---

### Post by colau on 2009-08-17
> **credobyte said:**
> Ok, I'm trying to read a file which contains the following line/-s and cut off the "PATH: " part:
```
PATH: /usr/bin
PATH: /usr/sbin
```C++ code ( the part which causes this error ):
```
getline(configfile, line);
string strp = line.substr(5, line.length()); 
envtable.push_back(strp);
```Error at runtime ( compilation went smoothly ):
```
terminate called after throwing an instance of 'std::out_of_range'
  what():  basic_string::substr
Aborted
```What could be the reason and how do I fix it ?
Can you post the complete code?

---

### Post by credobyte on 2009-08-17
> **colau said:**
> Can you post the complete code?

[http://ubuntuforums.org/showthread.php?t=1240305&page=2](http://ubuntuforums.org/showthread.php?t=1240305&page=2) :lolflag:

---

### Post by colau on 2009-08-17
> **credobyte said:**
> [http://ubuntuforums.org/showthread.php?t=1240305&page=2](http://ubuntuforums.org/showthread.php?t=1240305&page=2) :lolflag:
Hello,
Building with Netbeans 6.7 ran your code and the output is a **shell**.

---

### Post by credobyte on 2009-08-17
> **colau said:**
> Hello,
I build your code with Netbeans 6.7 and ran this and the output is a **shell**.

Linked code is a modified version of what I had ( already fixed by replacing substr with erase ). Original still gives me an error, no matter what strings and substrings I'm trying to obtain.

Even the following example fails:
```
string test = "two words";
string sub = test.substr(3, test.length());
```

Could it be a bug/corrupted installation of my build-essential ( g++ ) package ?

---

### Post by colau on 2009-08-17
> **credobyte said:**
> Could it be a bug/corrupted installation of my build-essential ( g++ ) package ?
No.
May be, your implementation of substr function is buggy at runtime.
Can you post:
```

dpkg -l | grep g++
dpkg -l | grep essential

```

---

### Post by credobyte on 2009-08-17
> **colau said:**
> No.
May be, your implementation of **substr function is buggy at runtime**.
Can you post:
```

dpkg -l | grep g++
dpkg -l | grep essential

```
Exactly!

```
dainis@ubuntu:~$ dpkg -l | grep g++
ii  g++                                        4:4.3.3-1ubuntu1                     The GNU C++ compiler
ii  g++-4.3                                    4.3.3-5ubuntu4                       The GNU C++ compiler
```

```
dainis@ubuntu:~$ dpkg -l | grep build-essential
ii  build-essential                            11.4 
```

---

### Post by johnl on 2009-08-17
Hi,

The problem is this:
```

string strp = line.substr(5, line.length()); 

```

Check your file.  I bet that there is a blank line at the end.  If the first argument (the index) is greater than the length of the string, you will see this exception thrown.

Hope this helps.

---

