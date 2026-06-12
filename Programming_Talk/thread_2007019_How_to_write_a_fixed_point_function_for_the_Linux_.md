---
title: "How to write a fixed point function for the Linux Kernel?"
date: 2012-06-20
forum: Programming Talk
---

### Post by geewhan on 2012-06-20
I would like to ask how to use fixed point in the linux kernel because the two functions, kernel_fpu_begin() and kernel_fpu_end(), does not work. So another method for solving this floating number is to use fixed point. My partner and I talked about this and we came upon to this function.


```
/*new "fixed" function -----------------------------------------*/global int cy; //comment: use global variable  cy .
global int x, int y;


int  filter(int x, int y) 
{
   cy = 10000*a*x + b*cy; // comment: cy = 10000*y; x is input;
   y = cy/10000;   //comment: 1>a >0; 1>b>0;
   return y;
}

/*----------------------------*/
```


I am still having trouble understanding this function. Okay so you take the values x and y and multiple the values okay. I do not see how this help for floating numbers.

The code below looks exactly the same as the fixed point function.
So how is this possible if I cannot use decimals/floating numbers?
```
avgRTT = ((255/256)*avgRtt) + ((1/256)*rtt);
```

Do you know any links or examples. I really want to figure this out because there is really no other way to go around this beside the fixed point function lol.

Thanks

---

### Post by Bachstelze on 2012-06-20
And this is related to the kernel how?

---

### Post by ofnuts on 2012-06-20
> **geewhan said:**
> I would like to ask how to use fixed point in the linux kernel because the two functions, kernel_fpu_begin() and kernel_fpu_end(), does not work. Just be a bit more modest and assume you don't know how to use them properly...

> **geewhan said:**
> So another method for solving this floating number is to use fixed point. My partner and I talked about this and we came upon to this function.


```
/*new "fixed" function -----------------------------------------*/global int cy; //comment: use global variable  cy .
global int x, int y;


int  filter(int x, int y) 
{
   cy = 10000*a*x + b*cy; // comment: cy = 10000*y; x is input;
   y = cy/10000;   //comment: 1>a >0; 1>b>0;
   return y;
}

/*----------------------------*/
```
I am still having trouble understanding this function. Okay so you take the values x and y and multiple the values okay. I do not see how this help for floating numbers.

The idea of "fixed point" is that you scale up everything so that your  smallest significant digit is the units digits. So to computer, for  instance, "2.45 * 6.32" you compute "245 * 632" ("(2.45*100) *  (6.32*100)" and divide the result by 10000 (100*100). The art of fixed  point is to order the operations carefully and scale up/down at the right times to avoid losing digits at  one end and ending with overflows at the other.

> **geewhan said:**
> The code below looks exactly the same as the fixed point function.
So how is this possible if I cannot use decimals/floating numbers?
```
avgRTT = ((255/256)*avgRtt) + ((1/256)*rtt);
```Do you know any links or examples. I really want to figure this out because there is really no other way to go around this beside the fixed point function lol.

With integer operations, "255/256" gives 0. (255*avgRtt)/256 may give a better result. Rewrite your whole operation as:
```

avgRTT = ((255*avgRtt) + rtt)/256

```

Programming the kernel... hmmm....

---

