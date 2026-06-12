---
title: "Search C string for semicolon"
date: 2016-10-05
forum: Programming Talk
---

### Post by courtney2 on 2016-10-05
Right now I'm learning to prevent types of code injection. The scenario I chose is an example on the OWASP website where you might create a C program with root level privileges to run the "cat" system binary for in-training sysadmins. This way they don't get escalated privileges to modify or run code they don't have permissions to and can see files on the system. Obviously with root privileges they can exploit bash's use of semicolons to run multiple commands in a single line and have full root privileges to the system.

My solution is to check the input for a semicolon in argv[1] and if there is one, abort the program. My pyroblem is none of my solutions have been able to recognize a semicolon in the string and report back. Here is what I have so far:


```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>


int main(int argc, char *argv[]) {
    char cmd[100] = "/usr/bin/cat ";
    int isSemiColon;

    isSemiColon = strchr(argv[1], ";");
    printf("%d\n", isSemiColon);
    if (isSemiColon != NULL) {
        printf("Invalid input.\n");
    } else {
        strcat(cmd, argv[1]);
        system(cmd);
    }

       
    return 0;
}

```

I have the idea fully conceptualized on what to do, but I have no idea how to search a string for a semicolon (or any special character) and then have the program say "aha! One exists" so I can approve/deny the command argument. So how would I go about this?

---

### Post by spjackson on 2016-10-06
Don't you get warnings like this when you compile your program?
```

semi.c: In function &#8216;main&#8217;:
semi.c:10:35: warning: passing argument 2 of &#8216;strchr&#8217; makes integer from pointer without a cast
     isSemiColon = strchr(argv[1], ";");
                                   ^
In file included from semi.c:3:0:
/usr/include/string.h:236:14: note: expected &#8216;int&#8217; but argument is of type &#8216;char *&#8217;
 extern char *strchr (const char *__s, int __c)
              ^
semi.c:10:17: warning: assignment makes integer from pointer without a cast
     isSemiColon = strchr(argv[1], ";");
                 ^
semi.c:12:21: warning: comparison between pointer and integer
     if (isSemiColon != NULL) {
                     ^

```
These help. So...
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>


int main(int argc, char *argv[]) {
    char cmd[100] = "/usr/bin/cat ";
    int isSemiColon;

    isSemiColon = (strchr(argv[1], ';') != NULL);
    printf("%d\n", isSemiColon);
    if (isSemiColon != 0) {
        printf("Invalid input.\n");
    } else {
        strcat(cmd, argv[1]); // DANGER. You need to prevent buffer overflow.
        system(cmd);
    }

       
    return 0;
}

```
Also note that it is valid for a filename to contain a semicolon. I don't know whether dealing with that is beyond the scope of your requirement.

---

### Post by courtney2 on 2016-10-06
Yes, I did get those compile errors, and your code fixes those errors. That is almost identical to another piece of code I tried earlier, and I have the same problem. Even when I input a semicolon into my argv[1], it still keeps isSemiColon = 0. Here's my output now wih the code you shared:

./program "filename.txt; ls"
Result: isSemiColon = 1 and "Invalid input." is printed

./program filename.txt; ls
both commands execute in bash. Perhaps placing quotation marks around argv[1] would help, but that might open up another code exploit.

---

### Post by spjackson on 2016-10-06
> **courtney2 said:**
> 
./program "filename.txt; ls"
Result: isSemiColon = 1 and "Invalid input." is printed

That is the correct result.
> 
./program filename.txt; ls
both commands execute in bash.
That is also the correct result. In this case, argv[1] is filename.txt and "; ls" are processed by the shell in which you type the command. Your program never sees "; ls".

---

### Post by steeldriver on 2016-10-06
*n/m ninja'd*

---

### Post by courtney2 on 2016-10-06
Aha! I see that now. I ran the program in gdb and it did in fact not see the "; ls". That fixes my problem then thank you!

---

### Post by dwhitney67 on 2016-10-08
Here's an exploit that was not covered in the previous responses.  Try running your program *without* any arguments (i.e. no filename).

Notice how the program generates a segmentation violation.

Also, do not use strcat().  Use strncat() instead.

---

