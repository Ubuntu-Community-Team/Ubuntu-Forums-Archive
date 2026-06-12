---
title: "[SOLVED] never before seen error...not sure wats wrong?"
date: 2008-02-19
forum: Programming Talk
---

### Post by S15_88 on 2008-02-19
Hey I've got a program that writes a structure to a binary file ten times and each time assigns the next structure different values for the contents of the structure.

i'm getting this error on line 12:
error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;int&#8217;

Here is my code:
[PHP]
#include <stdio.h>
#include <stdlib.h>

struct data 
{
    int count;
};

typedef struct data datatype

int main()/*LINE 12*/
{
    int i, count;
    datatype a[10]; 
    FILE * structfile;

    structfile = fopen("/home/alain/structfile.txt", "w");

    for(i=0; i<10; i++)
    {
        fwrite(a, sizeof(datatype), 1, structfile);
        
        count = i;
        datatype.count = count;
        count++;

        printf("%d\n", datatype.count);
    }    
    

    return 0;
}
[/PHP]

Not too sure whats going on, never seen this error...
Any help would be greatly appreciated, 
Thanks, Alain

---

### Post by Wybiral on 2008-02-19
You forgot a semicolon :)

---

