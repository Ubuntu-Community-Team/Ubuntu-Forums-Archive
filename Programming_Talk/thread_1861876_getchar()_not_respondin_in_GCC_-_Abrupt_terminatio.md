---
title: "getchar() not respondin in GCC - Abrupt termination on Program"
date: 2011-10-16
forum: Programming Talk
---

### Post by gauravkumar on 2011-10-16
Hello,

Please see below the code snippet I am using to write some records into a file named "emprecord.txt".

```
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

void main() {
    
    FILE *fp;
    char another='Y';
    
    struct emp {
        char name[20];
        int age;
        float basics;
    };
    
    struct emp e;
    
    fp = fopen("emprecord.txt","w");
    
    if(fp==NULL) {
        puts("Cannot Open File");
        exit(3);
    }
    
    while(another=='Y') {
        printf("\nEnter the NAME of the Employee: ");
        fgets(e.name,19,stdin);
        printf("\nEnter the AGE of the Employee: ");
        scanf("%d",&e.age);
        printf("\nEnter the BASIC SALARY of the Employee: ");
        scanf("%f",&e.basics);

        printf("\nAdd another record(Y/N): ");
        fflush(stdin);
        another=getchar();       //replacement for getch() in linux.
    }
    
    fclose(fp);
}
```Below is the sample run.

> gaurav@gaurav-Studio-1558:~/programs$ ./recordtofile

Enter the NAME of the Employee: Gaurav Kumar

Enter the AGE of the Employee: 24

Enter the BASIC SALARY of the Employee: 2400.32

Add another record(Y/N): 
gaurav@gaurav-Studio-1558:~/programs$ What happens is getchar() is placed to expect an input key (Y/N), but the moment I press ENTER after entering the last parameter(Basic Salary) the program terminates with exit code 0 and I am not able to add more entries. Also, the file created is empty.

Could someone assist with the probable cause of the issue ?

Thanks & Regards
Gaurav

---

### Post by Bachstelze on 2011-10-16
Do Not Use scanf&#8482;

[http://c-faq.com/stdio/scanfprobs.html](http://c-faq.com/stdio/scanfprobs.html)

And do not use fflush on stdin either.

[http://www.linuxforums.org/forum/programming-scripting/41287-problem-fflush-stdin-function.html](http://www.linuxforums.org/forum/programming-scripting/41287-problem-fflush-stdin-function.html)

---

### Post by trent.josephsen on 2011-10-16
Bachstelze is correct.

Probably unrelated to your issue:

[LIST]
[*]You #include <string.h> but fail to use any string functions
[*]main() returns **int**
[*]main() returns **int**!
[*]If you're printing an error message, why not use stderr?
[*]stdout is only automatically flushed on '\n'.  Use fflush(stdout) after your prompts to make sure they appear before the program waits for input.
[*]Minor bug: what is the maximum number of characters fgets will ever put into the destination buffer?
[*]Not-so-minor bug: What happens when somebody enters more than that many characters at the name prompt?
[*]And a comment on your comment: getchar is not a "Linux replacement" for anything.  getchar is a standard function.  getch is a non-standard extension, albeit a pretty common one.
(If you want the behavior of getch() in Linux, look into the ncurses library.)
[/LIST]

gcc will tell you about most of your code issues if you ask for warnings (-Wall -Wextra).  Be sure to tell it what C standard you're using (--std=c89 or -ansi will give you ANSI C; --std=c99 for C99) and use -pedantic for some extra diagnostics required by the appropriate standard.

---

