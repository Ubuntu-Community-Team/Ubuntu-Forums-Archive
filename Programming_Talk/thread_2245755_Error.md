---
title: "Error"
date: 2014-09-25
forum: Programming Talk
---

### Post by tdstruxness on 2014-09-25
h0926.c:21:23: warning: assignment makes integer from pointer without a cast [enabled by default]
          discountRate = "20%";
I am new to programming and am doing an assignment for a class but keep getting this error message.
Below is the code, could you please help and explain what i am doing wrong thanks.

#include <stdio.h>


main ()
{
        system ("clear");
        float sale1, sale2, sale3, totalSales;
        char name[20], discountRate;


        //start to read data
        printf ("What is your name? ");
        scanf ("%s", name);
        printf ("Great %s, now enter your three sales: ", name);
        scanf ("%f%f%f", &sale1, &sale2, &sale3);


        //calculate the total sales
        totalSales =  (sale1 + sale2 + sale3);
        
        if (totalSales >= 10000)
        {
         printf ("Congratulations\n");
         discountRate = "20%";
        }
        else if (totalSales >= 8000)
        {
         printf ("Congratulations\n");
         discountRate = "15%";
        }
        else if (totalSales >= 6000)
        {
         printf ("Congratulations\n");
         discountRate = "10%";
        }
        else if (totalSales >= 40000)
        {
    printf ("Congratulations\n");
         discountRate = "5%";
        }
        else
        {
         printf ("Sorry\n");
         discountRate = "0%";
        }
        //anything that follows the if block is out of the decision making
        
         printf ("Your discount rate was %c\n", discountRate);
         printf ("Have a good day %s\n", name);


}

---

### Post by Vaphell on 2014-09-25
discountRate is declared as char, 1 char. Trying to save a string there confuses the compiler, it takes the pointer to your "N%" string and crams it into that single char. You would need a pointer to char(s).

why do you use string for a discount rate in the first place with %? go with (unsigned) integer/char, you know it's percent.
```
discountRate = 20; //15/10/5/0;
```
and then 
```
printf( "Your discount rate was %d%%\n", discountRate )
```

It's infinitely easier to use numbers. They are both easily printable and readily available for any math involved.

---

