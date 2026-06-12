---
title: "A Little Help"
date: 2012-09-24
forum: Programming Talk
---

### Post by Mohan1289 on 2012-09-24
Hey Guys i am trying to solve a Problem...
I think i wrote the Logic correct but the size of that number is not fitted to any of the integer types in java

The Question is:

The Prime Factors of 13195 are 5,7,13,29
Then WHAT IS THE LARGEST PRIME FACTOR OF 600851475143

I wrote the code in Java

```

class factor 
{
	public static void main(String[] args) 
	{
		long num=600851475143; long lfact=0;
		long factors []= new long [2];
		for(long i=2; i*i<num; i++)
		{
			if(num%i==0)
			{
				factors[0]=i;
				factors[1]=num/i;
			for(int k=0;k<2;k++)
				{
				boolean isprime=true;
				for(long j=2; j*j<factors[k]; j++)
					{
					if(factors[k]%j==0)
						{
						isprime=false;
						break;
						}
					}
					if(isprime&&factors[k]>lfact)
					{
						lfact=factors[k];
					}
				}
			}
		}
	}
}

```

Can you tell me where the error lies??
and can we do that using SHELL SCRIPT too?

---

### Post by The Cog on 2012-09-24
Moved to Programming Talk

---

### Post by Majorix on 2012-09-24
Use the so called BigInteger class.

---

### Post by Mohan1289 on 2012-09-24
> **Majorix said:**
> Use the so called BigInteger class.

But if i use BigInteger i can't perform arithmatic operations in general way.. I am very New to java and i have a little idea about the BigInteger

---

### Post by Majorix on 2012-09-24
Well you WILL have to hold that large number somehow since you are going to use it for making comparisons against. I don't think there is any other way unless you use Python or Ruby or something.

---

### Post by PaulM1985 on 2012-09-24
> **Mohan1289 said:**
> But if i use BigInteger i can't perform arithmatic operations in general way.. I am very New to java and i have a little idea about the BigInteger

You could have a look at the documentation and learn about it:
[http://docs.oracle.com/javase/6/docs/api/java/math/BigInteger.html](http://docs.oracle.com/javase/6/docs/api/java/math/BigInteger.html)

Paul

---

### Post by Majorix on 2012-09-24
I think he meant that he can't use maths symbols (+, -, etc) to make calculations. He will have to write names of the methods instead, which looks ugly. I am not sure if there is a way to fix this though.

---

### Post by PoxSpax on 2012-09-24
Note: This post has been rewritten.

He could do it a little easier with a fast and simple recursive method.

I just wrote it because I was bored. haha. Banged out his answer in (according to NetBeans) 0 seconds.

EDIT: Btw, your answer is the prime factorization of 600851475143 is 71, 839, 1471, 6857.

EDIT EDIT: I redid it after trent's comment.

```

import java.util.ArrayList;
import java.math.BigInteger;
public class PrimeFactorization {

    private static ArrayList<BigInteger>primes = new ArrayList<BigInteger>();
   
    public static void main(String[] args) {
        BigInteger start = new BigInteger("600851475143");
        
        recurse(start);
        for(int i = 0; i < primes.size(); i++)
            System.out.print(primes.get(i).toString() + ", ");
    }
    
    public static void recurse(BigInteger num) {
        BigInteger i = new BigInteger("2");
        //we use these as "constants" later
        final BigInteger zero = new BigInteger("0");
        final BigInteger one = new BigInteger("1");
        //base case, num = 2; reuse i on our way 
        if(num.equals(i)) {
            primes.add(i);
            return;
        }
        
        for(; !num.mod(i).equals(zero); i = i.add(one)) {
            if(num.subtract(i).subtract(i).signum() == -1) { //this number is prime
                primes.add(num);
                return;
            }
        }
        //we found two divisors, recurse them
        recurse(i);
        recurse(num.divide(i));
    }
}

```

---

### Post by trent.josephsen on 2012-09-24
Don't use floating-point numbers to do integer arithmetic. Your version does indeed work fine for 600851475143, but it hangs on 600851475145, as well as many other numbers in the same ballpark.

---

### Post by PoxSpax on 2012-09-24
> **trent.josephsen said:**
> Don't use floating-point numbers to do integer arithmetic. Your version does indeed work fine for 600851475143, but it hangs on 600851475145, as well as many other numbers in the same ballpark.

Ahhh. I forgot to consider rounding errors. I used a double to expand the range of the value. But if it gets rounding error, that's no good is it?

Thanks for pointing it out. Rewrote it with a BigInteger implementation and updated post.

---

### Post by trent.josephsen on 2012-09-24
> **PoxSpax said:**
> Ahhh. I forgot to consider rounding errors. I used a double to expand the range of the value. But if it gets rounding error, that's no good is it?

Thanks for pointing it out. Rewrote it with a BigInteger implementation and updated post.

Props to you, looks good :)

---

### Post by Mohan1289 on 2012-09-25
> **Majorix said:**
> Well you WILL have to hold that large number somehow since you are going to use it for making comparisons against. I don't think there is any other way unless you use Python or Ruby or something.


Where can i learn PYTHON???

there aren't many sites offering python tutorials and answers for Question aroused during the coding

---

