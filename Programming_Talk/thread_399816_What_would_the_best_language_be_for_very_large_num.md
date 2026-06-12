---
title: "What would the best language be for very large numbers?"
date: 2007-04-02
forum: Programming Talk
---

### Post by cprofitt on 2007-04-02
I want to write a program that will determine if a number is a Lychrel number, but curious what programming language allows for very large numbers.

Thanks.

---

### Post by raja on 2007-04-02
Python can handle very large numbers and will also be very easy to write the code in. I would suggest trying python with numpy.

---

### Post by WW on 2007-04-02
You need a library that can handle arbitrarily large integers.  You could use C with the [GNU MP]("http://gmplib.org/") library. (Has the GNU MP web page always been in French?  The [online manual]("http://gmplib.org/manual/") is in English.)

You could also use C++ with the [CLN library]("http://www.ginac.de/CLN").

You can see an example of both of these [here]("http://math.colgate.edu/~wweckesser/software/cln").

---

### Post by cprofitt on 2007-04-02
Thanks WW -- those look like good possibilities.

raja -- what is the largest integer Python can handle... I am talking about integers with millions of places.

---

### Post by b1g4L on 2007-04-02
Integers that large may not be ideal for computing on a desktop computer. The time it would take to calculate anything would probobly take days...

---

### Post by samjh on 2007-04-02
> **PrivateVoid said:**
> Thanks WW -- those look like good possibilities.

raja -- what is the largest integer Python can handle... I am talking about integers with millions of places.

I've just tried:
```
print 10 ** 1000000
```which froze the Python interpreter.

But the following command worked OK, but there was a delay of around 3 seconds while it was processed:
```
print 10 ** 100000
```

Using the power of 10000 was almost instant, but there was a perceptible delay.

So it looks like Python will handle up to 10,000 places without suffering severe performance problems.  My machine is upper-middle spec: Intel Core 2 Duo 6300, 2GB DDR RAM, etc.  Your mileage may vary.

**[EDIT: Added result using Java]**

I've also tried the same as above, using Java.  I used the java.math.BigInteger class:
```
import java.math.BigInteger;

public class ArbInt {
	public static void main (String args[]) {
		BigInteger x = new BigInteger("10");
		x = x.pow(1000000);
		String huge = new String();
		huge = x.toString();
		System.out.println(huge);
	}
}
```

Similar result: good performance up to 10.000 places, sluggish at 100,000 places, hangs the JVM at 1,000,000 places.

**[EDIT: Revised results WITHOUT output to console]**

I've just retried the above methods, without outputting to console.  So these are merely 10 to the power of 1000000, within system memory only.  No printing.

Using Python, it was able to x = 10 ** 1000000 after around two seconds.  But using x = 10 ** 10000000 hung the interpreter.  So heavy calculations involving up to 1 million digits is possible using Python, but the performance penalty is heavy.

Using Java, doing x = x.pow(1000000) was also possible, but the delay was around 15 seconds.  So it was slower than Python.

---

### Post by WW on 2007-04-02
> **b1g4L said:**
> The time it would take to calculate anything would probobly take days...
...or even years: [Lychrel number at wikipedia]("http://en.wikipedia.org/wiki/Lychrel_number"). (Check out the section called "196 palindrome quest".)

---

### Post by cprofitt on 2007-04-02
I am not concerned with the time it takes -- I am concerned that it will not error out due to a limit on the size of integers; that was the problem I had when using .Net.

---

