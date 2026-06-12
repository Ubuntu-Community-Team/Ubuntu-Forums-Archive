---
title: "Need help calculating PI in C++"
date: 2011-04-28
forum: Programming Talk
---

### Post by jordanae on 2011-04-28
I'm writing a function in my program to calculate PI based on how far (in terms) the user wants it to go. The equation is PI = 4(1/1 – 1/3 + 1/5 – 1/7 + 1/9 – 1/11 + 1/13 – …) but I'm having a hard time getting it right. 
```

int piapprox() {
	int termnumb, count=0;		
	float sum=0.0, denom=-1.0;
	cout << "Number of terms: ";	
	cin >> termnumb;							//Input number of terms
	while (count != termnumb) {						//Loops until the loop has executed as many times as there are terms (termnumb)
		count++;
		denom = denom+2;						//Increases denominator by 2
		if (count % 2 != 0) {						//If the loop has executed an even amount of times...
			sum = sum + 1/denom;					//...add 1/denominator to sum
		}
		else {								//If the loop has executed an odd amount of times...
			sum = sum - 1/denom;					//...subtract 1/denominator 
		}
		}
		cout << "PI with " << termnumb << " terms is: " << 4.0*sum;	//Outputs the equation PI = 4(1/1 – 1/3 + 1/5 – 1/7 + 1/9 – 1/11 + 1/13 – …)
	}

```

---

### Post by ve4cib on 2011-04-28
What problem are you encountering?  It's hard for us to help when you don't tell us what the problem is and what you've already tried to do to fix it.

---

### Post by jordanae on 2011-04-28
Oh, sorry, I had to rush through posting that. Well the out come is never 3.anything. For example if you want 12 terms you get 8.897411. 13 terms, 8.897411. You might be able to get more of an idea if you compile it.

---

### Post by jordanae on 2011-04-28
And as far as what I tried to fix it was just declaring some previous ints as float points. Specifically sum and denom since I was dividing/multiplying them.

---

### Post by stchman on 2011-04-28
That function will take a VERY long time to approximate pi.

Here is one I have written in Java that takes ~62 secs.

[PHP]
import java.util.*;
import java.io.*;

public class CalculatePI {
    public static void main( String[] args ) {
        CalculatePI m = new CalculatePI();
        m.calculatePI();
    }

    public void calculatePI() {
        /* use the infinite series
         * 
         *    inf    (-1)^k
         * 4 * E  --------------
         *    k=0   (2k + 1)
         * 
         */
        
        double frac = 0.0, sum = 0.0;
        double startTime = 0.0, endTime = 0.0;
         
        // set the start time
        startTime = System.currentTimeMillis();
         
        // run the series
        for( int k = 0; k <= 1000000000; k++ )
        {
            frac = 0.0;
            frac = 4 * Math.pow( -1.0, (double)k ) / ( 2.0 * (double)k + 1 );
            sum += frac;
        }
        
        endTime = System.currentTimeMillis();

        System.out.println( "pi = " + sum );
        System.out.println( "pi = 3.14159265358979323846264338327950288" ); 
        System.out.println( "Time to calculate pi = " + ( endTime - startTime ) / 1000.0 + "secs" );
    }
}
[/PHP]Here is it written in C and it take ~59 secs.  Not a huge time difference.

[PHP]
/*
calculate PI
*/

#include <stdio.h>
#include <math.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>

// main function
int main( int argc, char *argv[] )
{
    /* use the infinite series
         * 
         *    inf    (-1)^k
         * 4 * E  --------------
         *    k=0   (2k + 1)
         * 
         */
        
    int k = 0;
    double frac = 0.0, sum = 0.0;
    double init_time = 0.0, final_time = 0.0, total_time = 0.0;
    
    // set initial time
    init_time = clock();
    
    // run the series
    for( k = 0; k <= 1000000000; k++ )
    {
        frac = 0.0;
        frac = 4 * pow( -1.0, (double)k ) / ( 2.0 * (double)k + 1 );
        sum += frac;
    }

    // set final time
    final_time = clock();
    
    // calculate total time, the clock parameter is in milliseconds
    total_time = (double)( final_time - init_time ) / 1000.0;
    
    printf( "pi = %12.15f\n", sum );
    printf( "pi = 3.14159265358979323846264338327950288" );
    printf( "Total time to calculate PI = %.3f seconds\n", total_time );

    return 0;
}
[/PHP]

---

### Post by Some Penguin on 2011-04-28
There's something very odd about a function named 'piapprox' that is declared to return an int.

---

### Post by BkkBonanza on 2011-04-28
Both of these are limited by double/float. It would be far more interesting to see an arbitrary length PI calculator - though I'm sure a few minutes on google would turn one up.

OP, try casting your 1/denom expression or indicating that 1 is not an int. eg.

(double)1/denom or 1.0/denom

