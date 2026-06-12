---
title: "[SOLVED] printf...integer array"
date: 2008-02-18
forum: Programming Talk
---

### Post by S15_88 on 2008-02-18
Having a total mental block!  I've got a program that writes an integer array of 100 containing 1 to 100 to a binary file using fwrite().  then i have to read the file into another array and  print the contents.  

i can;t for the life of me remember how to print the contents of an array!
here's my code:
[PHP]
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i, a1[100], a2[100];
    i=0;

    FILE * file;
    file = fopen("file.txt", "w");

    for(i=0; i<0; i++)
    {
        a1[i] = i;
        
    }
    fwrite(a1, sizeof(int), 100, file);
    fclose(file);

    file = fopen("file.txt", "r");
    fread(a2, sizeof(int), 100, file);    

    /*Print Contents Here*/
    
    fclose(file);

    return 0;
}
[/PHP]

if i do:

for(i=0;i<100;i++)
{
    printf("%d\n", a2[i]);
}

i'm printing the value of i at that point...not the value of a2 at point i

i'm just confused haha ugh. any help would be greatly appreciated

Thanks, Alain

---

### Post by yabbadabbadont on 2008-02-18
Your code to print the values is correct.  The problem is that you have a bug in the first "for" loop.
```
    for(i=0; i<0; i++)
    {
        a1[i] = i;
        
    }

```
Fix that and you will fix the other.  ;)

---

### Post by PaulFr on 2008-02-18
1. First you have a problem in your first for loop. Try changing this ```
[COLOR=#000000][COLOR=#007700]for([/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; [/COLOR][/COLOR]**[COLOR=#000000][COLOR=#0000bb]i[/COLOR][COLOR=#007700]<[/COLOR][COLOR=#0000bb]0[/COLOR][/COLOR]**[COLOR=#000000][COLOR=#007700]; [/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]++) 
    { 
        [/COLOR][COLOR=#0000bb]a1[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]] = [/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700];     
    }[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700] to [/COLOR][/COLOR]```
[COLOR=#000000][COLOR=#007700]for([/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; [/COLOR][/COLOR]**[COLOR=#000000][COLOR=#0000bb]i [/COLOR][COLOR=#007700]< 10[/COLOR][COLOR=#0000bb]0[/COLOR][/COLOR]**[COLOR=#000000][COLOR=#007700]; [/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]++) 
    { 
        [/COLOR][COLOR=#0000bb]a1[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]] = [/COLOR][COLOR=#0000bb]**i**[/COLOR]**[COLOR=#007700] + 1000[/COLOR]**[COLOR=#007700]; 
         
    }[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700] (see the bold parts) and then add your second for loop that you tried and see what you get. Good luck !

P.S. The i + 1000 is just so you can check that the output is not i, but actually a2[i].
[/COLOR][/COLOR]

---

### Post by S15_88 on 2008-02-18
bahh haha thanks alot! i had a total mental block! hahaha

---

