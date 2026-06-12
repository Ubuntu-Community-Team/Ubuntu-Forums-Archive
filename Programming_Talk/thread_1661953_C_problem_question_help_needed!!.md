---
title: "C problem question help needed!!"
date: 2011-01-07
forum: Programming Talk
---

### Post by hyperAura on 2011-01-07
Hi i am trying to use the pow function in one of my programs but it doesnt seem to be working properly for me.. Any help appreciated..

A part of my code is the following..
    
    float base, power;
    double answer;

        answer = (pow(power,(1/2)));

        printf("%f raised to the power of %f is %f.", base, power, answer);


Test data is: 

base: 56

power: 1/2

Test results

Answer: 1

It seems from the results that the pow function instead of raising the base (56) to the power (1/2), that it is rounding the power downwards, (i think due to casting), and therefore the base is raised to power 0 and the answer i get is 1.. 

Anyone that can help please help!!!!!!! Thanks

---

### Post by MadCow108 on 2011-01-07
> **hyperAura said:**
> Hi i am trying to use the pow function in one of my programs but it doesnt seem to be working properly for me.. Any help appreciated..

A part of my code is the following..
    
    float base, power;
    double answer;

        answer = (pow(power,(1/2)));

        printf("%f raised to the power of %f is %f.", base, power, answer);


Test data is: 

base: 56

power: 1/2

Test results

Answer: 1

It seems from the results that the pow function instead of raising the base (56) to the power (1/2), that it is rounding the power downwards, (i think due to casting), and therefore the base is raised to power 0 and the answer i get is 1.. 

Anyone that can help please help!!!!!!! Thanks

1/2 does integer division, which results in 0
make them floats or doubles:
1./2.

---