### Post by WW on 2007-04-02
This piqued my curiousity, so I had to try it.  It occurred to me that, since all you want to do is reverse the digits and add, even using GMP or some other big integer library is probably overkill.  Here is a C++ program that implements a class just for doing Lychrel computations:
```

//
// lychrel.cpp
//

#include <iostream>
#include <string>
#include <vector>
#include <cstdlib>

using namespace std;

class Linteger
    {
    private:

    // digits is a vector of the digits of the number
    // digits[0] is the least significant digit
    vector<char> digits;

    public:

    Linteger(string s);
    Linteger(long m);
    void next();
    bool is_palindrome();
    long num_digits();
    void print();
    };

Linteger::Linteger(string s)
    {
    for (string::reverse_iterator p = s.rbegin(); p != s.rend(); ++p)
        digits.push_back(*p - '0'); 
    }

Linteger::Linteger(long m)
    {
    while (m > 0)
        {
        digits.push_back((char)(m%10));
        m = m / 10;
        }
    }

void Linteger::next()
    {
    vector<char> rdigits;

    for (vector<char>::reverse_iterator p = digits.rbegin(); p != digits.rend(); ++p)
        {
        rdigits.push_back(*p);
        }
    size_t n = digits.size();
    int carry = 0;
    for (int i = 0; i < n; ++i)
        {
        int s = digits[i] + rdigits[i] + carry;
        digits[i] = s % 10;
        carry = s/10;
        }
    if (carry != 0)
        digits.push_back(carry);
    }

bool Linteger::is_palindrome()
    {
    size_t n = digits.size();
    for (int i = 0; i < n/2; ++i)
        if (digits[i] != digits[n-i-1])
            return false;
    return true;
    }

long Linteger::num_digits()
    {
    return digits.size();
    }

void Linteger::print()
    {
    for (vector<char>::reverse_iterator p = digits.rbegin(); p != digits.rend(); ++p)
        {
        cout << (int) *p;
        }
    cout << endl;
    }


int main(int argc, char **argv)
    {
    if (argc != 3)
        {
        cerr << "use: lychrel integer max_iterations\n";
        return -1;
        }

    Linteger N(argv[1]);
    int m = atoi(argv[2]);

    int k = 0;
    while(!N.is_palindrome() & (k < m))
         {
         N.next();
         ++k;
         }
    if (N.is_palindrome())
        {
        cout << argv[1] << " resulted in a palindrome after " << k << " iterations.\n";
        N.print();
        }
    else
        {
        cout << argv[1] << " did not result in a palindrome after " << k << " iterations. (" << N.num_digits() << " digits)\n";
        }
    return 0;
    }

```
Here are a couple sample runs:
```

$ time ./lychrel 196 100000
196 did not result in a palindrome after 100000 iterations. (41490 digits)

real    6m39.460s
user    6m38.273s
sys     0m0.448s
$ time ./lychrel 89 200
89 resulted in a palindrome after 24 iterations.
8813200023188

real    0m0.004s
user    0m0.000s
sys     0m0.004s
$

```

---

### Post by cprofitt on 2007-04-02
My C# code that I used below:

```
 
private void Lychrel(UInt64 i)
        {
            // will continue until iterations = 65,000
            string s = i.ToString();
            char[] reverse = s.ToCharArray();
            Array.Reverse(reverse);
            string sreverse = new string(reverse);

            // progress bar
            pgBarReg.Value += 1;

            if (s == sreverse)
            {
                _lychrel = true;
            }
            else
            {
                if (_iterations < 65000)
                {
                    _iterations += 1;
                    
                    // convert reverse to int64 and add it to i
                    i += Convert.ToUInt64(sreverse);
                    Lychrel(i);
                }                
            }
        }

```

I exceed the size allowed for UInt64 at 41 iterrations when I reach the value:
13,305,261,530,450,734,933 reverse it and try to add it to itself. I reach this in under 1s of processing time.

I will try running your code on my Ubuntu box tomorrow... it is an interesting concept... at least for me.

---

### Post by pmasiar on 2007-04-03
> **PrivateVoid said:**
> My C# code that I used below:

Looks like you use 64-bit integers, right? Python has arbitrary-length integers, just add L: 

```

>>> d = 111111111111111111111111111111111111111111111L
>>> dd = d * d
>>> dd
12345679012345679012345679012345679012345678987654320987654320987654320987654320987654321L
>>> d4 = dd * dd
>>> d4
152415790275872580399329370522786160646242950160036579789666209419295839048925468678555099222679469593049839963420210333790580704160950464868160341411370217954580094497789971041L
>>> d8 = d4 * d4
>>> d8
23230573125418774637910283573050778943185939574816860034472776683733936436180586205392973555407390960161634610914963766926637687455914330849961835652940905766086109090632013527814813118982976659244266247364113982107951962239911374434303602358005386751757468356300587913025942208234629531945069637243682277216887204765259588529402738944970976999618623681L

```

