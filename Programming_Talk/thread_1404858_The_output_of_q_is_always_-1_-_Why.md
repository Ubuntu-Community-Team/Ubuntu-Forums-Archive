---
title: "The output of q is always -1 - Why?"
date: 2010-02-11
forum: Programming Talk
---

### Post by NielsBhor on 2010-02-11
Please help me debug my code. The purpose of the program is to calculate q based on the given parameters (q is the discharge of a capacitor). My problem is that q is always outputing -1 instead of the value when the charge has been discharged. It runs. But, q will always be -1 for some reason.

```

#include <stdio.h>
#include <math.h>


float q(int V, int R, float L, float C, float t)
{
    float q=1;
    
    q = (V*C)*(exp(-(R*t)/(2*L)))*cos(t*(sqrt((1/L*C)-pow(R/(L*C), 2)))); //Formula for the charge degradation in the capacitor
    
    return q;
}

void sim(int time, int V, int R, float L, float C, float timestep)
{
    float temp=1;
    float i=0;
    
    for (i=0;i<(time);)
    {
        temp=q(V,R,L,C,timestep);
        i=i+timestep;
        printf("The value of q is: %f\n",temp);
    }

    //printf("The value of q is: %f\n",temp);
}

int timer(int *time, float *timestep)
{
    
    printf("Please enter the length of the time, and time steps (time timestep): ");
    scanf("%i %f", time, timestep);

    return 1;
}


int circuit(int *V, int *R, float *L, float *C)
{
    do
    {
        printf("Please enter the value of V: ");
        scanf("%i", V);

        if (((*V) < 5) || ((*V) > 15))
        {
            printf("V needs to be between 5 and 15\n");
        }
    }while(((*V) < 5) || ((*V) > 15));

    do
    {
        printf("Please enter the value of R: ");
        scanf("%i", R);

        if (((*R) < 50) || ((*R) > 500))
        {
            printf("R needs to be between 50 and 500\n");
        }
    }while(((*R) < 50) || ((*R) > 500));

    do
    {
        printf("Please enter the value of L: ");
        scanf("%f", L);

        if (((*L) < 0.001) || ((*L) > 0.1))
        {
            printf("L needs to be between 0.001 and 0.1\n");
        }
    }while(((*L) < 0.001) || ((*L) > 0.1));

    do
    {
        printf("Please enter the value of C: ");
        scanf("%f", C);

        if (((*C) < 0.00001) || ((*C) > 0.0001))
        {
            printf("C needs to be between 0.00001 and 0.001\n");
        }
    }while(((*C) < 0.00001) || ((*C) > 0.0001));

    return 1;
}

int main(void)
{
    int 
        v=0, 
        r=0, 
        time=0,
        sentinal=0;
        
    float 
        c=0.0,
        l=0.0,
        timestep=0.0;

    while(!sentinal)
    {
        circuit(&v,&r,&l,&c);
        timer(&time,&timestep);
        sim(time,v,r,l,c,timestep);
        printf("To cancel the program press 1, if not, press 0: ");
        scanf("%i",&sentinal);
    }
    return 0;
}

```

---

### Post by schauerlich on 2010-02-12
I ran it, and got q = nan (not a number). I'm guessing there's a negative number popping up in the sqrt().

edit:

```
eric@river1:~/src/c$ ./q.out 
Please enter the value of V: 10
Please enter the value of R: 100
Please enter the value of L: 0.01
Please enter the value of C: 0.0001
Please enter the length of the time, and time steps (time timestep): 10 3
V: 10 R: 100 L: 0.01 C: 0.0001 t: 3.00 The value of q is: nan
V: 10 R: 100 L: 0.01 C: 0.0001 t: 3.00 The value of q is: nan
V: 10 R: 100 L: 0.01 C: 0.0001 t: 3.00 The value of q is: nan
V: 10 R: 100 L: 0.01 C: 0.0001 t: 3.00 The value of q is: nan
To cancel the program press 1, if not, press 0: 1

```

With these values, the number under the square root is -10000000272564224, which is obviously invalid.

---

### Post by NielsBhor on 2010-02-12
I thought of that too, so I changed the '-' to '+'. I still get a NaN error. I still could not figure out why it's doing that or how to fix it. 


> **schauerlich said:**
> I ran it, and got q = nan (not a number). I'm guessing there's a negative number popping up in the sqrt().

---

### Post by LKjell on 2010-02-12
I hope this is just to teach yourself C. Since there are other tools which suits better for these task. Like python and spice.

---

### Post by NielsBhor on 2010-02-12
It is to teach myself C. It is a problem from the book. I got everything it asked for except the part when q outputs. Atleast I think I got everything right.

> **LKjell said:**
> I hope this is just to teach yourself C. Since there are other tools which suits better for these task. Like python and spice.

---

### Post by schauerlich on 2010-02-12
> **NielsBhor said:**
> I thought of that too, so I changed the '-' to '+'. I still get a NaN error. I still could not figure out why it's doing that or how to fix it.

Since the numbers are so large, you might be having an overflow issues. Try using long ints and doubles.

---

### Post by lavinog on 2010-02-12
isn't (1/L*C) better represented as (C/L)

---

### Post by LKjell on 2010-02-12
> **lavinog said:**
> isn't (1/L*C) better represented as (C/L)

When you write it like that it is (C/L) This is because the expression is (1/L) * C

---

### Post by lavinog on 2010-02-12
```

exp(-(R*t)/(2*L))
```
if t > .1L you are going to get 0

---

### Post by lavinog on 2010-02-12
```
sqrt((1/L*C)-pow(R/(L*C), 2))
```
is pretty much the same as sqrt( - (R * X)^2 )
Where X is L*C which will be larger than 100000
at most C/L = .1 therefore can be considered insignificant

Are you sure your formula is correct?
is there a source for it?

---

### Post by NielsBhor on 2010-02-12
The formula is nearly correct, except that R/LC should be R/2L. That still doesn't fix my problem.

---

### Post by NielsBhor on 2010-02-12
The source for the formula is straight from the book. I didn't do any modifications.

---

### Post by lavinog on 2010-02-12
is this correct:
[img]http://ubuntuforums.org/attachment.php?attachmentid=146895&stc=1&d=1266014135[/img]

I am wondering if the (1/L * C) should be 1/(L*C)

---

### Post by NielsBhor on 2010-02-12
Thank you everybody for your help.

The author did a mistake on the formula. Underneath the radical should be (R/2L)^2 - 1/LC in the squareroot.

I fixed the problem. I appreciate everyone's effort.

---

