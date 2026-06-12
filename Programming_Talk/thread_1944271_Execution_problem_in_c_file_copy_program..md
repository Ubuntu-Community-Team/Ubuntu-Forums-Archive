---
title: "Execution problem in c file copy program."
date: 2012-03-21
forum: Programming Talk
---

### Post by sneha09 on 2012-03-21
hi..i have just joined this forum.My problem is with C program.I am working with 'bloodshed Dev 4.9 9.2 software'  on windows xp. i have written  this program to "read a text file" (stored in disk c).After compiling(with no error),execution is not being done. I am Beginner in C,so please help! 
The moment i click on run,it[ ]("http://happening.it/")just shows the black  screen (where execution takes place)for half second & returns back to the program. Is there any problem in my logic?
 Program is as follows:
```

#include <stdio.h>
# include<stdlib.h>
int  main()
{ 
     
     FILE *fp;
     char s[80];
     fp=fopen("Untitled1.TXT","r");
     if ( fp==NULL)
     {
          puts("cant open");
          exit(1);
                  }           
 while (fgets (s,79,fp) != NULL)
 printf("%S",s);
fclose(fp);
}
```

---

### Post by Doug S on 2012-03-21
Shouldn't the "%S" in your printf be lower case?
Your program works for me after I make that change.
 
Welcome to Ubuntu forums.

---

### Post by 3rdalbum on 2012-03-21
You might get better replies if the post gets moved to the Programming and Development forum. Questions about programming are not really appropriate for Absolute Beginner Talk.

This doesn't affect the execution of the program, but on Linux you don't need the ".txt" extension. Linux is smart enough to be able to see that this is a text file.

You are using Ubuntu, right? You mentioned Win XP as your development OS but I just wanted to check whether you're specifically having trouble running the program on Ubuntu but not Windows. This forum is for Ubuntu users.

---

### Post by lisati on 2012-03-21
*Thread moved to **Programming Talk**.*
Just a suggestion: when testing a program using an IDE you might want to add a few lines of code at the end to prompt the user to press a key and then wait for them to do so.

---

### Post by PaulM1985 on 2012-03-21
As lisati said, you can prompt the user to press a key before the program ends and that way the "black screen" (command prompt) will stay visible until you press a key.

Alternatively, you can run your program from inside the command prompt and then the window will always stay open.

Paul

---

### Post by CynicRus on 2012-03-21
```

#include <stdio.h>
#include <io.h>
int main(int argc, char *argv[])
{
FILE * in, * out;
int  n;
char buf [512];
in=fopen(argv[1],"rb");
out=fopen(argv[2],"w");
while ((n = read(fileno(in), buf, sizeof buf)) > 0)
  {
    write(fileno(out), buf, n);  
  }
  return 0;
}

```symply file-copy program in C for windows. If i understand problem.

---

### Post by sneha09 on 2012-03-23
thanks for letting me know!! I didn't know much about ubuntu...so i posted it here. I am done with that problem now.

---

### Post by sneha09 on 2012-03-23
Is this forum not for Window users??????? Because when i was searching some links for my problem,than i found this Forum. So i am not much aware about it....please let me know.

---

### Post by PaulW2U on 2012-03-23
> **sneha09 said:**
> Is this forum not for Window users??????? Because when i was searching some links for my problem,than i found this Forum. So i am not much aware about it....please let me know.

This forum is primarily for the users of [Ubuntu]("http://www.ubuntu.com/") and its derivatives. Some of your problems might be able to be discussed here but anything specific to Windows is best dealt with elsewhere. Hope that helps.

---

### Post by sneha09 on 2012-03-23
ok thanks !!!!

---

