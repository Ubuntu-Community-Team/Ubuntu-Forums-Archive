---
title: "Character Arrays in C"
date: 2008-03-29
forum: Programming Talk
---

### Post by raddmadd on 2008-03-29
I understand simple character arrays; however I do not understand this code example in the K & R book:

```

#include <stdio.h>
#define MAXLINE 1000    /* maximum input line length */

int getline(char line[], int maxline);
void copy(char to[], char from[]);

/* print the longest input  line */
main()
{
    int len;             /* current line length */
    int max;             /* maximum length seen so far */
    char line[MAXLINE];     /* current input line */
    char longest[MAXLINE];  /* longest line saved here */
    max = 0;
    while ((len = getline(line, MAXLINE)) > 0)
        if (len > max) {
             max = len;
             copy(longest, line);
        }
    if (max > 0) /* there was a line */
        printf("%s", longest);
    return 0;
}

/* getline: read a line into s, return length   */
int getline(char s[],int lim)
{
    int c, i;
    for (i=0; i < lim-1 && (c=getchar())!=EOF && c!='\n'; ++i)
        s[i] = c;
    if (c == '\n') {
        s[i] = c;
        ++i;
    }
    s[i] = '\0';
    return i;
}

/* copy: copy 'from' into 'to'; assume to is big enough */
void copy(char to[], char from[])
{
    int i;
    i = 0;
    while ((to[i] = from[i]) != '\0')
        ++i;
}

```

As the comment before main says, the program outputs the longest string.  However, a few things I don't understand. 

 When I declare an array, I cannot leave the array subscript empty (int blah[]) I have to specify the subscript.  However in this program, the parameters for getline and copy have arrays with an empty subscript.  I don't understand this and I don't understand using the array line and longest.  They are being used as arguments without specifying which subscript is being used.  

I may not be clear on what I do not understand, but I would like someone to explain how line and longest are being passed to the functions.

Thank you in advance.

---

### Post by LaRoza on 2008-03-29
I think you haven't gotten to the part where the relationships between arrays and pointers is explained.

The program you posted makes use of that fact, and an array name is a pointer.

---