results are fast.

---

### Post by lnostdal on 2007-04-03
SBCL (or Common Lisp in general) has also got support for arbitrary long integers:

```

Test> (time
       (let* ((d 111111111111111111111111111111111111111111111)
              (d2 (* d d))
              (d4 (* d2 d2))
              (d8 (* d4 d4)))
         (princ d2) (terpri)
         (princ d4) (terpri)
         (princ d8) (terpri)))
        

12345679012345679012345679012345679012345678987654320987654320987654320987654320987654321
152415790275872580399329370522786160646242950160036579789666209419295839048925468678555099222679469593049839963420210333790580704160950464868160341411370217954580094497789971041
23230573125418774637910283573050778943185939574816860034472776683733936436180586205392973555407390960161634610914963766926637687455914330849961835652940905766086109090632013527814813118982976659244266247364113982107951962239911374434303602358005386751757468356300587913025942208234629531945069637243682277216887204765259588529402738944970976999618623681
Evaluation took:
  0.005 seconds of real time
  0.004 seconds of user run time
  0.0 seconds of system run time

```

..I bet most of that time is spent printing the result.

edit:
It switches from a native numeric type to a bignum type automatically when needed .. so code using smaller numbers will be very fast, especially when declarations are added (as fast as C .. sometimes faster: [http://www.lrde.epita.fr/cgi-bin/twiki/view/Publications/200606-IMECS](http://www.lrde.epita.fr/cgi-bin/twiki/view/Publications/200606-IMECS) ).

---

### Post by Ubuntist on 2007-04-03
> **PrivateVoid said:**
> I want to write a program that will determine if a number is a Lychrel number, but curious what programming language allows for very large numbers.

Thanks.

Common Lisp can handle large numbers and can even handle integers or rationals in arbitrary bases.  Common Lisp also allows you to compile your code for speed of execution.

---

### Post by cprofitt on 2007-04-03
Looks like I need to learn Python or Lisp... now I am off to do some reading...

Thanks guys!

---

### Post by dwblas on 2007-04-03
Python's decimal type claims that numbers can be as large as needed
> Unlike hardware based binary floating point, the decimal module has a user settable precision (defaulting to 28 places) which can be as large as needed for a given problem:from this link
[http://docs.python.org/lib/module-decimal.html](http://docs.python.org/lib/module-decimal.html)
However, if you are dealing with very large numbers you don't want to consider using anything other than C/C++ or assembly.  Other languages AFAIK will multiply the execution time by some multiple.

---

### Post by pmasiar on 2007-04-03
> **dwblas said:**
> However, if you are dealing with very large numbers you don't want to consider using anything other than C/C++ or assembly.

Yes, C/Asm solution would run faster, but "best solution" also depends on how often I plan to run the program, and how fast I need the solution. If I plan to run it 5 times, and can hack in 2 hours Python code which runs 10 minutes, Python might be "better" than spending week on Asm code which runs 5 sec. Heck, let it run overnight and get some sleep :-)

---

### Post by dwblas on 2007-04-03
If 10 to 20 minutes running time is OK, then you are in Python's ballpark.  I've used significant digits in the 30-40 range, but nothing larger.  I will try a for loop tomorrow, multiplying by 10 each time to see how high it will go.

Edit: Running this code went up to 10,000 digits with no problem.  The time was
real    15m20.478s
user    13m3.797s
sys     0m1.976s
so doing anything with numbers in the 10,000 digit range will literally take days or weeks.
```
import decimal                                                                       
                                                                                     
number = decimal.Decimal( 1 )                                                        
incr = decimal.Decimal( 10 )                                                         
decimal.getcontext().prec = 10002                                                    
for j in range( 0, 10000 ) :                                                         
   number *= incr                                                                    
   print len(str(number))
```

---

