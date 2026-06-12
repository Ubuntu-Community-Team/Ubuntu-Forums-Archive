---
title: "Need help with simple program"
date: 2014-01-14
forum: Programming Talk
---

### Post by bikewrecker on 2014-01-14
Hey I'm writing this program for my CS class and it's been like 2 years since I've done C. It's embarrasing how much I've forgotten. Anyways, I'm writing a program which is pretty straight-forward, but for some reason I'm missing something critical and can't for the life of me figure out what it is. 

Here is my code: 
```
#include <stdio.h>
int
main(void)
{
        float begOdometer; 
        float endOdometer;
        printf("MILEAGE REIMBURSEMENT CALCULATOR\n");
        printf("Enter beginning odometer reading=> ");  
        scanf("%1f", &begOdometer);
        while(getchar() != '\n');
        printf("Enter ending odometer reading=> ");
        scanf("%1f", &endOdometer);
        while(getchar() != '\n');
        float miles;
        miles = endOdometer - begOdometer;
        float reimb;
        float rate = 0.45;
        reimb = miles * rate;
        printf("You traveled %1f miles. At $%1f per mile,\nyour reimbursement is $%1f\n", miles, rate, reimb);
        return (0);
}

```

Here is the output I recieve: 
```

[drmcb@pc32 ~]$ gcc reimbursement.c -o reimbursement.out -Wall
[drmcb@pc32 ~]$ ./reimbursement.out
MILEAGE REIMBURSEMENT CALCULATOR
Enter beginning odometer reading=> 900
Enter ending odometer reading=> 1000
You traveled -8.000000 miles. At $0.450000 per mile,
your reimbursement is $-3.600000

```

I either get very wrong numbers like -8 and -3.6 or I get 0's depending on my inputted values. 

Any insights would be greatly appreciated!

---

### Post by steeldriver on 2014-01-14
I think it's because you are specifying a maximum field width of 1 in your scanfs (conversion specifier **%[COLOR=#ff0000]1[/COLOR]f**) - so your inputs become begOdometer = 9 and endOdometer = 1

---

### Post by bikewrecker on 2014-01-14
Awesome! That fixed it. Thank you very much!

---

### Post by papibe on 2014-01-14
EDIT: a little too late ;)

Hi bikewrecker.

The problem is that "%1f" format in
```
scanf(**"%1f"**, &begOdometer);
```
would read a one digit number.

Replace it with:
```
scanf(**"%f"**, &begOdometer);
```
and it should work.

Regards.

---

