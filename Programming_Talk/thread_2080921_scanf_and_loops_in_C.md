---
title: "scanf and loops in C"
date: 2012-11-05
forum: Programming Talk
---

### Post by snoopunit on 2012-11-05
So I have sort of a weird problem.... I have a program that's supposed to read input integers until the user enters a specific number (999), but the scanf statement seems to continue asking for input even thought my loop has completed. I've tried flushing the input with fflush(stdin), but apparently it's known not to work in linux? Any help would be appreciated.

```

int main (void){
    int j=0, n=0;
    int num[50] = {0};
    printf("Please enter your numbers.\n");
    while(n!=999){
        scanf("%d",&n);
        num[j] = n;
        j++;
    }
    printf("\nThe number of integers is:            %d", length(num));
    printf("\nThe sum of integers is:                %d", sum(num));
    printf("\nThe average of integers is:            %.2f", avg(num));
    printf("\nThe smallest of integers is:            %d", small(num));    
    printf("\nThe largest of integers is:            %d", large(num));
    printf("\nAt least one number was <20:            %d", less(num));
    printf("\nAt least one number was between 10 and 90:    %d\n", between(num));

return 0;
}

```

even after entering 999, the program continues to request more input while ignoring the rest of the code within the loop

---

### Post by dwhitney67 on 2012-11-05
Doing a spot check of your code reveals no issues; are you sure you posted all of your code?

On a side note, you should refrain from using scanf() to read raw-input from a user.  Use a combination of fgets() and sscanf() to get the appropriate data input.

For example:
```

#include <stdio.h>

int main()
{
    int n = 0;

    while (n != 999)
    {
        char input[20];

        printf("Enter a number: ");

        fgets(input, sizeof(input), stdin);

        if (sscanf(input, "%d", &n) != 1)
        {
            /* error parsing input */
        }
    }

    return 0;
}

```

---

### Post by Abhinav Kumar on 2012-11-05
> **snoopunit said:**
> So I have sort of a weird problem.... I have a program that's supposed to read input integers until the user enters a specific number (999), but the scanf statement seems to continue asking for input even thought my loop has completed. I've tried flushing the input with fflush(stdin), but apparently it's known not to work in linux? Any help would be appreciated.

```

int main (void){
    int j=0, n=0;
    int num[50] = {0};
    printf("Please enter your numbers.\n");
    while(n!=999){
        scanf("%d",&n);
        num[j] = n;
        j++;
    }
    printf("\nThe number of integers is:            %d", length(num));
    printf("\nThe sum of integers is:                %d", sum(num));
    printf("\nThe average of integers is:            %.2f", avg(num));
    printf("\nThe smallest of integers is:            %d", small(num));    
    printf("\nThe largest of integers is:            %d", large(num));
    printf("\nAt least one number was <20:            %d", less(num));
    printf("\nAt least one number was between 10 and 90:    %d\n", between(num));

return 0;
}

```even after entering 999, the program continues to request more input while ignoring the rest of the code within the loop
Hi,
I made a few changes in your code and ran it
```

#include<stdio.h>
int main (void){
    int j=0, n=0;
    int num[50] = {0};
    printf("Please enter your numbers.\n");
    while(n!=999){
        scanf("%d",&n);
        num[j] = n; 
//j takes care of no of loops. But, it should NOT be used as an array index
        j++;
    }
return 0;
}

```
It ran successfully. I had compiled using```
gcc -Wall -lm fileName.c
```
See if this works

Regards 
Abhinav

---

### Post by snoopunit on 2012-11-05
thanks for the help

---

### Post by Tony Flury on 2012-11-06
This issue here is that scanf is not a good idea for user input. scanf stops when it hits whitespace - but critically it does not consume it - so the newline/return character is still in the buffer when you call scanf again.

If you want to read user iput - use a combination of fgets and sscanf (or manually parsing) to detect are read your number input.

---

### Post by kevinharper on 2012-11-06
> **snoopunit said:**
> ...I've tried flushing the input with fflush(stdin), but...

Someone on this forum suggested to following to me a little over a year ago:
```
/* clrstdin() clear any leftover chars tha may be in stdin stream */
void clrstdin( void )
{
   int ch = 0;

   while( ( ch = getchar() ) != '\n' && ch != EOF )
         ;
}
```
It is an "stdin flusher". Worked great for me! I made it a function so I could just call it every time input was provided.

---

