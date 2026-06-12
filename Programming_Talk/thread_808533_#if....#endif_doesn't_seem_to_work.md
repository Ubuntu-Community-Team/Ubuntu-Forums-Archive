---
title: "#if....#endif doesn't seem to work"
date: 2008-05-26
forum: Programming Talk
---

### Post by Ned_in_Vancouver on 2008-05-26
The following conditional compilation works fine in Windows (Visual Studio) but i can't seem to get it to work in Eclipse on Unbuntu 8.04:

#define chatty 9
.
.
#if chatty > 9
printf(.......);
#endif

Eclipse/GCC highlights the #if and #endif so it recognizes the tokens, but it seems to compile the print statement anyway. I'm a newbie with Linux; is there some setting I should be setting so that GCC will recognize it?

Many thanks for what i'm sure is an operator error.

Ned

---

### Post by croto on 2008-05-26
I compiled this code with gcc:

```

#include<stdio.h>

#define flag 9

int main(){
#if flag > 8
  printf("flag>8\n");
#endif
#if flag > 9
  printf("flag>9\n");
#endif
  return 0;
}

```

The output is
```

flag>8

```

I don't seem to be able to reproduce the behavior you are saying. May it be related to Eclipse?

---

### Post by skeeterbug on 2008-05-26
> **Ned_in_Vancouver said:**
> The following conditional compilation works fine in Windows (Visual Studio) but i can't seem to get it to work in Eclipse on Unbuntu 8.04:

#define chatty 9
.
.
#if chatty > 9
printf(.......);
#endif

Eclipse/GCC highlights the #if and #endif so it recognizes the tokens, but it seems to compile the print statement anyway. I'm a newbie with Linux; is there some setting I should be setting so that GCC will recognize it?

Many thanks for what i'm sure is an operator error.

Ned

Since when is 9 > 9? Maybe you meant 9 >= 9?

---

### Post by sgg245 on 2008-05-27
It's working perfectly alright...

Try out this code... I tried in C++ rather on C...

int main()
{
 char quit;
 while(quit != 'q')
 {
    #if f > 9
        cout << "f > 9";
    #endif
    #if f < 9
        cout << "f < 9";
    #endif
    #if f == 9
        cout << "f = 9";
    #endif
        
    cout << "\nEnter q to QUIT : ";
    cin >> quit;
 }
    return 0;
}

---

### Post by Ned_in_Vancouver on 2008-05-28
Many thanks for all the help. Looks like the problem was Eclipse. I installed Geany - simpler IDE - and the problem disappeared.

---

