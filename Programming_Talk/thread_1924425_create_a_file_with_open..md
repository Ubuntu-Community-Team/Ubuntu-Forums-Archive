---
title: "create a file with open."
date: 2012-02-12
forum: Programming Talk
---

### Post by conradin on 2012-02-12
Hi everyone!
I want to write a simple program in C that creates  a file with 775 permissions, using the open command. Im not sure which mode arguments I need to make that happen with open. 
Can someone help me  out?
heres what I have:


```
#include <sys/types.h>   //Specified in man 2 open
#include <stdlib.h>
#include <errno.h>  	 //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>

int main(int argc, char ** argv){ 
  FILE *fp;
  fp = open("argv[1]", "O_CREAT", "MODE???");

  close(fp);  /* Close the file */
return 0;
}

```

---

### Post by gateway67 on 2012-02-12
You should run this command:
```

man 2 open

```One thing you might notice is that open() returns an int value, which is meant to represent a file descriptor.  If you want to work with a FILE pointer, then you should use fopen(), fclose(), etc.

Typically open() is used for low-level I/O.  For normal stuff, like reading or creating a file, fopen() is used.


P.S.  If you choose to use fopen() to create the file, you can subsequently use chmod() to set its permission mode.  See "man 2 chmod" for details on this particular function.

---

### Post by conradin on 2012-02-13
yeah, Im on man open(2), Im confused about what to do with multiple modes for open.
```
#include <sys/types.h>   //Specified in man 2 open
#include <stdlib.h>
#include <errno.h>  	 //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>
 
int main(int argc, char *argv[]){
	int fd;
	fd = open(argv[1], O_CREAT, S_IRWXU | S_IRWXG | S_IROTH | S_IXOTH);
 
    return 0;
}
```
gives me errors. open is what I want, eventually, I will develop device drivers. That really doesn't matter though. 
heres my errors, this thing is acting like its never seen the open modes before...
```
gcc -Wall -o "createFile775" "createFile775.c" (in directory: /home/h/Desktop/cpro)
createFile775.c: In function ‘main’:
createFile775.c:12: error: ‘S_IRWXU’ undeclared (first use in this function)
createFile775.c:12: error: (Each undeclared identifier is reported only once
createFile775.c:12: error: for each function it appears in.)
createFile775.c:12: error: ‘S_IRWXG’ undeclared (first use in this function)
createFile775.c:12: error: ‘S_IROTH’ undeclared (first use in this function)
createFile775.c:12: error: ‘S_IXOTH’ undeclared (first use in this function)
Compilation failed.

```

---

### Post by gateway67 on 2012-02-13
You need to include <sys/stat.h> to obtain those macro definitions (re-read the man page for open() a little more carefully).

---

### Post by conradin on 2012-02-13
```
$ ll balls3
----r-S--- 1 h h 0 2012-02-13 06:29 balls3
$ ./createFile775  balls4
$ ll balls4
--wxr-S--- 1 h h 0 2012-02-13 06:30 balls4*
```
When I omit the mode flags, I get a file with the permissions of balls3.
When I put anything in quotes for the mode I get permissions consistent with balls4

---

### Post by gateway67 on 2012-02-13
Check the 'umask' setting in your working environment.
```

umask

```
In my working environment it is set to 0002.

Btw, from the code you posted earlier, I got the following to work:
```

#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
    int fd = open(argv[1], O_CREAT, S_IRWXU | S_IRWXG | S_IROTH | S_IXOTH);

    close(fd);

    return 0;
}

```
The file that is created has permissions 775.

---

### Post by conradin on 2012-02-13
How do i set my umasq? is that in the bashrc?

---

### Post by conradin on 2012-02-13
Thank you everyone! I got it!
```
#include <sys/types.h>   //Specified in man 2 open
#include <sys/stat.h>
#include <stdlib.h>
#include <errno.h>  	 //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>
 
int main(int argc, char *argv[]){
	int fd;
	fd = open(argv[1], O_CREAT, S_IRWXU | S_IRWXG | S_IROTH | S_IXOTH);
			
     return 0;
}
```

---