---

### Post by Arndt on 2011-04-29
> **jordanae said:**
> Oh, sorry, I had to rush through posting that. Well the out come is never 3.anything. For example if you want 12 terms you get 8.897411. 13 terms, 8.897411. You might be able to get more of an idea if you compile it.

I did.

```
$ ./computepi
Number of terms: 12
PI with 12 terms is: 3.0584$

```

```
$ ./computepi
Number of terms: 10000
PI with 10000 terms is: 3.1415$

```
Looks alright to me.

---

### Post by Some Penguin on 2011-04-29
> **jordanae said:**
> Oh, sorry, I had to rush through posting that. Well the out come is never 3.anything. For example if you want 12 terms you get 8.897411. 13 terms, 8.897411. You might be able to get more of an idea if you compile it.

How would you suggest that we compile a single function that is clearly incomplete, considering that it has a non-void return type and a complete lack of return statements?

---

### Post by Arndt on 2011-04-29
> **Some Penguin said:**
> How would you suggest that we compile a single function that is clearly incomplete, considering that it has a non-void return type and a complete lack of return statements?

You're being silly. Yes, it's not right to demand that we make the code snippet into a working program, but it's perfectly trivial to do so in this case. It would have taken you less time to do it than to write your two posts on the subject.

For being able to reproduce an error reliably, it is a good thing to provide a complete program, a complete command line for building it, input, and the perceived faulty output. That point does deserve making.

---

### Post by Arndt on 2011-04-29
> **stchman said:**
> That function will take a VERY long time to approximate pi.

Here is one I have written in Java that takes ~62 secs.

[PHP]
import java.util.*;
import java.io.*;

public class CalculatePI {
    public static void main( String[] args ) {
        CalculatePI m = new CalculatePI();
        m.calculatePI();
    }

    public void calculatePI() {
        /* use the infinite series
         * 
         *    inf    (-1)^k
         * 4 * E  --------------
         *    k=0   (2k + 1)
         * 
         */
        
        double frac = 0.0, sum = 0.0;
        double startTime = 0.0, endTime = 0.0;
         
        // set the start time
        startTime = System.currentTimeMillis();
         
        // run the series
        for( int k = 0; k <= 1000000000; k++ )
        {
            frac = 0.0;
            frac = 4 * Math.pow( -1.0, (double)k ) / ( 2.0 * (double)k + 1 );
            sum += frac;
        }
        
        endTime = System.currentTimeMillis();

        System.out.println( "pi = " + sum );
        System.out.println( "pi = 3.14159265358979323846264338327950288" ); 
        System.out.println( "Time to calculate pi = " + ( endTime - startTime ) / 1000.0 + "secs" );
    }
}
[/PHP]Here is it written in C and it take ~59 secs.  Not a huge time difference.

[PHP]
/*
calculate PI
*/

#include <stdio.h>
#include <math.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>

// main function
int main( int argc, char *argv[] )
{
    /* use the infinite series
         * 
         *    inf    (-1)^k
         * 4 * E  --------------
         *    k=0   (2k + 1)
         * 
         */
        
    int k = 0;
    double frac = 0.0, sum = 0.0;
    double init_time = 0.0, final_time = 0.0, total_time = 0.0;
    
    // set initial time
    init_time = clock();
    
    // run the series
    for( k = 0; k <= 1000000000; k++ )
    {
        frac = 0.0;
        frac = 4 * pow( -1.0, (double)k ) / ( 2.0 * (double)k + 1 );
        sum += frac;
    }

    // set final time
    final_time = clock();
    
    // calculate total time, the clock parameter is in milliseconds
    total_time = (double)( final_time - init_time ) / 1000.0;
    
    printf( "pi = %12.15f\n", sum );
    printf( "pi = 3.14159265358979323846264338327950288" );
    printf( "Total time to calculate PI = %.3f seconds\n", total_time );

    return 0;
}
[/PHP]

Does it affect the times if you compute the sign by multiplying by -1 each time, rather than using 'pow'?

---

### Post by Some Penguin on 2011-04-29
> **Arndt said:**
> You're being silly. Yes, it's not right to demand that we make the code snippet into a working program, but it's perfectly trivial to do so in this case. It would have taken you less time to do it than to write your two posts on the subject.

For being able to reproduce an error reliably, it is a good thing to provide a complete program, a complete command line for building it, input, and the perceived faulty output. That point does deserve making.

