---
title: "Fresh Install n Poopy Makes"
date: 2008-09-14
forum: Packaging and Compiling Programs
---

### Post by sirdonkeypunch on 2008-09-14
i freshly installed the latest stable version of ubuntu after a dire escapade that ended with me kicking windoze to the curb for the last and final time.  (btw ive always hated the doze)

in any case i got most of my packages installed i want and all that jazz... all the dependencies that i know of that i need are on here but im encountering a problem with every single instance of "make"

./configure works golden most of the time but even then sometimes theres a no go.  for instance, whilst installing xprobe2 i get an error saying that the c compiler cannot create the executables (i did the whole sudo ( err id rather just have a root acct)).  in the config.log we have 

```

gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:1709: $? = 0
configure:1711: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1714: $? = 1
configure:1737: checking for C compiler default output file name
configure:1740: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1743: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1782: error: C compiler cannot create executables

```

then for instance when i try to install thc-hydra theres a different series of errors.

```

oxycoder@The-*******:~/Installs/hydra-5.4-src$ sudo make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
pw-inspector.c:1:19: error: stdio.h: No such file or directory
pw-inspector.c:2:20: error: unistd.h: No such file or directory
pw-inspector.c:3:20: error: stdlib.h: No such file or directory
pw-inspector.c:4:20: error: string.h: No such file or directory
pw-inspector.c:5:19: error: ctype.h: No such file or directory
pw-inspector.c: In function ‘help’:
pw-inspector.c:19: warning: implicit declaration of function ‘printf’
pw-inspector.c:19: warning: incompatible implicit declaration of built-in function ‘printf’
pw-inspector.c:38: warning: implicit declaration of function ‘exit’
pw-inspector.c:38: warning: incompatible implicit declaration of built-in function ‘exit’
pw-inspector.c: In function ‘main’:
pw-inspector.c:47: error: ‘FILE’ undeclared (first use in this function)
pw-inspector.c:47: error: (Each undeclared identifier is reported only once
pw-inspector.c:47: error: for each function it appears in.)
pw-inspector.c:47: error: ‘in’ undeclared (first use in this function)
pw-inspector.c:47: error: ‘stdin’ undeclared (first use in this function)
pw-inspector.c:47: error: ‘out’ undeclared (first use in this function)
pw-inspector.c:47: error: ‘stdout’ undeclared (first use in this function)
pw-inspector.c:47: warning: left-hand operand of comma expression has no effect

```

and the above just continues on and on and on for every single link to an include that it cant seem to find.  

whenever i make an attempt to install any src i get creamed by one of these 2 forms of error messages.  ive tried decoding the config.log files when applicable and the errors from the make.... but i havent been able to find any such dependencies or includes im missing... er rather where they belong since last i knew stdio.h was common with gcc

any such help would be absolutely wonderful.  ive done my normal searches to no avail... seems like no one has these errors like i got with ubuntu.  ive been trying to get my feet back in the water after a few year hiatus from the infosec scene...and now i feel pretty melee not being able to take care of this angering (albeit most likely EASY FIX) problem.

thank you so much in advance, and you'll be seeing me on the forums a lot more.

---

