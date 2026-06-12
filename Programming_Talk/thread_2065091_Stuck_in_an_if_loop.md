---
title: "Stuck in an if loop"
date: 2012-10-01
forum: Programming Talk
---

### Post by Litost on 2012-10-01
Problem! I have to make a program that accepts an integer and judges how many decimal places it has by using if statements and < 10, < 100 all the way up to a billion. Here is my code:
    if (x < 0) 
    { x = (x * -1); } 
    else if  (x < 10) 
        { System.out.println("This number has 1 digit."); }
        else if (x < 100 )
        { System.out.println("This number has 2 digits."); } 
            else if (x < 1000)
        { System.out.println("This number has 3 digits."); } 
                else if (x < 10000)
        { System.out.println("This number has 4 digits."); }
                    else if (x < 100000)
        { System.out.println("This number has 5 digits."); }
                        else if (x < 1000000)
        { System.out.println("This number has 6 digits."); }
                            else if (x < 10000000)
        { System.out.println("This number has 7 digits."); }
                                else if (x < 100000000)
        { System.out.println("This number has 8 digits."); }
                                    else if (x < 1000000000)
        { System.out.println("This number has 9 digits."); }
    }
}                        
This works great, unless I get a negative number, which is one of the inputs I had to try. I don't know how to get it to turn the negative number positive (which is the way I was instructed to deal with negative numbers in the question) but then also continue to go down the if tree.  Advice?

---

### Post by PaulM1985 on 2012-10-01
It looks like you are making the number positive by multiplying by minus 1. Do you send it through the if statement again once it is positive?

---

### Post by Vaphell on 2012-10-01
also try replacing that huge block of conditions with a loop. Conditions and results are very regular here, they would lend themselves to a general solution with a bit of math with no problem.

let's say start from the other end with m=100000000, n=9
check if the number/m is > 0 (integer division), return n
if not, m=m/10, n=n-1, repeat.

you can even transform the number to a text string and get its length.

---

### Post by The Cog on 2012-10-01
> if (x < 0)
{ x = (x * -1); }
else if (x < 10)

Your problem is here. If it's a negative number, you never test if it's single-digit.

---

### Post by albandy on 2012-10-01
> **Litost said:**
> Problem! I have to make a program that accepts an integer and judges how many decimal places it has by using if statements and < 10, < 100 all the way up to a billion. Here is my code:
    if (x < 0) 
    { x = (x * -1); } 
    else if  (x < 10) 
        { System.out.println("This number has 1 digit."); }
        else if (x < 100 )
        { System.out.println("This number has 2 digits."); } 
            else if (x < 1000)
        { System.out.println("This number has 3 digits."); } 
                else if (x < 10000)
        { System.out.println("This number has 4 digits."); }
                    else if (x < 100000)
        { System.out.println("This number has 5 digits."); }
                        else if (x < 1000000)
        { System.out.println("This number has 6 digits."); }
                            else if (x < 10000000)
        { System.out.println("This number has 7 digits."); }
                                else if (x < 100000000)
        { System.out.println("This number has 8 digits."); }
                                    else if (x < 1000000000)
        { System.out.println("This number has 9 digits."); }
    }
}                        
This works great, unless I get a negative number, which is one of the inputs I had to try. I don't know how to get it to turn the negative number positive (which is the way I was instructed to deal with negative numbers in the question) but then also continue to go down the if tree.  Advice?

you can use the abs() method to get the absolute value of the number.

also you can do this:

String number = Integer.toString(abs(x));

if (abs(x)>=0 && abs(x)<1000000000) System.out.println("This number has " + number.lenght + " digits");

---

### Post by ofnuts on 2012-10-01
> **Litost said:**
> Problem! I have to make a program that accepts an integer and judges how many decimal places it has by using if statements and < 10, < 100 all the way up to a billion. Here is my code:
    if (x < 0) 
    { x = (x * -1); } 
    else if  (x < 10) 
        { System.out.println("This number has 1 digit."); }
        else if (x < 100 )
        { System.out.println("This number has 2 digits."); } 
            else if (x < 1000)
        { System.out.println("This number has 3 digits."); } 
                else if (x < 10000)
        { System.out.println("This number has 4 digits."); }
                    else if (x < 100000)
        { System.out.println("This number has 5 digits."); }
                        else if (x < 1000000)
        { System.out.println("This number has 6 digits."); }
                            else if (x < 10000000)
        { System.out.println("This number has 7 digits."); }
                                else if (x < 100000000)
        { System.out.println("This number has 8 digits."); }
                                    else if (x < 1000000000)
        { System.out.println("This number has 9 digits."); }
    }
}                        
This works great, unless I get a negative number, which is one of the inputs I had to try. I don't know how to get it to turn the negative number positive (which is the way I was instructed to deal with negative numbers in the question) but then also continue to go down the if tree.  Advice?
Actually you don't need an else when testing of negative. You code should look like:
```

if X negative
   then X=-X

Now X is positive and you can proceed with the tests for the digits

```

---

### Post by Litost on 2012-10-01
Thank you everyone for the responses but I should have have been more specific. I have to turn it positive by multiplying it by negative 1, I can't use a loop, and my problem is I don't know how to make it go through the rest of the tree after I multiply it by -1. All the numbers work except negative numbers, I see the reason it stops is because I said "if negative then multiple by one" so why would it continue on with the else instruction, but I don't know what to do to make it do both.

---

### Post by Vaphell on 2012-10-01
you can't use loop because ...?
you can't use get_length( convert_to_string(number) ) approach either, because ...?

//first if
if x<0 x=-x

//another if
if x < 10
else if x < 100
else if x <1000
else if ...

---

### Post by thatguruguy on 2012-10-01
> **Litost said:**
> Thank you everyone for the responses but I should have have been more specific. I have to turn it positive by multiplying it by negative 1, I can't use a loop, and my problem is I don't know how to make it go through the rest of the tree after I multiply it by -1. All the numbers work except negative numbers, I see the reason it stops is because I said "if negative then multiple by one" so why would it continue on with the else instruction, but I don't know what to do to make it do both.

You've been told the answer. Take out the first "else" statement.

---

### Post by Litost on 2012-10-01
Hahahah to be honest I have no idea why I can't use a loop I guess because I'm supposed to get familiar with the if function. That worked,  but  I tried it last night before you told me and it gave me an error message! I guess I screwed it up somehow! Thank you again.

---

### Post by StephenF on 2012-10-01
Going off on a tangent for non zero values of n: floor(log10(abs(n))) + 1

---