Here, the point may be extremely relevant.  After all, if the math looks superficially correct (and floating point precision vs double isn't *that* bad; it is highly unlikely to accumulate sufficient errors to produce the claimed error), another possibility is that the OP isn't simply using the value that's bring printed in the snippet, but is dealing with an uninitialized variable (which would possibly explain the identical output!), bad casting, or both.  In other words, the snippet is not particularly useful.

I'm betting that the OP hasn't bothered with compiling using -Wall and resolving every warning.

---

### Post by Arndt on 2011-04-29
> **Some Penguin said:**
> Here, the point may be extremely relevant.  After all, if the math looks superficially correct (and floating point precision vs double isn't *that* bad; it is highly unlikely to accumulate sufficient errors to produce the claimed error), another possibility is that the OP isn't simply using the value that's bring printed in the snippet, but is dealing with an uninitialized variable (which would possibly explain the identical output!), bad casting, or both.  In other words, the snippet is not particularly useful.

I'm betting that the OP hasn't bothered with compiling using -Wall and resolving every warning.

It will be interesting to see what the error was. For what it's worth, here's my "trivial" encapsulation:
```

$ cat computepi.cc
#include <iostream>
using namespace std;

int piapprox() {
	int termnumb, count=0;		
	float sum=0.0, denom=-1.0;
	cout << "Number of terms: ";	
	cin >> termnumb;							
//Input number of terms
	while (count != termnumb) {						
//Loops until the loop has executed as many times as there are terms (termnumb)
		count++;
		denom = denom+2;						
//Increases denominator by 2
		if (count % 2 != 0) {						
//If the loop has executed an even amount of times...
			sum = sum + 1/denom;					
//...add 1/denominator to sum
		}
		else {								
//If the loop has executed an odd amount of times...
			sum = sum - 1/denom;					
//...subtract 1/denominator 
		}
		}
		cout << "PI with " << termnumb << " terms is: " << 4.0*sum;	
//Outputs the equation PI = 4(1/1 – 1/3 + 1/5 – 1/7 + 1/9 – 1/11 + 1/13 – …)
	}

int main()
{
  piapprox();
}
$ g++ -Wall -o computepi computepi.cc
computepi.cc: In function ‘int piapprox()’:
computepi.cc:20: warning: no return statement in function returning non-void

```

---

### Post by nvteighen on 2011-04-30
Related to the above is the fact that the OP is mixing implementation and interface. The approximation function shouldn't get any user input, but a proper argument list.

```

#include <iostream>
#include <cmath>

double piapprox(const unsigned int terms)
{
    double sum = 0.0;
    const double k = static_cast<const double>(terms);

    for(double i = 0; i <= k; i++)
        sum += 4 *(std::pow(-1.0, i) / (2.0 * i + 1.0));

    return sum;
}

int main()
{
    std::cout << "Enter how many terms to use for approximating PI: " 
              << std::endl;

    unsigned int terms = 0;
    std::cin >> terms;

    double my_pi = piapprox(terms);

    std::cout << "PI is approximately: " << my_pi << std::endl;

    return 0;
}

```

As you see, my function can be used for any argument regardless of its origin (user input, some other computation, a constant hardcoded value, etc.). I just pass the argument and I get a result. The user input is handled elsewhere, so I could write a GUI, a network-based interface or whatever I liked without modifying piapprox.

EDIT: Somehow, I posted without stating my real point. The problem with mixing implementation and interface in the OP's code leads to several issues pointed out by the posts above: specially, the lack of a return value, where one is certainly needed.

---

### Post by stber321 on 2011-04-30
> **jordanae said:**
> I'm writing a function in my program to calculate PI based on how far (in terms) the user wants it to go. The equation is PI = 4(1/1 – 1/3 + 1/5 – 1/7 + 1/9 – 1/11 + 1/13 – …) but I'm having a hard time getting it right. 
```

int piapprox() {
    int termnumb, count=0;        
    float sum=0.0, denom=-1.0;
    cout << "Number of terms: ";    
    cin >> termnumb;                            //Input number of terms
    while (count != termnumb) {                        //Loops until the loop has executed as many times as there are terms (termnumb)
        count++;
        denom = denom+2;                        //Increases denominator by 2
        if (count % 2 != 0) {                        //If the loop has executed an even amount of times...
            sum = sum + 1/denom;                    //...add 1/denominator to sum
        }
        else {                                //If the loop has executed an odd amount of times...
            sum = sum - 1/denom;                    //...subtract 1/denominator 
        }
        }
        cout << "PI with " << termnumb << " terms is: " << 4.0*sum;    //Outputs the equation PI = 4(1/1 – 1/3 + 1/5 – 1/7 + 1/9 – 1/11 + 1/13 – …)
    }

```


well first of all it may be helpful not to return an int and i do not even see where you are returning, also you could just define a const long double PI=many many digits then use floor and cel to round

for many many digits see [http://www.math.utah.edu/~pa/math/pi.html]("http://www.math.utah.edu/%7Epa/math/pi.html")
 
that seems like the easest option if you are not writing a program that NEEDS to calculate pi

---

### Post by Arndt on 2011-05-04
Would the original poster like to enlighten us what the error was? We could learn from it.

---

