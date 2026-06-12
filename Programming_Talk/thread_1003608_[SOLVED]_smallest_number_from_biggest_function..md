---
title: "[SOLVED] smallest number from biggest function."
date: 2008-12-06
forum: Programming Talk
---

### Post by StOoZ on 2008-12-06
Is it possible to do the following :
[PHP]int biggestOfThree( int num1 , int num2 , int num3 ) {

    int temp = (num1 > num2) ? num1 : num2;
    temp = ( temp > num3 ) ? temp : num3;

    return temp;
}

int smallestOfThree( int num1 , int num2 , int num3 ) {

    // use biggestOfThree here to determine the smallest number.
    // do not use comparison stuff

    return num3;
}
[/PHP]

Need to use biggestOfThree in smallestOfThree , to determine the smallest number without using comparison operators...
I dont think its possible.
what do u think?

---

### Post by pp. on 2008-12-06
> **StOoZ said:**
> 
what do u think?

Eye wood theenk
[LIST]
[*]It's perfectly pointless
[*]It can be done
[*]It takes more than one call to biggest
[/LIST]

---

### Post by Reiger on 2008-12-06
Easy: 

smallesOfThree(a,b,c) {
temp = biggestOfThree(-a,-b,-c);
return -temp;
}

---

### Post by nvteighen on 2008-12-06
> **StOoZ said:**
> Is it possible to do the following :
[PHP]int biggestOfThree( int num1 , int num2 , int num3 ) {

    int temp = (num1 > num2) ? num1 : num2;
    temp = ( temp > num3 ) ? temp : num3;

    return temp;
}

int smallestOfThree( int num1 , int num2 , int num3 ) {

    // use biggestOfThree here to determine the smallest number.
    // do not use comparison stuff

    return num3;
}
[/PHP]

Need to use biggestOfThree in smallestOfThree , to determine the smallest number without using comparison operators...
I dont think its possible.
what do u think?
Why do you think it is impossible?

---

### Post by pp. on 2008-12-06
> **Reiger said:**
> Easy: 

smallesOfThree(a,b,c) {
temp = biggestOfThree(-a,-b,-c);
return -temp;
}

I hadn't thought of that. 

Even shorter:

```
return -biggestOfThree(-a,-b,-c);
```

---

### Post by StOoZ on 2008-12-06
thank you all!! ):P

---

