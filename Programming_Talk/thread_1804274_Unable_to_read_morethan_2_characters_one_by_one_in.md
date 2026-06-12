---
title: "Unable to read morethan 2 characters one by one in c"
date: 2011-07-14
forum: Programming Talk
---

### Post by kptsuresh on 2011-07-14
Hi,
i just want to right a program to read morethan two characters in c but ..its only able to read only two times..

the program is...
#include<stdio.h>
main()
{
    printf("Hello\n");
    char * a,b,c,d;
    scanf("%c",&a);
    printf("printing a %c",a);
    scanf("%c",&b);
    printf("\nprinting b %c",b);
    scanf("%c",&c);
    printf("\nprinting c %c",c);
    scanf("%c",&d);
    printf("\nprinting d %c",d);
    return (0);
    
}


any help please...

---

### Post by cgroza on 2011-07-14
Have you considered a loop combined with an array of char*s?

---

### Post by Bachstelze on 2011-07-14
```
firas@aoba ~ % cat test.c
#include<stdio.h>
main()
{
printf("Hello\n");
char * a,b,c,d;
scanf("%c",&a);
printf("printing a %c",a);
scanf("%c",&b);
printf("\nprinting b %c",b);
scanf("%c",&c);
printf("\nprinting c %c",c);
scanf("%c",&d);
printf("\nprinting d %c",d);
return (0);

}
firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c                                
cc1: warnings being treated as errors
test.c:3: warning: return type defaults to &#8216;int&#8217;
test.c: In function &#8216;main&#8217;:
test.c:6: warning: format &#8216;%c&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;char **&#8217;
test.c:7: warning: format &#8216;%c&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;char *&#8217;

```

Fix that first.

---

### Post by JupiterV2 on 2011-07-14
Also do some searching, even in these forums, on the drawbacks/risks of using scanf to read from stdin.

---

### Post by Bachstelze on 2011-07-14
> **JupiterV2 said:**
> Also do some searching, even in these forums, on the drawbacks/risks of using scanf to read from stdin.

IMO scanf is acceptable when one is learning C, be it only because the main alternative (fgets+sscanf) requires some knowledge of how buffers and strings work (and understanding scanf's shortcomings even more so). scanf is more simple "just call it with the name of the variable preceded by a &, whatever that means, and the read value will be stored in that variable". One should certainly get rid of scanf as soon as possible, but in kptsuresh's case, now may be a bit too soon. ;)

---

