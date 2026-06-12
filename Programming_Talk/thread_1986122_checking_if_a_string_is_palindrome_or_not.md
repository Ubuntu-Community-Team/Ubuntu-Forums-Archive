---
title: "checking if a string is palindrome or not"
date: 2012-05-24
forum: Programming Talk
---

### Post by jamesbon on 2012-05-24
This is not a home work problem.It is an interview question taken discussed [here]("http://www.careercup.com/question?id=13650664") 

I made a program for same

```
#include<stdio.h>
#include<string.h>
int main ()
{
 int i,j,k;
 char st[50];
        k=0;
        printf("enter string\n");
        scanf("%s",st);
        printf("the entered string is %s\n",st);
        j=strlen(st);
        for (i=0;i<=j/2;i++)
        {
         if(st[i]!=st[j-i-1])
             k=k+1;
        }
        if(k==0)
        printf("string %s is palindrom\n",st);
        else
        printf("string %s is not palindrome \n",st);
}

```

What I am not clear is if my solution is the correct solution for the problem.Please read the problem and see if my solution is correct or not.It is a working code.

---

### Post by roelforg on 2012-05-24
```

if(strncmp(st,"palindrome",strlen("palindrome"))==0)
{
//st==palindrome
}

```

---

### Post by Bachstelze on 2012-05-24
EDIT: Disregard the message above.

1. Do Not Use scanf()&#8482; [http://c-faq.com/stdio/scanfprobs.html](http://c-faq.com/stdio/scanfprobs.html)
2. REALLY do not scanf("%s", buf) because if the user inputs a string larger than your buffer, you get a buffer overflow.
3. Your idea sorta kinda works. This is better:

```

bool ok = true;
for (int i=0; i<=j/2; i++) {
    if (str[i] != str[j-i-1]) {
        ok = false;
        break;
    }
}
if (ok) {
    printf("is a palindrome\n");
} else {
    printf("is not a palindrome\n");
}
```

The two problems you have is that you are incrementing k when you could just set it to 1 (you avoid the risk of overflowing if the string is really long), and you run a lot of unnecessary computation: once you have a mismatch, you can exit the loop, the string is definitely not a palindrome.

---

### Post by ofnuts on 2012-05-24
IMHO the code would be a bit more readable like this:
```

    int last=strlen(st)-1;
    same=1;
    int i;
        for (i=0; (i < last/2) && ok;i++)
        {
         if (st[i] != st[last-i])
             same=0;
        }
    if (same)
        printf("%s: palindrom (%d)\n",st,i);
    else
        printf("%s: not a palindrom (%d)\n",st,i);

```

---

### Post by Bachstelze on 2012-05-24
Why do people always insist on using an int for true/false values? That's what bool is for...

---

### Post by zombifier25 on 2012-05-24
> **Bachstelze said:**
> Why do people always insist on using an int for true/false values? That's what bool is for...

There's no bool in C.

---

### Post by dwhitney67 on 2012-05-24
> **ofnuts said:**
> IMHO the code would be a bit more readable like this:


Readability is a worthy goal; but getting the code to compile should be of the utmost importance.

---

### Post by Bachstelze on 2012-05-24
> **zombifier25 said:**
> There's no bool in C.

Is too.

---

### Post by dwhitney67 on 2012-05-24
> **zombifier25 said:**
> There's no bool in C.

That's not true; include <stdbool.h>

---

### Post by zombifier25 on 2012-05-24
Didn't know that :P I don't study C however, I just read somewhere that C doesn't have bool (by default obviously)

---

### Post by trent.josephsen on 2012-05-24
> **zombifier25 said:**
> Didn't know that :P I don't study C however, I just read somewhere that C doesn't have bool (by default obviously)
<stdbool.h> was introduced in C99. A lot of things were introduced in C99 and many compilers (including GCC) still don't support it 100% (because a lot of the design decisions were stupid), so it is still meaningful on occasion to distinguish between C89 features and C99 features. Maybe not in this case.

---

