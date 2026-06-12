---
title: "C++, issues converting decimal to fraction"
date: 2007-06-02
forum: Programming Talk
---

### Post by andrew222 on 2007-06-02
Hi all,

I am working on a C++ program that converts a decimal to a fraction, finds the lowest common multiple, multiplies the numerator by the denominator, then reduces the fraction again so the fraction will be 'numerator/1'.  

I am using this code in a larger program to change a floating point slope value to a whole value for slope-intercept equations and standard form equations. 

The program will run but I tested almost 500 numbers and 20 numbers made the program crash (it stalled and did not finish the equation, I had to close the terminal and open it up again... )

These 20 numbers I had problems with:

2.36,  7.36,  1.11,  1.001,  1.66,  1.88,  2.22,  2.13,  3.24,  3,26,  3.32,  3.43,  3.49,  3.51,  3.57,  3.68,  3.74,  3.76,  3.82  

(I am sure there are more...)

I have tried c-style casting and dynamic and static casting to try to resolve this issue. Can someone help me out and point out why these certain numbers make the program crash and offer a possible sloution?

I tried debugging this program on gdb and keep on getting this frustrating message..

(gdb) break 16
No line 16 in file "init.c".
(gdb) 


Here is the program's code, source files are attached to this thread in a tarball:

```


//example.cc
#include <iostream>
#include "reduce.h"
#include "decimal-to-fraction.h"
using namespace std;

int main()
{
	double deci;
	double n, d;

	while(1) {
		cout << "Enter a decimal to convert to a fraction ('0' to quit): ";
		cin >> deci;
		cin.ignore(INT_MAX, '\n');
		if(!deci) exit(0);
		
		dec_to_frac(deci, n, d);
		
		if (n * d != n){
			cout << '\n' << deci << " = " << n << '/' << d << "\n\n";
			cout<<'\n' << d << " x " << n;
			n = d * n;
			cout<< " = " << n << "\n\n";
			cout<<'\n' << n << '/' << d; 
			reduce(n, d);
		
			cout << " = " << n << '/' << d << "\n\n";

			cout<<'\n' << n << "\n\n";
		}
		
		else
			cout<<'\n' << deci<< "\n\n";
	
	}

	return 0;
}

#ifndef _REDUCE_H_

#error You must include "reduce.h" before this file

#endif /* def _REDUCE_H_ */



#ifndef _DECIMAL_TO_FRACTION_H_

#define _DECIMAL_TO_FRACTION_H_



void dec_to_frac(double decimal, double &numerator, double &denominator)

{

	//numerator = static_cast<int >(decimal);
	//numerator = (int )decimal;
	numerator = decimal;

	denominator = 1;
	


	while(numerator != (int)numerator) {

		numerator *= 10;

		denominator *= 10;

	}

	reduce(numerator, denominator);

}



#endif /* def _DECIMAL_TO_FRACTION_H_ */

#ifndef _REDUCE_H_

#define _REDUCE_H_



void reduce(double &numer, double &denom)

{

	int i;



	for(i=2; i<=numer; ++i) {
		

		if( ((numer/i) == ((int )(numer/i))) && ((denom/i) == ((int)(denom/i))) ) {

			numer /= i;

			denom /= i;

			--i;              

		}

	}

}



#endif /* def _REDUCE_H_ */

```

---

### Post by moma on 2007-06-02
<removed for inspection>

---

### Post by WW on 2007-06-02
The representation of real numbers in a computer is not exact.  If you say x=2.36, the actual value stored in the computer is not necessarily 2.36:

**ftest.cpp**

```

#include <iostream>
#include <iomanip>

using namespace std;

int main()
    {
    double x = 2.36;
    cout << "x = " << setprecision(20) << x << endl;
    return 0;
    }

```
```

$ g++ ftest.cpp -o ftest
$ ./ftest
x = 2.3599999999999998757
$

```

---

### Post by duaneb on 2007-06-03
Here's a quick ruby script I wrote to do this (though using a different method, I think?)
```

#!/usr/bin/ruby
# Copyright (c) Duane R. Bailey. All rights reserved.

class Fraction
  def initialize(n, d)
    @numerator = n.to_i
    @denominator = d.to_i
  end
  def + (arg)
    return Fraction.new(@numerator + (arg.to_i * @denominator), @denominator)
  end 
  def invert
    return Fraction.new(@denominator, @numerator)
  end
  def print
    puts "#{@numerator}/#{@denominator}\n"
  end
  def to_f
    return @numerator.to_f / @denominator.to_f
  end
end

def frac(num, var)
  var = var - 1
  $first = false
  n = num - num.to_i
  return Fraction.new(num.to_i + 1, 1) if var <= 0
  return (frac(1.0 / n, var).invert) + num.to_i.to_f unless $first
end

num = ARGV[0].to_f
iters = ARGV[1].to_i

num = 1.61803399 unless num > 0.0
iters = 100 unless iters > 0

(1..iters).each do |i|
  f = frac(num, i)
  f.print  
  if f.to_f == num
    exit
  end 
end

```

---

