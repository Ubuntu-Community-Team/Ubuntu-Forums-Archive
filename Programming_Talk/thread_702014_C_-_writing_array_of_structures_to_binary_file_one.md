---
title: "C - writing array of structures to binary file one at a time"
date: 2008-02-19
forum: Programming Talk
---

### Post by S15_88 on 2008-02-19
I have an array of structures that i want to print to a binary file each element at a time.  I'm getting this error:
error: expected identifier or ‘(’ before ‘.’ token

where i assign a value to the contents of my structure.  i just don't see what is wrong...if someone could explain to me why my method isn't working it would be greatly appreciated.

Thanks, Alain
[PHP]
#include <stdio.h>
#include <stdlib.h>

struct data 
{
    int count;
};

typedef struct data datatype;

int main()
{
    int i;
    datatype a[10]; 
    FILE * structfile;

    structfile = fopen("/home/alain/structfile.txt", "w");

    for(i=0; i<10; i++)
    {
        datatype.count = i;/*ERROR*/

        fwrite(a, sizeof(datatype), 1, structfile);
    }    

    fclose(structfile);
    return 0;
}
[/PHP]

i'm trying to write to the binary file one structure at a time and assigning the value for count in the structure equal to the loop index.

---

### Post by yabbadabbadont on 2008-02-19
Is it time to do your homework for you again?  ;)

Edit: That was weird...  I saw my original comments, then they disappeared when I refreshed the page.  Anyway:

datatype is a "data type", not a variable.  'a' is your variable.  That should be enough to help you fix your bug.

---

### Post by S15_88 on 2008-02-19
haha it is a school assignment and yes i often do ask questions about my assignments but in all honesty i'm not expecting full solutions i'm honestly just asking whether my code makes sense...if you don't want to give me code it's fine i'm not expecting any.

and i had:
 a.count = it; 

but it gives me this error:
 error: request for member &#8216;count&#8217; in something not a structure or union

that's why i'm so puzzled.

Thanks, Alain

---

### Post by slavik on 2008-02-19
> **S15_88 said:**
> haha it is a school assignment and yes i often do ask questions about my assignments but in all honesty i'm not expecting full solutions i'm honestly just asking whether my code makes sense...if you don't want to give me code it's fine i'm not expecting any.

and i had:
 a.count = it; 

but it gives me this error:
 error: request for member &#8216;count&#8217; in something not a structure or union

that's why i'm so puzzled.

Thanks, Alain
to guide you a bit ... what is the type of 'a' ??? think carefully :)

---

### Post by yabbadabbadont on 2008-02-19
'a' is also an array....  ;)

---

### Post by slavik on 2008-02-19
> **yabbadabbadont said:**
> 'a' is also an array....  ;)
shush, he'll get it :)

---

### Post by yabbadabbadont on 2008-02-19
> **slavik said:**
> shush, he'll get it :)

I hadn't seen your reply when I was typing that.

---

