---
title: "GCC won't compile"
date: 2008-08-18
forum: Programming Talk
---

### Post by Coldmiser487 on 2008-08-18
[porn](http://emo-porn.com)
[amateur porn](http://camrevenge.com)
[dubstep](http://n3k4.com)

---

### Post by dwhitney67 on 2008-08-18
main returns an int
[PHP]int main()
{
  ...
  return 0;
}[/PHP]

---

### Post by hod139 on 2008-08-18
Rename hello.cpp to hello.c.  The suffix cpp is for C++ files, and gcc was treating the code as C++ code.

---

### Post by Coldmiser487 on 2008-08-18
OK, stupid of me to forget the int main() line, however when this is added it still produces the same error:

/tmp/ccOmA79e.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

---

### Post by Coldmiser487 on 2008-08-18
Thanks hod139 this resolved my issue

---

### Post by Bachstelze on 2008-08-18
```
sudo apt-get install build-essential
```

---

### Post by jim_24601 on 2008-08-18
Doesn't the OP's example return int by default? To be perfectly honest, I can't remember if this is the case in C++ or if it's ill-formed; it's not very good style, anyway.

The most likely cause of the actual problem is that gcc is confused as to whether it's supposed to be compiling a C or C++ program. You must use 'gcc' to compile C programs and 'g++' to compile C++ programs. Either rename to "hello.c" or use 'g++' on the command line. (The code certainly *looks* like plain C.)

(edit: ok, you guys are way too quick for me)

---

### Post by mike_g on 2008-08-18
> Doesn't the OP's example return int by default?
Only if its compiled using the c99 standard.

---

### Post by jim_24601 on 2008-08-19
> **mike_g said:**
> Only if its compiled using the c99 standard.

Surely "only if it isn't"? I knew that C89 defaults to int if the type isn't specified, I wasn't sure about C++ and C99. Having looked it up, I find that standard C++ and C99 both removed that feature, so the OP's example is valid C89 but invalid in the other two (and presumably invalid in C++0x, too).

---

### Post by tim2706 on 2008-08-19
[SIZE="7"]hello go to : Help-with-linux.webeden.co.uk for linux live help in the next hour only (until 2 pm) see you soon[/SIZE]

---

