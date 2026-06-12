---
title: "Makefile test fails"
date: 2011-02-19
forum: Programming Talk
---

### Post by teaquack on 2011-02-19
I'm having problems with makefile. Basically if I just run my program like ./myshell, everything works as it should in it. However, from makefile it starts failing. This is my makefile:

myshell: myshell.o
myshell.o: myshell.c
clean:
        rm -f *.o
test: myshell
        pwd
        ls &
        ps

This is the output:
pwd
/home/foo
ls &
ps
enter  input.txt  makefile  myshell  myshell.c    myshell.o
  PID TTY          TIME CMD
 5472 pts/0    00:00:00 bash
 8671 pts/0    00:00:00 make
 8675 pts/0    00:00:00 ps

This is what the output should be (if I run ./myshell and type in commands myself):
pwd
/home/foo
ls &
Started job 8814
enter  input.txt  makefile  myshell  myshell.c    myshell.o
ps
  PID TTY          TIME CMD
 5472 pts/0    00:00:00 bash
 8810 pts/0    00:00:00 myshell
 8814 pts/0    00:00:00 ls <defunct>
 8820 pts/0    00:00:00 ps
Zombie with pid 8814 status 0 is reaped.

Please help. :|

---

### Post by Vox754 on 2011-02-20
> **teaquack said:**
> I'm having problems with makefile. Basically if I just run my program like ./myshell, everything works as it should in it. However, from makefile it starts failing. This is my makefile:

...

It's not clear what you are trying to do. Do you require assistance compiling, or only running the program?

Use code tags so the code is nicely formatted. Is this the makefile?
```

myshell: myshell.o
myshell.o: myshell.c
clean:
	rm -f *.o
test: myshell
	pwd
	ls &
	ps

```

It compiles the program using implicit rules. The "test" rule does not run your program, it runs "pwd", "ls &", and "ps", each in a separate shell.

Perhaps this is what you want
```

test: myshell
	./myshell ; \
	pwd ; \
	ls & ; \
	ps

```

---

