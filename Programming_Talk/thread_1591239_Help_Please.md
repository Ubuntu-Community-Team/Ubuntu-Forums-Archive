---
title: "Help Please?"
date: 2010-10-09
forum: Programming Talk
---

### Post by Planetes on 2010-10-09
Hi, I am very new to this but i can't seem to figure this out through books and google searches alone.

I can't figure out where the error is in this code i'm trying to write. I may now after having tried to fix it several thousand time thrown in some extra brackets and what not so i apologize if there are any.

It says i have a syntax error before the else that calculate the C grade value.

```

#include <stdio.h>
#include <math.h>

main()
{
       
float total, earned, percent;

      
      printf("Enter Total Points");
      scanf(" %f", &total);
      
      printf("Enter Earned Points");
      scanf("%f", &earned);
                  
                  
percent = 100*(earned / total);

                  printf("Grade Percentage %.2f \n", percent);
      
      
      if (percent >= 90)
        printf("Letter Grade: A");
      else { if ( (percent >= 80) && (percent <= 89));
               { printf("Letter Grade: B"); }}
               
               else { if ((percent >= 70) && (percent <= 79))
                  { printf("Letter Grade: C"); }}
                   else { if ((percent >= 60) && (percent <= 69))
                     { printf("Letter Grade: D"); }} }
     else
        { printf("Letter Grade: F \n"); }
      

      system("pause");
return 0;
}

```

I have created a simpler alternate version that I can submit if it reaches that time but I'de still like to know what i'm doing wrong.

---

### Post by yabbadabbadont on 2010-10-09
You have more "}" than "{".  Try cleaning up the format of the code and it should become obvious where you went wrong.  :D

Edit: You also have an extra semi-colon that, while syntactically allowed, will cause the code to produce incorrect output.  ;)

Edit2: After I cleaned it up, I realized that the extra semi-colon was also prevent a compile.  It's been a while since I coded in C (or C++ for that matter).

---

### Post by Planetes on 2010-10-09
I knew IT!!! Those little buggers.

Thank you.

---

### Post by Planetes on 2010-10-09
Well I found what you were talking about however my compiler is telling me i have a more immediate problem located around my second else clause.

---

### Post by yabbadabbadont on 2010-10-09
You might also want to check to see if the user entered zero for total points before you divide by it...  unless you just want to cause the universe to disappear.  :D

You have way too many {} in there as well as mismatched numbers of if's and else's.  Try writing out your solution in long hand on a piece of paper in English.  That usually helps beginning coders.

If you still have trouble, post the new code you are trying to build.

---

### Post by Planetes on 2010-10-09
I was sort of think the same thing about the brackets, I just don't know. I barely know the syntax and cannot find a good example of nested if clauses anywhere to guide me. 

Well whatever the case I have a version submitted already so the pressures off.

Gracias

---

### Post by yabbadabbadont on 2010-10-09
Here is your original code reformatted so that it should be easier to spot your errors:

```
#include <stdio.h>
#include <math.h>

main()
{
       
    float total, earned, percent;


    printf("Enter Total Points");
    scanf(" %f", &total);

    printf("Enter Earned Points");
    scanf("%f", &earned);

    percent = 100*(earned / total);
    printf("Grade Percentage %.2f \n", percent);

    if (percent >= 90)
        printf("Letter Grade: A");
    else
    {
        if ((percent >= 80) && (percent <= 89));
        {
            printf("Letter Grade: B");
        }
    }
    else
    {
        if ((percent >= 70) && (percent <= 79))
        {
            printf("Letter Grade: C");
        }
    }
    else
    {
        if ((percent >= 60) && (percent <= 69))
        {
            printf("Letter Grade: D");
        }
    }
}
else
{
    printf("Letter Grade: F \n");
}

system("pause");
return 0;
}

```

---

### Post by Mobidoy on 2010-10-09
You also have errors in your conditional structure. You can only have one else clause and it will be the last one. Between the IF and the ELSE, you need to use ELSE IF.

```

if (age >= 18)
  {
    printf ("You are major !");
  }

**else if** ( age > 10 )
  {
    printf ("Grow up");
  }

else
  {
    printf ("Aga gaa aga gaaa gaaa");
  }

```

---

### Post by Planetes on 2010-10-09
> **Mobidoy said:**
>  you need to use ELSE IF.



I did figure it out and it was something similar to your "else if". seems like yours is a nice mind trick to help you get around it. I had to place the ending bracket for each nested "else" at the very end, after all other "if's" and "else's".

So it looks like this now and it works. Still no zero stopper but who cares if the universe gets flushed down the toilet right.

```


#include <stdio.h>
#include <math.h>

main()
{
       
    float total, earned, percent;


    printf("Enter Total Points");
    scanf(" %f", &total);

    printf("Enter Earned Points");
    scanf("%f", &earned);

    percent = 100*(earned / total);
    printf("Grade Percentage %.2f \n", percent);

    if (percent >= 90)
       { printf("Letter Grade: A \n");} 
    else
    {
        if ((percent >= 80) && (percent <= 89))
        {
            printf("Letter Grade: B \n");
        }
    
        else
    {
            if ((percent >= 70) && (percent <= 79))
        {
            printf("Letter Grade: C \n");
        }
    
            else
    {
                if ((percent >= 60) && (percent <= 69))
        {
                printf("Letter Grade: D \n");
        }
 
else
{
    printf("Letter Grade: F \n");
                 }
           }
     }
}

system("pause");
return 0;

}


```

By the way Yabbadabba, your cleaned up formatting help a lot. I liked your placement of the brackets. I will be writing like that from now on. :)

---

### Post by trent.josephsen on 2010-10-09
Personally, I prefer K&R formatting, and use GNU indent to format most source code listings that I find online.

A few notes:
- You aren't using <math.h> at all, so there's no need to include it.
- It's a good idea to prototype main.  (An empty () like in your program means the function is not prototyped, so the compiler can't do any error checking if it's ever called with arguments.)  When you don't care to take arguments, use "int main(void)".
- Don't use scanf for user input.  When it fails, it fails hard, and you can't recover from it.
- When you do use scanf, make sure it succeeds by checking its return value.
- Your algorithm gives unusual results for certain inputs, e.g. 268 out of 300
- system("pause") is an ugly and unportable solution to a problem that doesn't exist.  Run your program from a shell and you don't need to worry about the terminal disappearing after the output is printed.  If you *really* want to wait for the user to hit Enter, you should prefer to do that in standard C.

---

