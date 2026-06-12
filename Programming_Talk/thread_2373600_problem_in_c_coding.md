---
title: "problem in c coding"
date: 2017-10-07
forum: Programming Talk
---

### Post by von9711 on 2017-10-07
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
void main()
{ system("clear");
char s[50][50];
int a,j,n,b=0,e=0,k,d=0;
static int i=0;
printf("Enter the number of names you want to enter:  ");
scanf("%d",&n);
printf("Enter names: \n"); 
for(i=0;i<n;i++)
{ scanf(" %[^\n]s",s[i]);                  //what can i use instead of this
}
printf("Names after abb.: \n");
for(i=0;i<n;i++);
{ a=strlen(s[i]);
printf("%d\n",a);                            // why a is coming zero....
for(j=0;j<a;j++)
{ if(s[0][j]==' ')
{ b++; } } 
for(k=0;k<b;k++)
{ printf("%c.",s[i][k+e]);
while(s[0][d]!=' ')
 { e++; d=e; }
 d=e+1;} 
printf("%s\n",&s[i][d]);
} 
}

input: 
chandelier
a is coming zero...
what's the problem.....please help

---

### Post by wildmanne39 on 2017-10-07
*Thread moved to **Programming Talk for better support**.*

---

### Post by QIII on 2017-10-07
Have you spoken with your instructor?

---

### Post by lisati on 2017-10-08
As others have asked, have you asked your instructor?

Properly formatting your code can help with debugging some kinds of problems, as can using [code tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168") when copying to the forum.

---

### Post by von9711 on 2017-10-08
No i haven't asked my instructor as it is the part of my assignment.

---

### Post by steeldriver on 2017-10-08
```

for(i=0;i<n;i++)[COLOR=#ff0000]**;**[/COLOR]

```

loops from i=0 to i=n-1 **doing nothing**

Then you execute the body 
```

{ a=strlen(s[i]);
printf("%d\n",a);                            // why a is coming zero....
for(j=0;j<a;j++)
{ if(s[0][j]==' ')
{ b++; } } 
for(k=0;k<b;k++)
{ printf("%c.",s[i][k+e]);
while(s[0][d]!=' ')
 { e++; d=e; }
 d=e+1;} 
printf("%s\n",&s[i][d]);
}

```

once, with i=n

---

### Post by jeremy31 on 2017-10-08
Per [https://ubuntuforums.org/showthread.php?t=2158945](https://ubuntuforums.org/showthread.php?t=2158945) see item #8
Thread is closed

---

