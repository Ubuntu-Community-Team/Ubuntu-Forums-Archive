---
title: "C - fopen() user specified filename...?"
date: 2007-11-15
forum: Programming Talk
---

### Post by S15_88 on 2007-11-15
I'm writing a program which uses a ceaser shift to cipher a block of text, programming assignment for school.   the user can write a block of text either in the console and cipher it, or i gave them the option of fetching a text file.  the only problem is they will create and name that text file, so i need them to input the filename.

I am unsure as to how to use fopen() to fetch that specific file:
```

 printf("Please Enter The Name Of The File You Would Like To Fetch\n");
 scanf("%s", filename);
 userfile = fopen("WHAT-THE-USER-JUST-ENTERED.txt", "r");

```

i know how to do it in java:
```

fileName = text_areaOne.getText() + ".txt"; 

		

BufferedReader infile = new BufferedReader(newFileReader(fileName));

```

Any help would be greatly appreciated!
Thanks, Alain!

---

### Post by j_g on 2007-11-15
I presume filename is declared as:

char filename[PATH_MAX];

Um...

```
userfile = fopen(filename, "r");
```

You may want to review how scanf works. The question you asked really surprised me in its simplicity. So it may be best to review some fundamentals before you move on to more advanced topics, and then get really lost.

---

### Post by smartbei on 2007-11-15
If you want to append .txt to filename, look up the string.h functions.

---

### Post by LaRoza on 2007-11-15
Depending on the use of the program, you might want to have the file specificied as a command line argument, like many other programs.

---

### Post by Damanther on 2007-11-15
If you are wanted the user to input the file name without the .txt extension, then add it after the fact you will have to

scanf("%s", &filename);
strcat(&filename, ".txt");

fd = fopen(filename, "r");

---

### Post by LaRoza on 2007-11-15
> **Damanther said:**
> If you are wanted the user to input the file name without the .txt extension, then add it after the fact you will have to

scanf("%s", &filename);
strcat(&filename, ".txt");

fd = fopen(filename, "r");

If the "filename" is a character array, which is should be, you don't (and shouldn't have) the "&" symbol.

[php]
#include <stdio.h>
int main(int argc,char ** argv)
{
    char filename[20];
    FILE * userfile = 0;
    printf("Please Enter The Name Of The File You Would Like To Fetch\n");
    scanf("%s", filename);
    userfile = fopen(filename, "r");
    if (userfile)
    {
        /*Work on file here*/
    }
    else
    {
        /*Give error, create the file, ask again, etc...*/    
    }
    return 0;
}
[/php]

I don't recommend adding the file extension, but if you do, remember not to overflow the buffer.

---

### Post by Damanther on 2007-12-26
Ick your right. Thats what I get for cut and pasting without double-checking.

---

### Post by LaRoza on 2007-12-26
I hope you weren't brewing over this for over a month.

---

