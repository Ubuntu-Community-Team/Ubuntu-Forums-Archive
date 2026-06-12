---
title: "Factoring a number."
date: 2008-09-18
forum: Programming Talk
---

### Post by leg on 2008-09-18
I have been trying to solve this problem for a while now and I am having some problems. I am trying to find the number of factors for a number. I can find the prime factors ok and I have written a m choose n method to find the unique combinations. I still am not getting this right. I know it is not correct as it is a problem from the project euler site and my answer is rejected each time. Here is my effort:
```

import java.util.Vector;

public class problem_twelve
{
	
	public static Vector<Integer> primes;//store some prime numbers
	public static long num = 100;        //number to start searching on
	
	public static void main(String [] args)
	{
		sievePrimes();
		while(true)
		{
			long triangle = getTriangular(num);
			long ans = numDivisors(triangle) + primeFactors(triangle).size();
			if( ans > 500)
			{
				System.out.println("Stopped on " + ans);
				System.out.println("triangle number " + num + " is " + 
																	triangle);
				System.out.println("prime factors = " + primeFactors(triangle));
				System.out.println("num divisors = "  + numDivisors(triangle));
				break;
			}
			else
			{
				++num;
			}
		}		
		System.out.println(mChooseN(10, 4));
	}
	
/*
 * mChoosen
 * 
 *      m!
 *  ---------
 *  (n!)(m-n)!
 */
	public static long mChooseN(long m, long n)
	{
		return (factorial(m) / ( factorial(n) * factorial(m-n)) );				
	}
	
//return the number of factors for n
	public static long numDivisors(long n)
	{
		Vector<Integer> divs = primeFactors(n);		
						
		long [] temp = new long[divs.size()];
		for(int i = 0; i < temp.length; ++i)
		{
			temp[i] = (long)divs.elementAt(i);
		}
		
		long choices = 0; 
		for(int i = temp.length; i > 1; --i)
		{
			choices += mChooseN(temp.length, i);
		}		
		return choices;
	}
	

//find the factorial of a number
	public static long factorial(long m)
	{
		long ans = 1;
		for(long i = m; i > 0; --i)
		{
			ans *= i;
		}
		return ans;
	}
	
//get the prime factors of n
	public static Vector<Integer> primeFactors(long n)
	{
		Vector<Integer> primeDivs = new Vector<Integer>();
		
		int index = 0;
		while(n > 1)
		{	
			
			if(n % primes.elementAt(index) == 0)
			{
				n /= primes.elementAt(index);
				primeDivs.add(primes.elementAt(index));	
				index = 0;		
			}
			else
			{
				++index;
			}				
		}
		return primeDivs;
	}
	
//compute the nth triangular number
	public static long getTriangular(long n)
	{
		long sum = 0;
		for(long i = n; i > 0; --i)
		{
			sum += i;
		}
		return sum;
	}
	
//get some prime numbers
	public static void sievePrimes()
	{
		int startNum = 10000;
		primes = new Vector<Integer>();		
		int root = (int)Math.sqrt(startNum);		
		boolean [] primeStore = new boolean [startNum];
		
		for(int i = 0; i < primeStore.length; ++i)
		{
			primeStore[i] = true;
		}		
		primeStore[0] = primeStore[1] = false;
		
		for(int i = 2; i < root; ++i)
		{
			for(int j = i; j < primeStore.length; ++j)
			{
				if( j != i && j % i == 0)
				{
					primeStore[j] = false;
				}
			}
		}
		
		for(int i = 0; i < primeStore.length; ++i)
		{
			if(primeStore[i])
			{
				primes.add(new Integer(i));
			}
		}		
	}
}

```Individually the methods appear to be working for example mChooseN(10, 4) returns 210 which is correct.

I think my problem is in the numDivisors method and the way I am summing the calls to mChooseN(). The way I understand how this works is that I need to work out how many permutations there are for each grouping from 2 to n. Is this correct.

---

### Post by Reiger on 2008-09-18
Do you have to find the number of *unique* factors? OR the actual number of factors.

Because take for example 4:
It has *one* unique factor: 2.
But.
It has *two* factors: 2 and 2.

So the firs question would yied (here): 1; the latter would yield: 2.

---

### Post by leg on 2008-09-18
Unique factors so   

     1,2,4,7,14,28

are the factors of 28. This is why I have written the mChooseN method as (per my understanding) if I have the prime factors of a number the unique permutations of those primes should give me the number of factors a number has. Note I am not interested in generating a list of the factors just how many there are. The [math forum]("http://mathforum.org/library/drmath/view/56106.html") is one place I have researched this and may help you understand what I mean.

---

### Post by leg on 2008-09-18
I think I am actually going to have to work out the factors themselves for this problem. As the numbers get higher I have noticed that the prime list contains multiples of each prime number. This doesn't seem to be a problem until three of a prime is stored. for example the list of primes for the number 25200 is [2,2,2,2,3,3,5,5,7]. Now working out the combinations from the size of this list is going to be wrong as firstly working out how many combinations of two numbers exist will give me 6 combinations of 2x2. So I would be counting the number 4 six times in my list of factors. If I calculate the numbers and use a set I should be ok. I tried to use a set of primes so I calculated the combinations of [2,3,5,7] but that didn't seem to work either.

If anyone can see a flaw please let me know.

---

### Post by Reiger on 2008-09-18
No the Set thing won't work because you miss out on the 'accumulated' factors based on only 1 element of the set. I.e.: [2,3] are the only prime factors of 24. Now using a Powerset you will find you have 4 possibilities: [[], [2],[3],[2,3]]. But in actual fact the value 4 and 8 need to be accounted for.

A simple Haskell solution would be:
```

module Factors where
isDivisibleBy = \x y -> x `mod` y == 0

numFactors = \x-> length $ filter (isDivisibleBy x)) [1..x]

```

EDIT Or for the fans of list comprehension:
```

numFactors = \x-> length [y | y<-[1..x], x `isDivisibleBy` y]

```

---

### Post by leg on 2008-09-24
As it turns out I was a little off in what I should have been doing. There is a very simple way to count how many factors the number has. I won't state it here just in case any one else is trying to work through project euler. I don't want to spoil their fun.

---

