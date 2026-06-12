---
title: "Could not find so lib"
date: 2011-10-11
forum: Packaging and Compiling Programs
---

### Post by huangyingw on 2011-10-11
Hello,
   I am writing this makefile to demonstrate the compiling and loading of dynamic lib. And I met the following problem.
```
huangyingw@desktop:~/myproject/git/cplusplus/linux/fundamental/makefile$ cat makefile 
main:
	gcc -shared max.c -o libmax.so
	export LD_LIBRARY_PATH=/media/volgrp/myproject/git/cplusplus/linux/fundamental/makefile/:${LD_LIBRARY_PATH}
	sudo ldconfig
	gcc -lmax  test_so.c -o test_so

```
   The output of make command is as bellow:
```
huangyingw@desktop:~/myproject/git/cplusplus/linux/fundamental/makefile$ make
gcc -shared max.c -o libmax.so
export LD_LIBRARY_PATH=:/media/volgrp/myproject/git/cplusplus/linux/fundamental/makefile:/media/volgrp/myproject/git/cplusplus/linux/fundamental/makefile
sudo ldconfig
gcc -lmax  test_so.c -o test_so
/usr/bin/ld: cannot find -lmax
collect2: ld returned 1 exit status
make: *** [main] Error 1
```
I am sure that the libmax.so is available:
```
huangyingw@desktop:~/myproject/git/cplusplus/linux/fundamental/makefile$ ls /media/volgrp/myproject/git/cplusplus/linux/fundamental/makefile/|grep libmax.so
libmax.so
```

---

### Post by Bachstelze on 2011-10-11
Try with -shared on that line too.

---

### Post by MadCow108 on 2011-10-11
you have to use the -L flag, LD_LIBRARY_PATH is a runtime flag no compile time flag.
```
gcc -L/media/volgrp/myproject/git/cplusplus/linux/fundamental/makefile/ test_so.c -o test_so -lmax
```
also the -lmax belongs to the end of the command line.

---

### Post by BillD1 on 2011-10-11
Here's a more complete example (not using a makefile, just the commands):

```

% $ ls -1
max.c
test_so.c
$ cat max.c

int getIntValue(float v) {
    return (int) v;
}

$ cat test_so.c

extern int getIntValue(float);

int main(int argc, const char* argv[]) {
    float fv = 2.5;
    int iv = getIntValue(fv);
    printf("fv = %f  iv = %d\n", fv, iv);
}
$ gcc -c max.c -o max.o                 # compile max.c to produce max.o
$ gcc -shared max.o -o libmax.so   # create libmax.so shared library containing max.o
$ gcc -c test_so.c -o test_so.o        # compile test program test_so.c to produce test_so.o
$ ls -1
libmax.so
max.c
max.o
test_so.c
test_so.o
$ gcc -lmax  test_so.o -o test_so     # link test program test_so FAILS, no -L argument
/usr/bin/ld: cannot find -lmax
collect2: ld returned 1 exit status
$ gcc -L. -lmax  test_so.o -o test_so  # link test program test_so with -L. Succeeds
$ ls -1
libmax.so
max.c
max.o
test_so
test_so.c
test_so.o
$ ./test_so                    # No LD_LIBRARY_PATH set
./test_so: error while loading shared libraries: libmax.so: cannot open shared object file: No such file or directory
$ export LD_LIBRARY_PATH=.    # set LD_LIBRARY_PATH (to current directory or full path)
$ ./test_so                                 # successful execution
fv = 2.500000  iv = 2

```This example used '.', the current directory for both the -L argument in linking the test program and in specifying LD_LIBRARY_PATH. Usually you would see a full path to the directory in question.

To emphasize what MadCow108 replied, LD_LIBRARY_PATH is used at runtime, not at linking.

---

### Post by huangyingw on 2011-10-12
> **MadCow108 said:**
> you have to use the -L flag, LD_LIBRARY_PATH is a runtime flag no compile time flag.
```
gcc -L/media/volgrp/myproject/git/cplusplus/linux/fundamental/makefile/ test_so.c -o test_so -lmax
```
also the -lmax belongs to the end of the command line.
Thank you for guidance.

---

### Post by huangyingw on 2011-10-12
> **BillD1 said:**
> Here's a more complete example (not using a makefile, just the commands):

```

% $ ls -1
max.c
test_so.c
$ cat max.c

int getIntValue(float v) {
    return (int) v;
}

$ cat test_so.c

extern int getIntValue(float);

int main(int argc, const char* argv[]) {
    float fv = 2.5;
    int iv = getIntValue(fv);
    printf("fv = %f  iv = %d\n", fv, iv);
}
$ gcc -c max.c -o max.o                 # compile max.c to produce max.o
$ gcc -shared max.o -o libmax.so   # create libmax.so shared library containing max.o
$ gcc -c test_so.c -o test_so.o        # compile test program test_so.c to produce test_so.o
$ ls -1
libmax.so
max.c
max.o
test_so.c
test_so.o
$ gcc -lmax  test_so.o -o test_so     # link test program test_so FAILS, no -L argument
/usr/bin/ld: cannot find -lmax
collect2: ld returned 1 exit status
$ gcc -L. -lmax  test_so.o -o test_so  # link test program test_so with -L. Succeeds
$ ls -1
libmax.so
max.c
max.o
test_so
test_so.c
test_so.o
$ ./test_so                    # No LD_LIBRARY_PATH set
./test_so: error while loading shared libraries: libmax.so: cannot open shared object file: No such file or directory
$ export LD_LIBRARY_PATH=.    # set LD_LIBRARY_PATH (to current directory or full path)
$ ./test_so                                 # successful execution
fv = 2.500000  iv = 2

```This example used '.', the current directory for both the -L argument in linking the test program and in specifying LD_LIBRARY_PATH. Usually you would see a full path to the directory in question.

To emphasize what MadCow108 replied, LD_LIBRARY_PATH is used at runtime, not at linking.
Great thanks for your guidance step by step.

---

