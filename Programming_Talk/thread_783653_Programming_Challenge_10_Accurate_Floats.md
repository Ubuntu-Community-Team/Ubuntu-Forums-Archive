---
title: "Programming Challenge 10: Accurate Floats"
date: 2008-05-05
forum: Programming Talk
---

### Post by mssever on 2008-05-05
[COLOR=Red]**Note the updated deadline below!**[/COLOR]

Many languages have trouble with floating-point numbers, due to differences between binary and decimal. For example, 0.1 + 0.2 == 0.3, but in Python: ```
>>> 0.1 + 0.2
0.30000000000000004
```Your challenge is to solve that problem. Essentially, you need to provide accurate base-10 floats.

[SIZE=4]** Requirements**[/SIZE]
Your submission should, at the minimum, meet all of the following requirements:

[LIST]
[*]Write a library that accurately stores any floating point number to at least the same precision as your language's native floats.
[*]The library should be able to accurately calculate, at the minimum, one of addition, subtraction, multiplication, or division. For example, given 0.1 + 0.2, it should return 0.3. Entries that handle all four will have an advantage.
[*]Include a way to cast your floats to a string (or something equivalent) for the purposes of printing the number.
[*]Your submission must be a library (it must be usable by another program).
[*]Include a test program to verify that your library works correctly. It must be separate from the library. However, if your language supports something similar to Python's [FONT=Courier New]if __name__ == '__main__':[/FONT] feature, you may use it provided that your library is still separated from the test stub.

The test program should implement one of the following interfaces:
[LIST=1]
[*]It will get three arguments on the command line: a number, an operator (+-*/), another number. At least one of the numbers will be a floating point number. It should solve the math problem and print the answer (optionally followed by \n) to stdout. If the requested operation isn't supported, it should print "Not supported" to stdout. Any other chatter should go to stderr. This program will be called repeatedly by a script, so long startup times are discouraged. Example bash session: ```
~/programming/snippets/programming challenges/floats:$ ./your_program "0.1" "+" "0.2"
0.3
~/programming/snippets/programming challenges/floats:$
```
[*]It should provide a multi-line input box which will accept expressions in the form number operator(+-*/) number where at least one number is a float. Each expression will be on a line by itself, and there will be more than one expression to process. When told to do the math, it should process all input and return the results, one per line.
[/LIST]
You should use option 1 unless it isn't feasible for your language. Option 2 exists primarily for the benefit of Javascript, which can't print to stdout.
[*]It isn't necessary to handle large numbers. All test numbers will be in the range 5000...-5000 and use no more than 6 decimal places.
[*]As always, you aren't allowed to use any pre-existing libraries to implement your accurate floats. Your test program, however, may use whatever libraries you like to enable input/output/whatever else may be necessary.
[/LIST]

[SIZE=4]**Recommendations**[/SIZE]
These items aren't required, but implementing them will get you extra points.
[LIST]
[*]Integrate your floats such that when your library is imported (or a switch is toggled) all floats become your floats, not the language's built in floats. There's a big bonus for this.
[*]Simply rounding your floats to achieve the effect of accurate floats is frowned upon.
[*]Elegant code is a Good Thing. If you make your code easy to read and understand, that's even better.
[*]Documenting each library method/function is a Good Thing.
[*]Make your floats work with a full math library.
[/LIST]

[SIZE=4]**Languages**[/SIZE]
This challenge is meaningless in some languages. For example, Ruby has accurate floats built in, so there's no point in making a Ruby implementation (EDIT: Actually, I just discovered that Ruby fails my test script, so it's not pointless). Also, if the proper compiler/interpreter isn't available from the official Ubuntu repositories (including the universe and multiverse), then I won't test it. And if I don't test it, it's difficult to win. :) Finally, I consider solutions in Javascript and Python to be particularly interesting, with Javascript being more interesting than Python (hint, hint). That doesn't mean, though, that a Javascript or Python entry will automatically win over another language; the other criteria mentioned are much more important.

Oh, and don't forget to include build/run instructions if you use an uncommon language.

[SIZE=4]**Deadline [COLOR=Red](Updated)[/COLOR]**[/SIZE]
I will begin judging on Sunday, May 11 at 8:00 pm US Central Time (Monday, 01:00 GMT).

---

### Post by nvteighen on 2008-05-06
A question: does C have this problem? I've been printing floats with printf and is I set output precision bigger than the variable's I get some inaccuracy.

Here's a sample code that illustrates what I mean:

[PHP]
#include <stdio.h>

int main(void)
{
	const float a = 0.1 + 0.3;
	printf("%.100f", a); /*printing with precision 100*/
	
	return 0;
}
[/PHP]

---

### Post by mssever on 2008-05-06
> **nvteighen said:**
> A question: does C have this problem?
Your code prints ```
0.4000000059604644775390625000000000000000000000000000000000000000000000000000000000000000000000000000
``` but it should print ```
0.4000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
``` so yes, your code has this problem. I don't really know C, so I can't comment on the specifics.

---

### Post by samjh on 2008-05-06
> **mssever said:**
> Write a library that accurately stores any floating point number to at least the same precision as your language's native floats.
Can we get a clarification on what you mean by this?

By "precision", are you talking about the minimum and maximum exponential of 10, or the number of significant digits?  For example, Ada's standard Float has a range from 10^-128 to 10^128 but the maximum number of significant digits is only 6.

So is it necessary to make the float accurate to 10^+/-128 or just 6 digits?  I'm hoping for the latter! :p

---

### Post by mouldy on 2008-05-06
I think the OP means get more accurate results than the language's own way of dealing with floats. So while the language might get 0.3004 when doing 0.1+0.2, your library might get 0.300001 - which would be more accurate.

I suppose the easiest way to do that would be to change the number of bits in the mantissa.

---

### Post by RIchard James13 on 2008-05-06
Although one could change the number of bits, is that the only way to solve the problem? I don't believe so. You could change to Base 10 which solves the fractional conversion to binary problem. I did a lot of reading on this subject this afternoon, I think what is more important than moving that error away is to ensure that in multiple calculations the error is minimised. One might say that increasing the number of bits is similar to just rounding the floats, you have not solved the problem you just hid it. Is there a better way? ;)

---

### Post by ibuclaw on 2008-05-06
Or we could write a piece of code that doesn't treat the float as an entire number. But as separate numbers that the app adds together to get an accurate model.

ie:
```

0.1 + 0.2

Translated into:
    0.1000000
    0.2000000

And from left to right add the n values of top + down.
    (0+0=0),(0+0=0),etc,etc,(1+2=3),(0+0=0).

So you get the answer:
    0.3000000

```

I'm just working on this idea right now...

Regards
Iain

---

### Post by mssever on 2008-05-06
> **samjh said:**
> Can we get a clarification on what you mean by this?

By "precision", are you talking about the minimum and maximum exponential of 10, or the number of significant digits?  For example, Ada's standard Float has a range from 10^-128 to 10^128 but the maximum number of significant digits is only 6.

So is it necessary to make the float accurate to 10^+/-128 or just 6 digits?  I'm hoping for the latter! :p

If you're accurate to six decimal places, you'll pass my test script. But I'm looking for something more than just rounding.

HINT: A solution could involve creating a custom data type/class to store your floats.

---

### Post by mssever on 2008-05-06
> **mouldy said:**
> I think the OP means get more accurate results than the language's own way of dealing with floats. So while the language might get 0.3004 when doing 0.1+0.2, your library might get 0.300001 - which would be more accurate.
0.300001 would be an improvement, but it doesn't solve the problem. To solve the problem, you need to get 0.3.

---

### Post by WW on 2008-05-06
Just a couple comments...

The (default) floating point numbers in Ruby have the same problems as those in Python or C++, but Ruby "hides" it.  When you add 0.1+0.2 and print the result, you get 0.3, but the actual value is not 0.3:
```

$ irb
irb(main):001:0> 0.1+0.2
=> 0.3
irb(main):002:0> 0.1+0.2 == 0.3
=> false
irb(main):003:0> 

```
To get around this in Ruby, you can use BigDecimals.

One *could* approach this problem by building an arbitrary precision representation of numbers (see, for example, [Programming Challenge 3](http://ubuntuforums.org/showthread.php?t=716010) as a possible starting point).  Or one could use standard floating point, but implement a string conversion that recognizes the each number actually corresponds to a tiny interval, and creates the most compact decimal representation of a number in that interval. Or ... ? 

Here's a question: What "should" the test program print when the input is "1.0" "/" "3.0"?

---

### Post by RIchard James13 on 2008-05-06
I thought of trying to make 0.1 a sum of smaller fractions like 0.02 + 0.08 but it appears that won't work due to the way the fractions are composed in binary.

Each number is 0. + b1x1/2 + b2x1/4 + b3x1/8 +b4x1/16 ....
where b1,b2 are the bits set so 0.1 is
0.00011001100110011001100110011001100110011001100110011
and I can't see any smaller fractions than 0.5 which are non-recurring
0.5 is 0.01
0.05 is 
0.00001100110011001100110011001100110011001100110011001
Which just seems to be 0.1 pushed back by 1 binary place which makes sense when you consider 0.05 + 0.05 = 0.1

But there are non-recurring fractions but can they be used as composites?

Can't help but wonder if this is all backwards

---

### Post by nvteighen on 2008-05-06
OK, confirmed with some sources: C's float type is also inaccurate.

Splitting the float into a custom data structure seems the best way to follow, as it is done in the GMP Library (GNU Multi-Precision)...

Not sure if I'll be able to take part this time due to work, but I'll try.

---

### Post by mssever on 2008-05-06
> **WW said:**
> The (default) floating point numbers in Ruby have the same problems as those in Python or C++, but Ruby "hides" it.So I noticed after writing my test script. Ruby doesn't completely hide its error, either: ```
~:$ irb
>> 1.1 - 1.2
=> -0.0999999999999999
```> To get around this in Ruby, you can use BigDecimals.Which suggests that people could use that class as a hint, if necessary.

> Here's a question: What "should" the test program print when the input is "1.0" "/" "3.0"?A reasonable approximation. Numbers that can't be precisely represented in base 10 are beyond the scope of this challenge. The results of all my test inputs can be precisely represented using no more than 6 decimal places and are in the range 5000 > x > -5000.

---

### Post by ibuclaw on 2008-05-06
**UPDATED: FIXED SEVERAL BUGS. THE APP IS NOW 100% USABLE FOR THE MINIMAL TASK IT HAS TO HANDLE**
BASH doesn't handle floats, except with the aid of other apps (which I won't use).

So I'll make my project an attempt to implement the ability to appear to use floats as throughly and solid as possible using only BASH shell script.
```

#!/usr/bin/env bash

num()
{
    export len=${#1}
    export i=0
    while [ $len -ge $i ]
    do export ch=${1:$i:1}
       if [ "$ch" != "." ]
       then export ans=$ans$ch
            let 'i++'
       else let "i=$len+1"
       fi
    done
    echo $ans
}

dec()
{
    export len=${#1}
    export i=1
    while [ $len -ge $i ]
    do export ch=${1:$len-$i:1}
       if [ "$ch" != "." ]
       then export ans=$ch$ans
            let 'i++'
       else let "i=$len+1"
       fi
    done
    echo $ans
}

checkint()
{
    echo $1 | grep "\."
    case $? in
         1) echo $1".00"
            ;;
         0) echo $1
            ;;
    esac
}

setlength()
{
    while [ ${#xnum} -lt ${#ynum} ]
    do export xnum=0$xnum
    done

    while [ ${#ynum} -lt ${#xnum} ]
    do export ynum=0$ynum
    done

    while [ ${#xdec} -lt ${#ydec} ]
    do export xdec=$xdec"0"
    done

    while [ ${#ydec} -lt ${#xdec} ]
    do export ydec=$ydec"0"
    done
}

add()
{
    export x=$1
    export y=$2
    export len=${#x}
    export i=1
    
    while [ $len -ge $i ]
    do export xch=${x:$len-$i:1}
       export ych=${y:$len-$i:1}
       if [ "$xch" != "." ]
       then export temp="$((carry + xch + ych))"
            if [ $temp -gt "9" ]
            then export carry=${temp:0:${#temp}-1}
                 export drop=$carry"0"
                 let "temp -= $drop"
            else export carry=0
            fi
            export ans=$temp$ans
            let 'i++'
       else let 'i++'
            export decimal="$ans"
            export ans=""
       fi
    done

    while [ ${#decimal} -lt "17" ]
    do export decimal=$decimal"0"
    done

    if [ "$roff" != "" ]
    then export decimal=${decimal:0:$roff}
    fi

    if [ $carry -ge "1" ]
    then export ans=$carry$ans"."$decimal
    elif [ "$ans" == "" ]
    then export ans="0."$decimal
    else export ans=$ans"."$decimal
    fi

    echo $ans
}

if [ $# == "0" ]
then exit 1
elif [ $# == "1" ]
then export x=$(checkint $1)
     export job="add"
else case $1 in
add|sub|div|mul)
             export job=$1
             export x=$(checkint $2)
             export y=$(checkint $3)
             export roff=$4
             ;;
          *)
             if [ $# == "2" ] || [ $# == "3" ]
             then export x=$(checkint $1)
                  export y=$(checkint $2)
                  export roff=$3
                  export job="add"
             else
                  exit 1
             fi
             ;;
     esac
fi

export xnum=$(num $x)
export ynum=$(num $y)
export xdec=$(dec $x)
export ydec=$(dec $y)

setlength
export answer=$($job "$xnum.$xdec" "$ynum.$ydec")

echo $answer
exit 0

```

Since first writing, the **can-do** list has grown:
[LIST]
[*] It can **ADD** only **TWO** floats together.
[*] It can convert integers into floats.
17 decimal places is default at the current moment.(Although may up it to 38 digits.)
[*] It can trim down (**not round off**) the number of decimal places.
[*] It can input dot floats (ie: ".7") and converts them to a proper format ("0.7").
[/LIST]

**What it can't do is everything else (Subtraction, Multiplication, Division and the handling of Negative Numbers)**.

Some test samples:
[PHP]
# Your example.
$ $ ./float 0.1 0.2
0.30000000000000000

# Rounding off your example to 3 decimal places.
$ ./float 0.1 0.2 3
0.300

# Some other stuff.
$ ./float 0.1234567890987654321 0.1234567890987654321
0.2469135781975308642

$ ./float 0.98765432101234567890 0.98765432101234567890
1.97530864202469135780

$ ./float 1 2 3
3.000

$ ./float 5.321 5.123 2
10.44
# Conversions...
$ ./float 1
1.00000000000000000
[/PHP]

Is this the sort of answer you are looking for in this weeks challenge mssever?

Regards
Iain

---

### Post by Paul Miller on 2008-05-06
Are you aware of the Decimal module for Python?  It looks to me like a simple wrapper around that module would easily meet the requirements.

---

### Post by achelis on 2008-05-06
I guess this is the standard most languages uses (I know for sure Java does, but it would make sense for other languages to use it as well)

[http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754)

From what I've gathered so far you're after a base-10 representation of numbers, to replace the standard base-2 representation? 

Is there any requirements to the size of numbers the float should be able to represent, or any requirements to the number of significant digits? and number of bits the float can use ?

Found an article on precision the other day, but lost the link - will post it if I find it...

---

### Post by ibuclaw on 2008-05-06
I've updated my post. (#14)

I would love to hear you're thoughts on it mssever. So I can pickup a few pointers on what you are looking for (or not looking for) in this challenge.

Also, can you state whether or not you think BASH is a viable language to use in this challenge (as it really can only handle strings and integers).

Regards
Iain

---

### Post by Wybiral on 2008-05-06
Why the particular lenience towards JavaScript?

/me thinks that mssever is trying to get us to do his work for him :grin:

---

### Post by aamukahvi on 2008-05-06
> **Paul Miller said:**
> Are you aware of the Decimal module for Python?  It looks to me like a simple wrapper around that module would easily meet the requirements.
I was thinking the same. Here:
[PHP]#!/usr/bin/env python

from decimal import Decimal

x = 0.1
y = 0.2

def add(x, y):
	return Decimal(str(x)) + Decimal(str(y))

def subtract(x, y):
	return Decimal(str(x)) - Decimal(str(y))

def multiply(x, y):
	return Decimal(str(x)) * Decimal(str(y))

def divide(x, y):
	return Decimal(str(x)) / Decimal(str(y))

print add(0.1, 0.2)
print subtract(0.1, 0.2)
print multiply(0.1, 0.2)
print divide(0.1, 0.2)[/PHP]
The output is 

0.3
-0.1
0.02
0.5

(I guess that's against the library rule)

---

### Post by theta4 on 2008-05-06
> **Paul Miller said:**
> Are you aware of the Decimal module for Python?  It looks to me like a simple wrapper around that module would easily meet the requirements.

That would be breaking the rules. The rules state that you can't use any external libraries excluding input/output libraries.

---

### Post by ibuclaw on 2008-05-06
> **theta4 said:**
> That would be breaking the rules. The rules state that you can't use any external libraries excluding input/output libraries.

Are you sure?

Forgive me, as I don't know python that well.
But after a small play about with it, I think that it has the same fundamental flaw as ruby (trims off the float to give the impression that it is the right answer).

Here's my example:
[PHP]
$ python
Python 2.5.2 (r252:60911, Apr 21 2008, 11:12:42) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print 0.1 + 0.2
0.3
>>>
>>>
>>> if 0.1 + 0.2 == 0.3:
...     print 'TRUE'
... else:
...     print 'FALSE'
... 
FALSE
>>> 
[/PHP]

That correct me if I'm wrong, but that proves that 0.1 + 0.2 does not appear to equal 0.3 afterall... Does it?

[EDIT]
**PROOF**
I took mssevers number on his first post ("0.30000000000000004") and put it in the if statement.

The program never lies!
[PHP]
>>> if 0.1 + 0.2 == 0.30000000000000004:
...     print 'TRUE'
... else:
...     print 'FALSE'
... 
TRUE
>>> 
[/PHP]
[EDIT2]
Infact, it works for numbers from 002 through to 007... hmm.. I wonder why?
[PHP]
>>> if 0.1 + 0.2 == 0.30000000000000001:
...     print 'TRUE'
... else:
...     print 'FALSE'
... 
FALSE
>>> if 0.1 + 0.2 == 0.30000000000000002:
...     print 'TRUE'
... else:
...     print 'FALSE'
... 
TRUE
>>> if 0.1 + 0.2 == 0.30000000000000007:
...     print 'TRUE'
... else:
...     print 'FALSE'
... 
TRUE
>>> if 0.1 + 0.2 == 0.30000000000000008:
...     print 'TRUE'
... else:
...     print 'FALSE'
... 
FALSE
>>> 
[/PHP]

Regards
Iain

---

### Post by achelis on 2008-05-06
Possibly because 2 - 7 is rounded to 4. (It's a guess :) )

---

### Post by achelis on 2008-05-06
Oh well.. here's a shot written in Java. 

I've limited the number of significant digits to 4 to simplify testing. Should be able to go to 9 without much changing.

It's not exactly trying to be efficient (storage or computation-wise) but is rather a crude draft.

A short explanation:
The exponent (e) is stored in a byte.
The component (c) is stored as an int.
The component determines the amount of significant digits and the sign of the Decimal. c is limited by the constant maxDigits which is currently set to 4.

Addition:
n = n1 + n2 = c1 * 10^e1 + c2 * 10^e2 = (c1 * 10^(e1-e2) + c2) * 10^e2
Multiplication:
n = n1 * n2 = c1 * c2 * 10^(e1 + e2)
Division:
n = n1 / n2 = c1 * 10^8 / c2 * 10^(e1 - e2 - 8 )

```

public class Decimal
{
	private static byte maxDigits = 4;

	private int c;

	private byte e;

	protected Decimal(int c, byte e)
	{
		this.c = c;
		this.e = e;
		
		removeTrailingZerosFromC();
	}

	protected void removeTrailingZerosFromC()
	{
		while (("" + c).endsWith("0"))
		{
			c /= 10;
			e++;
		}				
	}

	public Decimal add(Decimal d)
	{
		if (this.e > d.e)
		{
			return addDecimals(this, d);
		}
		else
		{
			return addDecimals(d, this);
		}
	}

	private Decimal addDecimals(Decimal n1, Decimal n2)
	{
		int eDiff = n1.e - n2.e;
		if (eDiff >= maxDigits)
		{
			return n1;
		}
		long cx = n1.c * pow10(eDiff) + n2.c;

		if (digits(cx) <= maxDigits)
		{
			return new Decimal((int) cx, n2.e);
		}
		else
		{
			byte excessDigits = (byte) (digits(cx) - maxDigits);
			cx = cx / pow10(excessDigits);
			return new Decimal((int) cx, (byte) (n2.e + excessDigits));
		}
	}
	
	public Decimal multiply(Decimal d)
	{
		long cx = this.c * d.c;
		byte ex = (byte) (this.e + d.e);
		if (digits(cx) < maxDigits)
		{
			return new Decimal((int) cx, ex);
		}
		else
		{
			byte excessDigits = (byte) (digits(cx) - maxDigits);
			cx = cx / pow10(excessDigits);
			return new Decimal((int) cx, (byte) (d.e + this.e + excessDigits));
		}
	}
	
	public Decimal divide(Decimal d)
	{
		long thisc = this.c * pow10(maxDigits * 2);
		long cx = thisc / d.c;
		int ex = this.e - d.e - (maxDigits * 2);
		while (("" + cx).endsWith("0"))
		{
			cx /= 10;
			ex++;
		}
		
		if (digits(cx) < maxDigits)
		{
			return new Decimal((int) cx, (byte) ex);
		}
		else
		{
			byte excessDigits = (byte) (digits(cx) - maxDigits);
			cx = cx / pow10(excessDigits);
			return new Decimal((int) cx, (byte) (ex + excessDigits));
		}
	}

	public String toDecimalString()
	{
		String result = c + "";
		if (e > 0)
		{
			for (int i = 0; i < e; i++)
			{
				result += "0";
			}
			return result;
		}
		else if (e < 0 && e > -maxDigits)
		{
			int splitLocation = result.length() + e;
			return result.substring(0, splitLocation) + "." + result.substring(splitLocation);
		}
		else if (e < 0 && e <= -maxDigits)
		{
			int diff = -e - maxDigits;
			
			String leadingZeros = "0.";
			
			if (result.startsWith("-"))
			{
				result = result.substring(1);
				leadingZeros = "-" + leadingZeros;
			}
			
			for (int i = 0; i < diff; i++)
			{
				leadingZeros += "0";
			}
			return leadingZeros + result;
		}
		return result;
	}

	public static long pow10(int e)
	{
		long result = 1;
		for (int i = 0; i < e; i++)
		{
			result *= 10;
		}
		return result;
	}

	public static byte digits(Long n)
	{
		if (n > 0) {
			return (byte) n.toString().length();
		}
		else
		{
			return (byte) (n.toString().length() - 1);
		}
	}
}

```

---

### Post by KaeseEs on 2008-05-07
> **achelis said:**
> I guess this is the standard most languages uses (I know for sure Java does, but it would make sense for other languages to use it as well)

[http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754)


This is correct.  Furthermore, almost every modern 32- or 64-bit processor implements IEEE floating point, and sane compilers use a processor's floating-point instructions on floats and doubles.  

Finally, the inaccuracy problem is not always caused by binary/decimal conversion; rather, it is usually caused by trying to extract more precision from a datatype than it actually stores.  If you try to do decimal arithmetic on a computer, you actually end up with less precision (and considerably so) for a given amount of memory, due to the gross inefficiency of BCD encoding.

---

### Post by mssever on 2008-05-07
Wow. A lot has happened while I've been away from the computer.

> **tinivole said:**
> Is this the sort of answer you are looking for in this weeks challenge mssever?That's the general idea, especially if you move everything into functions so that you can simply source the file and do math from wherever.

> **Paul Miller said:**
> Are you aware of the Decimal module for Python?  It looks to me like a simple wrapper around that module would easily meet the requirements.Except that would be using an external lib.

> **achelis said:**
> From what I've gathered so far you're after a base-10 representation of numbers, to replace the standard base-2 representation?Yes.

> Is there any requirements to the size of numbers the float should be able to represent, or any requirements to the number of significant digits? and number of bits the float can use ?It doesn't need to be large. The test script I wrote contains no more than 6 decimal places, and all numbers are between 5000 and -5000.
> **Wybiral said:**
> Why the particular lenience towards JavaScript?

/me thinks that mssever is trying to get us to do his work for him :grin:
My secret is out! :) Actually, that's only partly the case. I do have a Javascript project that contains a long-standing, low-priority bug related to this, but that isn't my only motivation. Ever since I discovered that bug, I've been mildly intrigued by base-10 floating-point errors. I remember reading a while back about accounting software and the fact that it has to work around these issues. One of the early things I tried when I first started learning Python was to see how it handled floats.

Basically, this is a problem that's intrigued me for a while. So when I needed an idea for a programming challenge, it came to mind. It appears, though, that I might have just jumped into the deep end of the pool with a 1-ton weight strapped to me. If you (or one of the other regulars around here) think that this challenge is mis-guided, feel free to PM me with criticisms and suggestions for how to tweak the rules to improve it. After posting it, I realized that it was a lot harder than I originally thought.

The other reason why Javascript is particularly interesting to me is because it seems to be a common language that's uncommonly difficult to master (to me, at least).

---

### Post by mssever on 2008-05-07
> **achelis said:**
> Oh well.. here's a shot written in Java.
Thanks for your entry. Unfortunately, I can't run it as written. Is there a test harness?

---

### Post by mcsimon on 2008-05-07
Here goes my submission :)

It looks like i overcomplicated things way too much, but ah well. I'm a newbie, so be nice please guys :)

Only works with plus and minus at the moment. Works with any precision as large as you like though :D


The library class:    AccurateFloat.java
```



public class AccurateFloat {

	private int[] listage;
	private int pointPos;
	
	//constructor sets up an array of ints containing the int value of all characters in the string
	public AccurateFloat(String innacurateNumber) {
		String number;
		if(innacurateNumber.indexOf(".") == -1) {
			number = innacurateNumber + ".0";
		} else {
			number = innacurateNumber;
		}
		int characters = number.length();
		
		listage = new int[characters];
		pointPos = number.indexOf(".");
		for (int i = 0; i < characters; i++) {
			if (number.charAt(i) != 46) {
				listage[i] = (int)number.charAt(i) -(int)'0' ;
			} else {
				listage[i] = (int)number.charAt(i);
			}
		}
	}
	
	//returns the array as a single string
	public String getString() {
		String result = "";
		for (int i = 0; i < getLength(); i++) {
			if (getInt(i) == 46) {
				result += ".";
			} else {
				result += getInt(i);
			}
		}
		return result;
	}
	
	//returns the index of the decimal point
	public int getPoint() {
		return pointPos;
	}
	
	//returns number of entries in the array
	public int getLength() {
		return listage.length;
	}
	
	//returns the value of the int at index
	public int getInt(int index) {
		return listage[index];
	}
	
	
	//addition method. 
	public static String addition(AccurateFloat newnumber1, AccurateFloat newnumber2) {
		
		//initialise local variables
		int longest, shortest;
		AccurateFloat longa, number1, number2;			
		String output = "";
		String s = "";
		
		//if there aren't the same number of characters left of the decimal point, fill up the shorter one with zero's until the 
		//decimal points line up, output the lined up numbers as AccurateFloat objects number1 and number2
		if (newnumber1.getPoint() < newnumber2.getPoint()) {
			for (int i = 0; i < (newnumber2.getPoint() - newnumber1.getPoint()); i++) {
				s += "0";
			}
			s += newnumber1.getString();
			number1 = new AccurateFloat(s);
			number2 = newnumber2;
		} else if (newnumber2.getPoint() < newnumber1.getPoint()) {
			for (int i = 0; i < (newnumber1.getPoint() - newnumber2.getPoint()); i++) {
				s += "0";
			}
			s += newnumber1.getString();
			number2 = new AccurateFloat(s);
			number1 = newnumber1;
		} else {
			number1 = newnumber1;
			number2 = newnumber2;
		}
				
		//find which array is the longer
		if (number1.getLength() >= number2.getLength()) {
			longest = number1.getLength();	
			shortest = number2.getLength();
			longa = number1;
			
		} else {
			longest = number2.getLength();
			shortest = number1.getLength();
			longa = number2;
		}	
		int[] result = new int[longest];
		
		
		//loop through to add up all corresponding ints (46's are decimal points, and will be ignored)
		for(int i = 0; i < longest; i++) {
					
			if(i<shortest){
				if(number1.getInt(i) != 46 && number2.getInt(i) != 46) {
					
					result[i] = number1.getInt(i) + number2.getInt(i);
				} else {
					result[i] = '.';
					longa.getInt(i);
				}
			} else {
				if (longa.getInt(i) != 46) {
					result[i] = longa.getInt(i);
				} else {
					result[i] = '.';
				}
			}
		}
		
		//loop through from last first, to shift > 10's
		for(int i = longest - 1; i >= 0; i--) {
			if (result[i] >= 10 && result[i] != 46 && i !=0) {
				result[i] -= 10 ;
				if(result[i-1] != 46) {
					result[i-1] += 1;
				} else {
					result[i-2] += 1;
				}
			} 
		}
		
		//loop one more time to reconstruct array as a string
		
		for(int i = 0; i < longest; i++) {
			if (result[i] == (int)'.') {
				output = output + '.';
			} else {
				output = output + result[i];
			}
			
		}
		//return the sum as a string.
		return output;
	}
	
	public static String subtraction(AccurateFloat unarrangedNumber1, AccurateFloat unarrangedNumber2) {
		
	
		//initialise local variables
		int longest, shortest;
		AccurateFloat longa, number1, number2, newnumber1, newnumber2;
		String output = "";
		String s = "";
		boolean firstIsBiggest;
		
		//check if the first arg is larger than the second. if it is, set as newnumber1 and newnumber2. If opposite way round,
		//set the second arg as newnumber1 and the first arg as newnumber2 and flag firstisbiggest as false to negate the final 
		//value.
		if (Float.valueOf(unarrangedNumber1.getString()).compareTo(Float.valueOf(unarrangedNumber2.getString())) >= 0) {
			firstIsBiggest = true;
			newnumber1 = unarrangedNumber1;
			newnumber2 = unarrangedNumber2;
		} else {
			firstIsBiggest = false;
			newnumber2 = unarrangedNumber1;
			newnumber1 = unarrangedNumber2; 
		}
		
		
		//if there aren't the same number of characters left of the decimal point, fill up the shorter one with zero's until the 
		//decimal points line up, output the lined up numbers as AccurateFloat objects number1 and number2
		if (newnumber1.getPoint() < newnumber2.getPoint()) {
			for (int i = 0; i < (newnumber2.getPoint() - newnumber1.getPoint()); i++) {
				s += "0";
			}
			s += newnumber1.getString();
			number1 = new AccurateFloat(s);
			number2 = newnumber2;
		} else if (newnumber2.getPoint() < newnumber1.getPoint()) {
			for (int i = 0; i < (newnumber1.getPoint() - newnumber2.getPoint()); i++) {
				s += "0";
			}
			s += newnumber1.getString();
			number2 = new AccurateFloat(s);
			number1 = newnumber1;
		} else {
			number1 = newnumber1;
			number2 = newnumber2;
		}
				
		//find which array is the longest
		if (number1.getLength() >= number2.getLength()) {
			longest = number1.getLength();	
			shortest = number2.getLength();
			longa = number1;
			
		} else {
			longest = number2.getLength();
			shortest = number1.getLength();
			longa = number2;
		}	
		int[] result = new int[longest];
		
		
		//loop through and subtract all corresponding ints. (46's are decimal points and are consequently ignored)
		for(int i = 0; i < longest; i++) {
					
			if(i<shortest){
				if(number1.getInt(i) != 46 && number2.getInt(i) != 46) {
					
					result[i] = number1.getInt(i) - number2.getInt(i);
				} else {
					result[i] = '.';
				}
			} else {
				if (longa.getInt(i) != 46) {
					if(longest == number1.getLength()) {
						result[i] = longa.getInt(i);
					} else {
						result[i] = 0 - longa.getInt(i);
					}
				} else {
					result[i] = '.';
				}
			}
		}
		
		
		
		//loop through from last first, if negative, add 10 to the value and add 1 to the value one to the left.
		for(int i = longest - 1; i >= 0; i--) {
			if (result[i] < 0 && result[i] != 46 && i !=0) {
				result[i] += 10 ;
				if(result[i-1] != 46) {
					result[i-1] -= 1;
				} else {
					result[i-2] -= 1;
				}
			} 
		}
		//loop one more time to reconstruct the result as a string, removing all leading zeros apart from a singe one if <1
		boolean zeros = true;
		for(int i = 0; i < longest; i++) {
			if ((zeros && result[i] != 0) || !zeros) {
				zeros = false;		
				
				if (result[i] == (int)'.') {
					output = output + '.';
				} else {
					output = output + result[i];
				}
			} else if(result[i+1] == (int)'.' && result[i] == 0 ) {
				output += 0;
			}
		}
		
		//if flagged as the second argument was bigger, add a negative sign.
		if (!firstIsBiggest) {
			output = "-" + output;
		}
		return output;
		}
		
}




```  


and the program that implements it: TestProg.java
```


public class TestProg {

	/**
	 * test program that makes use of the AccurateFloat Class. Only error checking that takes place is for * and /, which
	 * aren't yet supported.
	 * 
	 * input takes three args, number1, operator, number2.
	 */
	public static void main(String[] args) {
		
		AccurateFloat num1 = new AccurateFloat((String)args[0]);
		AccurateFloat num2 = new AccurateFloat((String)args[2]);
		
		if (args[1].equals("+")) {
			System.out.println(AccurateFloat.addition(num1, num2));
		} else if (args[1].equals("-")) {
			System.out.println(AccurateFloat.subtraction(num1, num2));
		} else if (args[1].equals("/") || args[1].equals("*")) {
			System.out.println("Operation Not Supported");
		}
		
	}

}

```


:)

---

### Post by nvteighen on 2008-05-07
Just noticed how much these challenges are helping me to learn C... and programming in general.

Some progress here... but not too much. If I happen to make this work, it will result in a nice shared/static library you can link to.

---

### Post by ibuclaw on 2008-05-07
> **mssever said:**
> Wow. A lot has happened while I've been away from the computer.

That's the general idea, especially if you move everything into functions so that you can simply source the file and do math from wherever.


Thanks, I've just tweaked the code a bit and it's now the building blocks of a library. I've put in everything there (except the sub/mul/div functions).

Once I've finished it should be a nice little integrated tool for any programming language (ie: in C you use the command "**popen()**" or "**system()**" to run it with it's arguments.)

Anyways, Thanks again.
Regards
Iain

---

### Post by tatrefthekiller on 2008-05-08
Here is my program :
```

using System;

namespace AccurateFloats
{
	
	
	public class Fraction
	{
		int num, denom;
		
		public Fraction()
		{
			this.num = 0;
			this.denom = 1;
		}
		
		public Fraction(int num, int denum)
		{
			this.num = num;
			this.denom = denum;
		}
		
		public Fraction(string s)
		{
			int val;
			int puiss;
			
			if(s.Contains("."))
			{
				int virgule = 0;
			
				virgule = s.IndexOf('.');
			
				string nombre = s.Replace(".", "");
			
				val = int.Parse(nombre);
				puiss = virgule - nombre.Length;
				
			}
			else
			{
				val = int.Parse(s);
				puiss = 0;
			}
			
			int pgcd = Fraction.pgcd(val, (int)Fraction.Pow(10, -puiss));
			
			this.num = val / pgcd;
			this.denom = (int)Fraction.Pow(10, -puiss) / pgcd;
		}
		
		public static Fraction operator +(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.denom + b.num * a.denom, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator -(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.denom - b.num * a.denom, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator -(Fraction a)
		{
			return new Fraction(- a.num, a.denom).simplifier();
		}
		
		public static Fraction operator *(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.num, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator *(Fraction a, int b)
		{
			return new Fraction(b * a.num, a.denom).simplifier();
		}
		
		public static Fraction operator /(Fraction a, Fraction b)
		{
			return a * new Fraction(b.denom, b.num).simplifier();
		}
		
		public static Fraction operator /(Fraction a, int b)
		{
			return new Fraction(a.num, a.denom * b).simplifier();
		}
		
		public override string ToString ()
		{
			return ((double)this.num / (double)this.denom) + "";
		}
		
		public void afficher()
		{
			Console.WriteLine(this.num + " / " + this.denom);
		}

		
		public Fraction simplifier()
		{
			int pgcd = Fraction.pgcd(this.num, this.denom);
			return new Fraction(this.num / pgcd, this.denom / pgcd);
		}
		
		private static int Pow(int a, int b)
		{
			if(b == 0)
			{
				return 1;
			}
			
			if(b == 1)
			{
				return a;
			}
			else
			{
				return a * Fraction.Pow(a, b - 1);
			}
		}
		
		private static int pgcd(int a, int b)
		{
			if(b == 0)
			{
				return a;
			}
			else
			{
				return Fraction.pgcd(b, a%b);
			}
			
		}
	}
}

```

Just storing and calculating the numbers as fractions.
Test program :
```
using System;

namespace AccurateFloats
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			Fraction f1 = new Fraction(1, 3);  // 1/3
			Fraction f2 = new Fraction("18");
			
			Console.WriteLine(f1 * f2);  // Displays 6

			f1 = new Fraction("0.2");
			f2 = new Fraction("0.1");

			Console.WriteLine(f1 + f2);  // Displays 0.3
		}
	}
}
```

---

### Post by mssever on 2008-05-09
> **tatrefthekiller said:**
> Here is my program :

What language is this? How do I compile it? It looks vaguely like C++, but: ```
~/programming/snippets/programming challenges/floats/30:$ g++ AccurateFloats.cpp 
AccurateFloats.cpp:1: error: expected nested-name-specifier before ‘System’
AccurateFloats.cpp:1: error: ‘System’ has not been declared
AccurateFloats.cpp:7: error: expected unqualified-id before ‘public’
```

---

### Post by mssever on 2008-05-09
I have to take an unanticipated trip, so I won't be able to choose a winner at the previously scheduled time. I have to shorten this challenge by a day, else this contest would last two weeks. The new deadline is Sunday, 8:00 PM CDT (Monday, 01:00 GMT).

---

### Post by mssever on 2008-05-09
Since we're more than halfway through the contest, I'm going to throw out a few hints.

So far, I've only been able to test tinivole's (post 14) and mcsimon's (post 27) entries. Since there are other entries, the other entrants would be well-advised to make sure I can test their submissions. Instructions are in the first post. Please don't assume that I know your language of choice well enough to write the test stub.

As an additional hint, here are a few additional expressions in my test suite. There's a reason I'm mentioning these specific expressions.
```
321.3   +  6.4
-34.6   +  5.5
  0.7   + -2.8
 -1.259 +  3
```

---

### Post by Verminox on 2008-05-09
Is code optimization a criteria? My solutions seem to waste a bit of memory. Should I go back and try to fix it?

Also, should it handle fixed precision or arbitrary precision?

---

### Post by howlingmadhowie on 2008-05-09
to the best of my knowledge, the standard way of doing this without resorting to bignum libraries or hoping the processor has decimal math capabilities (we're looking at you, ibm power), is to read the number as string, remove the decimal point while remembering where it was and save the number as a long or long long. then you put perform your operation and convert the answer back into a string, being sure to insert the decimal point at the right place.

---

### Post by mssever on 2008-05-09
> **Verminox said:**
> Is code optimization a criteria? My solutions seem to waste a bit of memory. Should I go back and try to fix it?

Also, should it handle fixed precision or arbitrary precision?

Optimization isn't essential. Of course, it can't hurt...

I'm testing with varying precision numbers. However, padding with zeros is acceptable.

---

### Post by tatrefthekiller on 2008-05-09
I made a few changes... I'm programing in C#. You can compile it by typing :
```
gmcs Main.cs Fraction.cs
```
A file "Main.exe" is generated.
Execute it with :
```
./Main.exe 321.3 + 6.4
```

My code :

Main.cs :
```
// Main.cs

using System;

namespace AccurateFloats
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			Fraction f1 = new Fraction(args[0]);
			Fraction f2 = new Fraction(args[2]);
			
			switch(args[1])
			{
			case "+":
				Console.WriteLine(f1 + f2);
				break;
				
			case "-":
				Console.WriteLine(f1 - f2);
				break;
				
			case "*":
				Console.WriteLine(f1 * f2);
				break;
			case "/":
				Console.WriteLine(f1 / f2);
				break;
			}
		}
	}
}

```

Fraction.cs :
```
// Fraction.cs 

using System;

namespace AccurateFloats
{
	
	
	public class Fraction
	{
		int num, denom;
		
		public Fraction()
		{
			this.num = 0;
			this.denom = 1;
		}
		
		public Fraction(int num, int denum)
		{
			this.num = num;
			this.denom = denum;
		}
		
		public Fraction(string s)
		{
			int val;
			int puiss;
			
			if(s.Contains("."))
			{
				int virgule = 0;
			
				virgule = s.IndexOf('.');
			
				string nombre = s.Replace(".", "");
			
				val = int.Parse(nombre);
				puiss = virgule - nombre.Length;
				
			}
			else
			{
				val = int.Parse(s);
				puiss = 0;
			}
			
			int pgcd = Fraction.pgcd(val, (int)Fraction.Pow(10, -puiss));
			
			this.num = val / pgcd;
			this.denom = (int)Fraction.Pow(10, -puiss) / pgcd;
		}
		
		public static Fraction operator +(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.denom + b.num * a.denom, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator -(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.denom - b.num * a.denom, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator -(Fraction a)
		{
			return new Fraction(- a.num, a.denom).simplifier();
		}
		
		public static Fraction operator *(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.num, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator *(Fraction a, int b)
		{
			return new Fraction(b * a.num, a.denom).simplifier();
		}
		
		public static Fraction operator /(Fraction a, Fraction b)
		{
			return a * new Fraction(b.denom, b.num).simplifier();
		}
		
		public static Fraction operator /(Fraction a, int b)
		{
			return new Fraction(a.num, a.denom * b).simplifier();
		}
		
		public override string ToString ()
		{
			return ((double)this.num / (double)this.denom) + "";
		}
		
		public void afficher()
		{
			Console.WriteLine(this.num + " / " + this.denom);
		}

		
		public Fraction simplifier()
		{
			int pgcd = Fraction.pgcd(this.num, this.denom);
			return new Fraction(this.num / pgcd, this.denom / pgcd);
		}
		
		private static int Pow(int a, int b)
		{
			if(b == 0)
			{
				return 1;
			}
			
			if(b == 1)
			{
				return a;
			}
			else
			{
				return a * Fraction.Pow(a, b - 1);
			}
		}
		
		private static int pgcd(int a, int b)
		{
			if(b == 0)
			{
				return a;
			}
			else
			{
				return Fraction.pgcd(b, a%b);
			}
			
		}
	}
}

```

With my program, the precision is 1 / 2147483647 = 1 / int.MaxValue. But I could extend it to 1 / 9223372036854775807 with a long type ;-).

---

### Post by Verminox on 2008-05-09
Ok here is my **Javascript** solution.

Edit: mssever, I've posted a new version in a different post. ([Clicky]("http://ubuntuforums.org/showpost.php?p=4927752&postcount=54")). Use that instead for judging.

Features:
- Stores floats in the form of rational numbers, as integers can be represented accurately
- Only converts to and from decimal during input/output, otherwise it only handles rationals
- Can parse varying inputs (from 1.23 to 00.1 to .750)
- Customizable output precision
- Minimal Error Reporting
- Because of the way it is made, it can be easily modified to serve different bases other than 10


The script: (Rational.js)
```
// First we create a prototype for rational numbers
function Rational(numerator,denominator)
{
	// Data
	this.numerator = (typeof numerator != 'undefined') ? numerator : 0;
	this.denominator = (typeof denominator != 'undefined') ? denominator : 1;
	
	// Reduce a fraction
	this.reduce = function()
	{
		var divisor = gcd(this.numerator,this.denominator);
		this.numerator = this.numerator / divisor;
		this.denominator = this.denominator / divisor;
	}
	
	// Adding two rationals
	this.add = function(q)
	{
		var r = new Rational();
		r.numerator = this.numerator*q.denominator + q.numerator*this.denominator;
		r.denominator = this.denominator * q.denominator;
		r.reduce();
		return r;
	}

	// Subtracting two rationals
	this.subtract = function(q)
	{
		var r = new Rational();
		r.numerator = this.numerator*q.denominator - q.numerator*this.denominator;
		r.denominator = this.denominator * q.denominator;
		r.reduce();
		return r;
	}

	// Multiplying two rationals
	this.multiply = function(q)
	{
		var r = new Rational();
		r.numerator = this.numerator * q.numerator;
		r.denominator = this.denominator * q.denominator;
		r.reduce();
		return r;
	}

	// Dividing two rationals
	this.divide = function(q)
	{
		var r = new Rational();
		if(q.numerator==0)
		{
			throw "Cannot divide by zero";
		}
		r.numerator = this.numerator*q.denominator;
		r.denominator = q.numerator*this.denominator;
		r.reduce();
		return r;
	}
		
}

function gcd(a, b)
{
	if (b == 0)
		return a;
	else 
		return gcd(b, a % b);
}

// Then we extend it to read and write strings of base 10
String.prototype.toRational = function()
{
	var str = this;
	var negative = false;
	if( str.indexOf('-') == 0 )
	{
		negative = true;
	}
	str = this.replace(/^-?|0+|0+$/g,''); // Trim zeros from either side
	var r = new Rational(0,1);
	var point = false; // Whether we have encountered the decimal point yet
	for(var i=0; i<str.length; i++)
	{
		var c = str.charAt(i);
		if( c >= '0' && c <= '9' ) // Digit
		{
			r.numerator = r.numerator * 10 + parseInt(c); // Append to numerator
			if( point ) // Increase denominator
			{
				r.denominator = r.denominator * 10;
			}
		}
		else if ( c == '.' && point == false ) // First time encountering a point
		{
			point = true;
		}
		else
		{
			break;
		}
	}
	if( negative )
	{
		r.numerator = -r.numerator;
	}
	r.reduce(); // Normalize
	return r;
}

Rational.prototype.toString = function(precision)
{
	if( typeof precision == 'undefined' )
		precision = 6; // Default precision
	var str = '';
	var n = this.numerator;
	var d = this.denominator;
	// Sign
	if( ( n < 0 && d >= 0 ) || ( n >= 0 && d < 0 ) )
	{
		str += '-';
		n = -n;
	}
	// Integral part
	str += parseInt( n / d );
	n = n % d;
	// Point
	str += '.';
	// Fractional part
	var p = 1;
	do
	{
		if( p > precision )
			break;
		n = n * 10;
		str += parseInt( n / d );
		n = n % d;
		p++;
	} while(n!=0);	
	return str;
}


// And now we evaluate a set of commands of the syntax <float> <op> <float>
function evaluate(input,precision)
{
	var lines = input.split("\n");
	var output = "";
	for(var i=0; i<lines.length; i++)
	{
		lines[i] = lines[i].replace(/^\s+|\s+$/g,''); // Trim spaces from sides
		lines[i] = lines[i].replace(/\s\s+/g,' '); // Remove multiple spaces
		var tokens = lines[i].split(" ");					
		try
		{
			var r1 = tokens[0].toRational();
			var r2 = tokens[2].toRational();
			var op = tokens[1];
			var r3;
			switch ( op )
			{
				case '+':
					r3 = r1.add(r2);
					break;
				case '-':
					r3 = r1.subtract(r2);
					break;
				case '*':
					r3 = r1.multiply(r2);
					break;
				case '/':
					r3 = r1.divide(r2);
					break;
				default:
					throw "Not Supported";
			}
			output += r3.toString(precision);
		}
		catch (e)
		{
			output += e;
		}
		output += "\n";
	}
	return output;
}
```

The test:
[HTML]<html>
	<head>
		<title>Float10 Test</title>
		<script src="Rational.js" type="text/javascript"></script>
		<script type="text/javascript">
			function $(id)
			{
				return document.getElementById(id);
			}
			function execute()
			{
				$('output').value = evaluate($('input').value,$('precision').value);
			}
		</script>
	</head>
	<body>
	<fieldset>
		<legend>Float10 Test</legend>
		<label for="input">Input:</label><br />
		<textarea id="input" cols="20" rows="6"></textarea><br />
		<label for="percision">Precision: </label>
		<input type="text" id="precision" size="2" value="6" /><br />
		<button onclick="execute();">Execute</button><br />
		<label for="output">Output:</label><br />
		<textarea id="output" cols="20" rows="6"></textarea>
	</fieldset>
	</body>
</html>[/HTML]

---

### Post by tatrefthekiller on 2008-05-09
I think we found the same solution !

---

### Post by achelis on 2008-05-09
[QUOTE=howlingmadhowie]to the best of my knowledge, the standard way of doing this without resorting to bignum libraries or hoping the processor has decimal math capabilities (we're looking at you, ibm power), is to read the number as string, remove the decimal point while remembering where it was and save the number as a long or long long. then you put perform your operation and convert the answer back into a string, being sure to insert the decimal point at the right place.[/QUOTE]
That would be the easiest way to do it. And knowing the range of the test data you wouldn't even have to remember the decimal location - you could have it at a fixed location. But it would be kind of boring to implement :)

I like the fraction solutions.

[QUOTE=tatrefthekiller]With my program, the precision is 1 / 2147483647 [/QUOTE]

Not really - only for numbers < 1. But I do like it.

---

### Post by Bichromat on 2008-05-09
Hi,
I found this challenge interesting, so I subscribed to the forums !

I did it in python. It's the first time I create a class in python, but I found it particularly easy.

module acfl.py :
```
def gcd(a,b):
   """Computes the GCD of two numbers with the Euclidian algorithm"""
   while b:
      a,b=b,a%b
   return a

class frac:
   """
   A fraction class that can do basic arithmetic operations on rationals
   without loss of precision
   """

   def __init__(self,numer=0,denom=1):

      if isinstance(numer,frac):
         assert denom==1
         num=numer.num
         denom=numer.denom
      elif isinstance(numer,int) or isinstance(numer,long):
         assert denom!=0
         num=numer
      elif isinstance(numer,str) or isinstance(numer, float):
         assert denom==1
         strnum=str(numer).strip()

         if strnum[0]=="-":
            sign=-1
            strnum=strnum[1:]
         else:
            sign=1

         dot=strnum.find(".")
         if dot==len(strnum)-1:
            strnum=strnum[:-1]
         elif dot!=-1:
            denom=10**(len(strnum)-dot-1)
            strnum=strnum[:dot]+strnum[dot+1:]
         num=int(strnum)*sign
      else:
         raise TypeError("Cannot convert %s to frac!"%(num))

      pgcd=gcd(num,denom)
      self.num=num/pgcd
      self.denom=denom/pgcd
      if self.denom<0:
         self.num*=-1
         self.denom*=-1


   def __pow__(self,exponent):
      """Integer power of a fraction"""
      assert isinstance(exponent,int)
      return frac(self.num**exponent,self.denom**exponent)
   
   def __mul__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return frac(self.num*other.num,self.denom*other.denom)

   def __rmul__(self,other):
      return self*other

   def __div__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return self*frac(other.denom,other.num)
   
   def __rdiv__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return other/self
   
   def __add__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return frac(self.num*other.denom+other.num*self.denom,self.denom*other.denom)
   
   def __radd__(self,other):
      return self+other
      
   def __neg__(self):
      return frac(-self.num,self.denom)
   
   def __sub__(self,other):
      return self+(-other)
   
   def __rsub__(self,other):
      return other+(-self)

   def __cmp__(self,other):
      if not isinstance(other, frac): other=frac(other)
      num=(self-other).num
      if num>0:   return 1
      elif num<0: return -1
      else:       return 0

   def __str__(self):
         if self.denom==1 : return "%d" % (self.num)
         return "%d/%d" % (self.num,self.denom)

   def __repr__(self):
      return str(self)

   def __float__(self):
      return self.num/float(self.denom)

   def ex(self,decimals=16):
      """Decimal expansion of a fraction"""
      sign="-"*(self.num<0)
      q,r=divmod(abs(self.num),self.denom)
      expansion=sign+str(q)
      if r==0: return expansion
      expansion+="."

      for i in xrange(decimals):
         q,r=divmod(r*10,self.denom)
         expansion+=str(q)
         if r==0 : break

      return expansion

```

Test program test_acfl.py :

```
from acfl import *
import sys

# Read command line parameters :
number1=frac(sys.argv[1])
operator=sys.argv[2]
number2=frac(sys.argv[3])

# Optional 4th argument to specify the number of decimals :
if len(sys.argv)==5: 
   decimals=int(sys.argv[4])
else:
   decimals=16

# Use a nice python builtin :
result=eval("number1"+operator+"number2")

print result.ex(decimals)
```

You can call it this way :
```
python test_acfl.py -12.3456 "*" 567.89
```

you can pass a 4th arg to specify the max number of decimals you want to display (default is 16) :
```
python test_acfl.py -12.3456 "+" 567.89 7
```

As you can see from the code, I had the same idea as tatrefthekiller and Verminox.

Edit : corrected my example following tatrefthekiller's remark about the "*" in the shell,
+ new version of acfl.py

---

### Post by Verminox on 2008-05-10
> **tatrefthekiller said:**
> I think we found the same solution !

You are still dividing two doubles in the toString() method and printing a double, which means you will get double precision, which is standard precision, and not the aim of this challenge.

---

### Post by tatrefthekiller on 2008-05-10
The toString method is only for displaying the value... you can't get an accurate display, it's impossible : try to print 1/3 with infinite accuracy :confused:...
All computation is done accurately with the +, -, * and / operators, because I use fractions. If you doubt, try my program with the test values (or others).

I made a few changes in my code... because of a "bug". To multiply two numbers, you have to use "x", and not "*" because the console interpret this like "all files in the current directory", like in "rm *" delete all files from the current directory.
Now, you can enter numbers in their fraction form : "1/3 x 3".
Main.cs :
```
// Main.cs

using System;

namespace AccurateFloats
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			Fraction f1, f2;
			
			if(args[0].Contains("/"))
			{
				f1 = new Fraction(int.Parse(args[0].Split('/')[0]), int.Parse(args[0].Split('/')[1]));
			}
			else
			{
				f1 = new Fraction(args[0]);
			}
			
			if(args[2].Contains("/"))
			{
				f2 = new Fraction(int.Parse(args[2].Split('/')[0]), int.Parse(args[2].Split('/')[1]));
			}
			else
			{
				f2 = new Fraction(args[2]);
			}
				      
			
			switch(args[1])
			{
			case "+":
				Console.WriteLine(f1 + f2);
				break;
				
			case "-":
				Console.WriteLine(f1 - f2);
				break;
				
			case "x":
				Console.WriteLine(f1 * f2);
				break;
			case "/":
				Console.WriteLine(f1 / f2);
				break;
			}
		}
	}
}
```

Fraction.cs :
```
// Fraction.cs 

using System;

namespace AccurateFloats
{
	
	
	public class Fraction
	{
		int num, denom;
		
		public Fraction()
		{
			this.num = 0;
			this.denom = 1;
		}
		
		public Fraction(int num, int denum)
		{
			this.num = num;
			this.denom = denum;
		}
		
		public Fraction(string s)
		{
			int val;
			int puiss;
			
			if(s.Contains("."))
			{
				int virgule = 0;
			
				virgule = s.IndexOf('.');
			
				string nombre = s.Replace(".", "");
			
				val = int.Parse(nombre);
				puiss = virgule - nombre.Length;
				
			}
			else
			{
				val = int.Parse(s);
				puiss = 0;
			}
			
			int pgcd = Fraction.pgcd(val, (int)Fraction.Pow(10, -puiss));
			
			this.num = val / pgcd;
			this.denom = (int)Fraction.Pow(10, -puiss) / pgcd;
		}
		
		public static Fraction operator +(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.denom + b.num * a.denom, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator -(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.denom - b.num * a.denom, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator -(Fraction a)
		{
			return new Fraction(- a.num, a.denom).simplifier();
		}
		
		public static Fraction operator *(Fraction a, Fraction b)
		{
			return new Fraction(a.num * b.num, a.denom * b.denom).simplifier();
		}
		
		public static Fraction operator *(Fraction a, int b)
		{
			return new Fraction(b * a.num, a.denom).simplifier();
		}
		
		public static Fraction operator /(Fraction a, Fraction b)
		{
			return a * new Fraction(b.denom, b.num).simplifier();
		}
		
		public static Fraction operator /(Fraction a, int b)
		{
			return new Fraction(a.num, a.denom * b).simplifier();
		}
		
		public override string ToString ()
		{
			return ((double)this.num / (double)this.denom) + "";
		}
		
		public void afficher()
		{
			Console.WriteLine(this.num + " / " + this.denom);
		}

		
		public Fraction simplifier()
		{
			int pgcd = Fraction.pgcd(this.num, this.denom);
			return new Fraction(this.num / pgcd, this.denom / pgcd);
		}
		
		private static int Pow(int a, int b)
		{
			if(b == 0)
			{
				return 1;
			}
			
			if(b == 1)
			{
				return a;
			}
			else
			{
				return a * Fraction.Pow(a, b - 1);
			}
		}
		
		private static int pgcd(int a, int b)
		{
			if(b == 0)
			{
				return a;
			}
			else
			{
				return Fraction.pgcd(b, a%b);
			}
			
		}
	}
}

```

---

### Post by RIchard James13 on 2008-05-10
> **howlingmadhowie said:**
> to the best of my knowledge, the standard way of doing this without resorting to bignum libraries or hoping the processor has decimal math capabilities (we're looking at you, ibm power), is to read the number as string, remove the decimal point while remembering where it was and save the number as a long or long long. then you put perform your operation and convert the answer back into a string, being sure to insert the decimal point at the right place.

I'm finding it is more difficult to do it than what you have said. The problem is that in standard FP the decimal point is kept at the same position and the number is moved around it. You can do the string thing and convert to a integer and then place the decimal point back in afterwards. So at least for storing most numbers that method works. 

The problems come when you need to add or subtract numbers that have their decimal point out of alignment. E.g. 0.1 + 100 for that in FP is simple 0.1 e -1 + 0.1 e 2. Which enables you to simply add the numbers together since the exponent tells you where the decimal point should be. 

Now consider the following sum. 0.1001 + 1001.0 in FP that is again 0.1001 e -1 + 0.1001 e 3 but if you try and add them together as two integers you need to shift them both forward by different amounts e.g 10,010,000 + 1,001 when you get the sum which is 10,011,001 you need to shift that back by the size of the larger number to 1001.1001 the possibility that you can overflow with such simple numbers is huge so you need to watch out for that. 

But those numbers are not even using a fraction of the size of a FP number. For instance say you want to add 0.13 e 13 + 0.13 e -13. Then you need to make sure that you don't over shift the numbers.

---

### Post by tatrefthekiller on 2008-05-10
RIchard James13 : you need to remember the position of the point. This position represents the power of 10 by witch you multiply your number :
0.001 = 1 * 10¯³
300 = 3 * 10²
It's a little bit more complicated for handling numbers like :
300.01 = 30001 * 10¯²
You should be able to found the relation between the length of the number, the position of the point, and the power of 10. If you don't, take a look at my code.

---

### Post by Verminox on 2008-05-10
> **tatrefthekiller said:**
> The toString method is only for displaying the value... you can't get an accurate display, it's impossible : try to print 1/3 with infinite accuracy :confused:...

It's not impossible. Take a look at my toString() method. ;)

If your fraction is say, 3/10, the string might just be 0.3000000000001 because the double precision cannot represent 0.3 accurately. Therefore you need to manually do the division using only integers and build up the string.

> **tatrefthekiller said:**
> RIchard James13 : you need to remember the position of the point. This position represents the power of 10 by witch you multiply your number :
0.001 = 1 * 10¯³
300 = 3 * 10²
It's a little bit more complicated for handling numbers like :
300.01 = 30001 * 10¯²
You should be able to found the relation between the length of the number, the position of the point, and the power of 10. If you don't, take a look at my code.

But that doesn't solve the overflow problem. 
Consider a one byte integer representation (biggest possible is 255). 
I can represent 25.5 easily (num=255,dec=1). 
I can represent 255 easily (num=255,dec=0).
I can represent 200 easily (num=200,dec=0).
But I can't represent 200.1 (num=2001 overflow)

---

### Post by WW on 2008-05-10
> **Verminox said:**
> It's not impossible. Take a look at my toString() method. ;)

Verminox, your toString() method can print the number with a given *finite* precision, but 1/3 = 0.33333...  Any printed decimal value will be an approximation.

A nice bonus challenge would be to allow the precision to be "infinite", and have the code either print the full value if the expansion terminates, or figure out the part of the expansion that repeats and indicate it using, say, curly braces.  Then the "infinite" precision output would be something like:

3/320 = 0.009375   (detects terminating expansion automatically)
1/3 = 0.{3}   (finds the repeating part and prints it in braces)
1/7 = 0.{142857}
5/6 = 0.8{3}
etc.

But this is a bit more than what mssever asked for. :)

---

### Post by Lster on 2008-05-10
I have a solution in Python using the decimal class. I think that would make it disallowed, right?

---

### Post by Bichromat on 2008-05-10
> **WW said:**
> 
A nice bonus challenge would be to allow the precision to be "infinite", and have the code either print the full value if the expansion terminates, or figure out the part of the expansion that repeats and indicate it using, say, curly braces.  Then the "infinite" precision output would be something like:

3/320 = 0.009375   (detects terminating expansion automatically)
1/3 = 0.{3}   (finds the repeating part and prints it in braces)
1/7 = 0.{142857}
5/6 = 0.8{3}
etc.

But this is a bit more than what mssever asked for. :)

I thought about finding a repeating pattern too (my code already detects when the expansion terminates before the maximum number of decimals is reached).
It does not seem to require a lot of modifications. I might try it tonight...

---

### Post by nvteighen on 2008-05-10
> **Lster said:**
> I have a solution in Python using the decimal class. I think that would make it disallowed, right?
Probably the same as using the GNU Multi-Precision Library ([GMP]("http://gmplib.org/"))! By the way, it's a great library.

/*My Float library project doesn't even add yet :) It just stores and print data to  a file (or screen, if pointing to stdout)... so currently it is a plain (and useless) I/O library! (But I'll keep working on it, I'm enjoying this!)...
**UPDATE: Now it adds up!!***/

---

### Post by Bichromat on 2008-05-10
I implemented the repeating part detection, and the program also indicates an incomplete expansion with "...".

Examples of output :

1/7 with max 16 decimals :
0.(142857)

1/7 with max 4 decimals :
0.1428...

1/8 with max 16 decimals :
0.125

1/8 with max 2 decimals :
0.12...


code acfl.py :
```
def gcd(a,b):
   """Computes the GCD of two numbers with the Euclidian algorithm"""
   while b:
      a,b=b,a%b
   return a

class frac:
   """
   A fraction class that can do basic arithmetic operations on rationals
   without loss of precision
   """

   def __init__(self,numer=0,denom=1):

      if isinstance(numer,frac):
         assert denom==1
         num=numer.num
         denom=numer.denom
      elif isinstance(numer,int) or isinstance(numer,long):
         assert denom!=0
         num=numer
      elif isinstance(numer,str) or isinstance(numer, float):
         assert denom==1
         strnum=str(numer).strip()

         if strnum[0]=="-":
            sign=-1
            strnum=strnum[1:]
         else:
            sign=1
         
         rec_num=0
         rec_denom=1
         dot=strnum.find(".")
         paren=strnum.find("(")
         if paren!=-1:
            assert strnum[-1]==")"
            recur=strnum[paren+1:-1]
            strnum=strnum[:paren]
            rec_num=int(recur)
            rec_denom=(10**len(recur)-1)*10**(paren-dot-1)
            
         if dot==len(strnum)-1:
            strnum=strnum[:-1]
         elif dot!=-1:
            denom=10**(len(strnum)-dot-1)
            strnum=strnum[:dot]+strnum[dot+1:]

         num=(int("0"+strnum)*rec_denom+rec_num*denom)*sign
         denom*=rec_denom
      else:
         raise TypeError("Cannot convert %s to frac!"%(num))

      pgcd=gcd(num,denom)
      self.num=num/pgcd
      self.denom=denom/pgcd
      self=self

   def __pow__(self,exponent):
      """Integer power of a fraction"""
      assert isinstance(exponent,int)
      return frac(self.num**exponent,self.denom**exponent)
   
   def __mul__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return frac(self.num*other.num,self.denom*other.denom)

   def __rmul__(self,other):
      return self*other

   def __div__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return self*frac(other.denom,other.num)
   
   def __rdiv__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return other/self
   
   def __add__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return frac(self.num*other.denom+other.num*self.denom,self.denom*other.denom)
   
   def __radd__(self,other):
      return self+other
      
   def __neg__(self):
      return frac(-self.num,self.denom)
   
   def __sub__(self,other):
      return self+(-other)
   
   def __rsub__(self,other):
      return other+(-self)

   def __cmp__(self,other):
      if not isinstance(other, frac): other=frac(other)
      num=(self-other).num
      return cmp(num,0)

   def __str__(self):
         if self.denom==1 : return "%d" % (self.num)
         return "%d/%d" % (self.num,self.denom)

   def __repr__(self):
      return str(self)

   def __float__(self):
      return self.num/float(self.denom)

   def ex(self,decimals=16):
      """Decimal expansion of a fraction"""
      sign="-"*(self.num<0)
      q,r=divmod(abs(self.num),self.denom)
      expansion=sign+str(q)
      if r==0: return expansion
      expansion+="."
      remainders={r:len(expansion)}

      for i in xrange(decimals):
         q,r=divmod(r*10,self.denom)
         expansion+=str(q)
         if r==0 : break
         elif r in remainders:
            pos=remainders[r]
            r=0
            expansion=expansion[:pos]+"("+expansion[pos:]+")"
            break
         else: remainders[r]=len(expansion)
      if r!=0: expansion+="..."

      return expansion

```

---

### Post by WW on 2008-05-10
> **Bichromat said:**
> I implemented the repeating part detection, and the program also indicates an incomplete expansion with "...".

Examples of output :

<snip>

Nice!

Since you're having so much fun, how about an option where the code doesn't use a given number of decimals, and it prints the exact value, no matter how many decimals that might require. Maybe this could be indicated with decimals=-1 in the ex function.

EDIT: For example, 355/113 is a pretty good approximation to Pi.  What is the exact decimal expansion?

---

### Post by Bichromat on 2008-05-10
> **WW said:**
> Nice!

Since you're having so much fun, how about an option where the code doesn't use a given number of decimals, and it prints the exact value, no matter how many decimals that might require. Maybe this could be indicated with decimals=-1 in the ex function.

EDIT: For example, 355/113 is a pretty good approximation to Pi.  What is the exact decimal expansion?

I think this is a bit too dangerous. Sometimes a small fraction can yield a large output. For example, 1/607 is :
0.(00164744645799011532125205930807248764415156507
41350906095551894563426688632619439868204283360790
77429983525535420098846787479406919275123558484349
2586490939044481054365733113673805601317957166392092257)...

Imagine with larger fractions ! :o

Anyway, talking about Pi, here is a program I wrote earlier today that computes it up to hundreds of decimals :

```

from acfl import *

# Compute pi using Machin's formula :
# pi/4=4*atan(1/5)-atan(1/239)
#
# with atan(x)=x-x**3/3+x**5/5-x**7/7...
#
# See http://en.wikipedia.org/wiki/Machin-like_formula

max_decimals=100

a5=frac(0.2)
a239=frac(1,239)
atan5=0
atan239=0
for i in xrange(71):
   altern=(-1)**i
   impair=2*i+1

   atan5+=altern*a5**impair/impair
   atan239+=altern*a239**impair/impair
   pi=16*atan5-4*atan239
   print "%03d  pi=%s"%(i,pi.ex(max_decimals))

```

---

### Post by Verminox on 2008-05-10
> **WW said:**
> A nice bonus challenge would be to allow the precision to be "infinite", and have the code either print the full value if the expansion terminates, or figure out the part of the expansion that repeats and indicate it using, say, curly braces.  Then the "infinite" precision output would be something like:

3/320 = 0.009375   (detects terminating expansion automatically)
1/3 = 0.{3}   (finds the repeating part and prints it in braces)
1/7 = 0.{142857}
5/6 = 0.8{3}
etc.

But this is a bit more than what mssever asked for. :)


Done :)

Fixed a couple of minor bugs and added some **more features**:
1. For WW, it now recognizes recurrance of decimals and puts the repeating part in braces {}
2. If the decimals are terminating within precision, thats cool.
3. If the decimals are not recurring, but not terminating either when the max precision is reached, then an ellipses (...) is appended. 

Edit: I can't believe Bichromat did an almost ditto implementation 35 minutes before me :p

You can see what I mean from the examples below.

Test inputs: (Precision = 25)
```
 321.3  +  6.4
 -34.6  +  5.5
   0.7  + -2.8
-1.259  +  3
     5  /  6
    11  *  10
  22.9  /  11.131
    22  /  7
```

Output:
```
327.7
-29.1
-2.1
1.741
0.8{3}
110.0
2.0573174018506872697870811...
3.{142857}
```

Rational.js:
```
// First we create a prototype for rational numbers
function Rational(numerator,denominator)
{
	// Data
	this.numerator = (typeof numerator != 'undefined') ? numerator : 0;
	this.denominator = (typeof denominator != 'undefined') ? denominator : 1;
	
	// Reduce a fraction
	this.reduce = function()
	{
		var divisor = gcd(this.numerator,this.denominator);
		this.numerator = this.numerator / divisor;
		this.denominator = this.denominator / divisor;
	}
	
	// Adding two rationals
	this.add = function(q)
	{
		var r = new Rational();
		r.numerator = this.numerator*q.denominator + q.numerator*this.denominator;
		r.denominator = this.denominator * q.denominator;
		r.reduce();
		return r;
	}

	// Subtracting two rationals
	this.subtract = function(q)
	{
		var r = new Rational();
		r.numerator = this.numerator*q.denominator - q.numerator*this.denominator;
		r.denominator = this.denominator * q.denominator;
		r.reduce();
		return r;
	}

	// Multiplying two rationals
	this.multiply = function(q)
	{
		var r = new Rational();
		r.numerator = this.numerator * q.numerator;
		r.denominator = this.denominator * q.denominator;
		r.reduce();
		return r;
	}

	// Dividing two rationals
	this.divide = function(q)
	{
		var r = new Rational();
		if(q.numerator==0)
		{
			throw "Cannot divide by zero";
		}
		r.numerator = this.numerator*q.denominator;
		r.denominator = q.numerator*this.denominator;
		r.reduce();
		return r;
	}
		
}

function gcd(a, b)
{
	if (b == 0)
		return a;
	else 
		return gcd(b, a % b);
}

// Then we extend it to read and write strings of base 10
String.prototype.toRational = function()
{
	var str = this;
	var negative = false;
	if( this.indexOf('-') == 0 )
	{
		negative = true;
		str = this.substring(1); // all except - sign		
	}
	str = str.replace(/^0+/g,''); // Trim zeros from left side
	var r = new Rational(0,1);
	var point = false; // Whether we have encountered the decimal point yet
	//alert(str);
	for(var i=0; i<str.length; i++)
	{
		var c = str.charAt(i);
		if( c >= '0' && c <= '9' ) // Digit
		{
			r.numerator = r.numerator * 10 + parseInt(c); // Append to numerator
			if( point ) // Increase denominator
			{
				r.denominator = r.denominator * 10;
			}
		}
		else if ( c == '.' && point == false ) // First time encountering a point
		{
			point = true;
			str = str.replace(/0+$/g,''); // Trim zeros from right side
		}
		else
		{
			break;
		}
	}
	if( negative )
	{
		r.numerator = -r.numerator;
	}
	r.reduce(); // Normalize
	return r;
}

Rational.prototype.toString = function(precision)
{
	if( typeof precision == 'undefined' )
		precision = 6; // Default precision
	var str = '';
	var n = this.numerator;
	var d = this.denominator;
	// Sign
	if( ( n < 0 && d >= 0 ) || ( n >= 0 && d < 0 ) )
	{
		str += '-';
		n = -n;
	}
	// Integral part
	str += parseInt( n / d );
	n = n % d;
	// Point
	str += '.';
	var l = str.length;
	// Fractional part
	var p = 1;
	var dividends = new Array();
	do
	{
		if( p > precision )
		{
			str += '...';
			break;
		}
		n = n * 10;
		if( dividends.indexOf( n ) != -1 ) // Dividend is repeated => Recurring part
		{
			var i = l + dividends.indexOf( n ); // index to put a '{'
			str = str.substring(0,i) + '{' + str.substring(i) + '}';
			break;
		}
		dividends.push(n);
		str += parseInt( n / d );
		n = n % d;
		p++;
	} while(n!=0);	
	return str;
}


// And now we evaluate a set of commands of the syntax <float> <op> <float>
function evaluate(input,precision)
{
	var lines = input.split("\n");
	var output = "";
	for(var i=0; i<lines.length; i++)
	{
		lines[i] = lines[i].replace(/^\s+|\s+$/g,''); // Trim spaces from sides
		lines[i] = lines[i].replace(/\s\s+/g,' '); // Remove multiple spaces
		var tokens = lines[i].split(" ");					
		try
		{
			var r1 = tokens[0].toRational();
			var r2 = tokens[2].toRational();
			var op = tokens[1];
			var r3;
			switch ( op )
			{
				case '+':
					r3 = r1.add(r2);
					break;
				case '-':
					r3 = r1.subtract(r2);
					break;
				case '*':
					r3 = r1.multiply(r2);
					break;
				case '/':
					r3 = r1.divide(r2);
					break;
				default:
					throw "Not Supported";
			}
			output += r3.toString(precision);
		}
		catch (e)
		{
			output += e;
		}
		output += "\n";
	}
	return output;
}

```

Test HTML Page
[html]<html>
	<head>
		<title>Float10 Test</title>
		<script src="Rational.js" type="text/javascript"></script>
		<script type="text/javascript">
			function $(id)
			{
				return document.getElementById(id);
			}
			function execute()
			{
				$('output').value = evaluate($('input').value,$('precision').value);
			}
		</script>
	</head>
	<body>
	<fieldset>
		<legend>Float10 Test</legend>
		<label for="input">Input:</label><br />
		<textarea id="input" cols="20" rows="6"></textarea><br />
		<label for="percision">Precision: </label>
		<input type="text" id="precision" size="2" value="6" /><br />
		<button onclick="execute();">Execute</button><br />
		<label for="output">Output:</label><br />
		<textarea id="output" cols="20" rows="6"></textarea>
	</fieldset>
	</body>
</html>[/html]

---

### Post by unutbu on 2008-05-10
AccurateFloats.pm:
```

package AccurateFloats;
use strict;
use warnings;

use vars qw( @EXPORT_OK $accuracy $prettify);

BEGIN {
    require Exporter;
    @EXPORT_OK= qw( $accuracy $prettify);
}

# $AccurateFloats::accuracy equals the number of digits after the decimal which are printed when an AccurateFloat is turned into a string. The user is expected to defined $AccurateFloats::accuracy.

# A trick I learned from Tye McQueen's BigApprox.pm
my $significant_digits= length( 10 / 7 );
my $biggest_int=10**($significant_digits-1)-1;
#    warn "biggest int = $biggest_int\n";

use overload(
    '""' => \&_str,
    '+' =>  \&_add,
    '-' =>  \&_sub,
    '*' =>  \&_mul,
    '/' =>  \&_div,
    'abs' =>  \&_abs,
    fallback => \&not_supported,
);

=head2 PUBLIC methods

=cut

=head1 new

new can be called with one argument or two. 

$num1=new AccurateFloats(3.1) creates an AccurateFloat whose decimal representation equals 3.1.

$num1=new AccurateFloats(31,10) creates an AccurateFloat whose representation as a rational number equals 31/10.

AccurateFloats are represented as rational numbers, with the numerator and denominator both of type int (or whatever the hell perl uses to represent its numbers). Trouble will arise if calculations cause the numerator or denominator to exceed the range of a perl integer.

=cut

sub new {
    my ($invocant)=shift @_;
    my $class=ref $invocant || $invocant;

    my ($numerator,$denominator);
    if ((scalar @_) >= 2) {
	($numerator,$denominator)=(shift @_,shift @_);
    } elsif ((scalar @_) == 1) {
	my $num=shift @_;
	my $numpat=qr/[-]?(?=\d|\.\d)(\d*)(\.(\d*))?/;
	&not_supported unless (defined($num));
	&not_supported unless ($num=~m/$numpat/);
	my $sign=(($num<0) ? -1 : 1);
	my ($int_part,undef,$decimal_part)=($num=~m/$numpat/);
	$int_part=0 unless ($int_part);
	if ($decimal_part) {
	    $denominator=10**(length($decimal_part));
	} else {
	    $denominator=1;
	    $decimal_part=0;
	}
	$denominator=10**(length($decimal_part));
	$numerator=$sign*($int_part*$denominator+$decimal_part);
    } else {
	&not_supported;
    }
    my $self=[$numerator,$denominator];
    bless $self,$class;
    $self->reduce;
#    warn "Creating accurate float: ($self->[0]/$self->[1])";
    return $self;
}

sub not_supported {
    print STDOUT "Not supported";
    exit;
}

=head1 frac

frac returns a string representation of the AccurateFloat as a rational number.

=cut


sub frac {
    my $self=shift;
    return "$self->[0]/$self->[1]";
}

=head1 report

report prints the AccurateFloat as a rational number.

=cut

sub report {
    my $self=shift;
    print "$self->[0]/$self->[1]\n";
}


=head2 PRIVATE methods and procedures

=cut

=head1 reduce

reduce reduces the rational number representation of AccurateFloat to a proper fraction.

=cut

sub reduce {
    my $self=shift;
    if ((abs($self->[0])>$biggest_int)||(abs($self->[1])>$biggest_int)) {
	warn "My representation of rationals is smacking against the biggest int limitation.";
	warn "problem number: $self->[0]/$self->[1]";
	exit;
    }
    my $divisor=$self->gcd;
    $self->[0]/=$divisor;
    $self->[1]/=$divisor;

    return $self;
}

=head1 gcd

gcd finds the greatest common divisor of an AccurateFloat's rational representation.

=cut

sub gcd {
    my $self=shift;
    my ($a,$b)=($self->[0],$self->[1]);
    while ($b) {
	($a,$b)=($b,$a % $b);
    }
    return $a;
}

=head1 _add,_sub,_mul,_div,_abs

Don't call _add,_sub,_mul,_div,_abs. If things are working correctly, '+','-','*','/','abs' will call them for you.

=cut


sub _add {
    my ($x,$y)=@_;
    $y= $x->new($y) unless (ref $y);
    my ($numerator,$denominator)=((($x->[0]*$y->[1])+($y->[0]*$x->[1])),$x->[1]*$y->[1]);
    my $result=new AccurateFloats($numerator,$denominator);
    $result->reduce;
    return $result;
}

sub _sub {
    my ($x,$y)=@_;
    $y= $x->new($y) unless (ref $y);
    my ($numerator,$denominator)=((($x->[0]*$y->[1])-($y->[0]*$x->[1])),$x->[1]*$y->[1]);
    my $result=new AccurateFloats($numerator,$denominator);
    $result->reduce;
    return $result;
}

sub _mul {
    my ($x,$y)=@_;
    $y= $x->new($y) unless (ref $y);
    my ($numerator,$denominator)=($x->[0]*$y->[0],$x->[1]*$y->[1]);
    my $result=new AccurateFloats($numerator,$denominator);
    $result->reduce;
    return $result
}

sub _div {
    my ($x,$y)=@_;
    $y=$x->new($y) unless (ref $y);
    if (!$y->[0]) {
	warn "division by zero, doofus.";
	$y->not_supported;
    }
    my ($numerator,$denominator)=($x->[0]*$y->[1],$x->[1]*$y->[0]);
    my $result=new AccurateFloats($numerator,$denominator);
    $result->reduce;
    return $result;
}


sub _abs {
    my ($x)=@_;
    $x->[0]=abs($x->[0]);
    $x->[1]=abs($x->[1]);
    return $x;
}


=head1 _str

The _str method returns a string which contains the decimal representation of the AccurateFloat. Repeated decimals are represented with braces surrounding the repeating part. So 1/3 = 0.{3}. At most $accuracy number of decimal digits are printed. If the string is terminated before the decimal representation is fully presented, '...' is added to the end fo the string.

=cut

sub _str {
    my $self=shift;
    my ($numerator,$denominator)=($self->[0],$self->[1]);
    my ($int_part);
    my $str;
    $str.="-" if ($numerator<0);
    $numerator=abs($numerator);
    $int_part=int($numerator/$denominator);
    $str.=$int_part;
    my $remainder=$numerator % $denominator;
    if ($remainder) {
	my %remainder_idx;
	$str.='.';
	$remainder_idx{$remainder}=length($str);

	for (1..$accuracy) {
	    $int_part=int($remainder*10/$denominator);
	    $remainder=($remainder*10) % $denominator;
	    $str.=$int_part;

	    last if ($remainder==0);
	    if (($prettify) && (exists($remainder_idx{$remainder}))) {
		my $pos=$remainder_idx{$remainder};
		$str=substr($str,0,$pos) . '{' . substr($str,$pos) . '}';
		return "$str";
	    } else {
		$remainder_idx{$remainder}=length($str);
	    }
	}
	$str.='...' if (($remainder!=0)&&($prettify));
    }
    return "$str";    
}

1;

```
test-AccurateFloats.pl:
```

#!/usr/bin/perl

=head
Usage:

% test-AccurateFloats.pl "0.1" "+" "0.2"
0.3

% test-AccurateFloats.pl "0.1" "/" "0.0"
division by zero, doofus. at AccurateFloats.pm line 184.
Not supported
% test-AccurateFloats.pl "0.1" "/" "0.0" 2>/dev/null
Not supported
% test-AccurateFloats.pl "0.1" "/" "0.1"
1

% test-AccurateFloats.pl "0.1" "*" "0.2"
0.02

% test-AccurateFloats.pl "24426.24" "-" "24356.25"
69.99

% VERBOSE=1 test-AccurateFloats.pl "24426.24 - 24356.25"
69.9900000000016 (Perl's default math)
69.99

% test-AccurateFloats.pl "24426.24" "-" "-24356.25"
48782.49

% test-AccurateFloats.pl "24426.24 --24356.25"
48782.49

% test-AccurateFloats.pl "0.1" "/" "7"
0.0142857142857142857142857142857142857142

% test-AccurateFloats.pl "0.1" "*-.2"
-0.02

% test-AccurateFloats.pl "1+2/7"
1.2857142857142857142857142857142857142857

% test-AccurateFloats.pl "(1+2)/7"
0.4285714285714285714285714285714285714285

% test-AccurateFloats.pl "1+blah"
Not supported
% test-AccurateFloats.pl "1 blah 2" 2>/dev/null
Not supported
% test-AccurateFloats.pl "1 exp 2"
Not supported
% test-AccurateFloats.pl "1 abs 2"
Not supported
% test-AccurateFloats.pl "abs(-2/3) + 1/7"
0.8095238095238095238095238095238095238095

% test-AccurateFloats.pl "abs(-2/3)"
0.6666666666666666666666666666666666666666

% test-AccurateFloats.pl  "355/113"
3.1415929203539823008849557522123893805309

% ACCURACY=20 test-AccurateFloats.pl  "355/113"
3.14159292035398230088

% ACCURACY=200 PRETTIFY=1 test-AccurateFloats.pl  "355/113"
3.{1415929203539823008849557522123893805309734513274336283185840707964601769911504424778761061946902654867256637168}

% ACCURACY=20 PRETTIFY=1 test-AccurateFloats.pl  "355/113"
3.14159292035398230088...

% ACCURACY=20 VERBOSE=1 test-AccurateFloats.pl "355/113"
3.14159292035398 (Perl's default math)
3.14159292035398230088


=cut

use strict;
use warnings;
use AccurateFloats;


$AccurateFloats::accuracy=$ENV{ACCURACY} || 40;
$AccurateFloats::prettify=$ENV{PRETTIFY} || 0;

my $str=join(' ',@ARGV);

#warn "str=$str";

if ($ENV{VERBOSE}) {
    my $inaccurate_val=eval($str);
    print "$inaccurate_val (Perl's default math)\n";
}

my $numpat=qr/[-]?(?=\d|\.\d)(\d*)(\.(\d*))?/;

my @af;
my $idx=0;
while ($str=~m/$numpat/) {
#    warn "str=$str\n";
    my ($a)=($str=~m/($numpat)/);
#    warn "a=$a";
    $af[$idx]=new AccurateFloats($a);
    $str=~s/$a/\$af[*]/;
    $idx++
}
$idx=0;
while ($str=~m/\[\*\]/) {
#    warn "str=$str\n";
    $str=~s/\$af\[\*\]/\$af[$idx]/;
    $idx++;
}

#warn "str=$str\n";
my $result;
my $cmd='$result = ' . $str;
eval($cmd);
if ($@) {
    print STDOUT "Not supported";
} else {
    print "$result\n";    
}

```

---

### Post by mssever on 2008-05-11
> **tatrefthekiller said:**
> I made a few changes in my code... because of a "bug". To multiply two numbers, you have to use "x", and not "*" because the console interpret this like "all files in the current directory", like in "rm *" delete all files from the current directory.
Um, the spec says to use *, not x, because my first round of testing involves running a test script on each program to see if it passes. My script uses * for multiplication, not x, so if you're using x, your program will fail the test. It's trivial to make * work properly.

---

### Post by Bichromat on 2008-05-11
I modified my last acfl.py code so that :
- it does not print "..." when the expansion is recurring
- it can read a recurring expansion and convert it :
```

$ python test_acfl.py "0.125" "*" "0.(142857)"
0.017(857142)

```

---

### Post by Verminox on 2008-05-11
> **Bichromat said:**
> I modified my last acfl.py code so that :
- it does not print "..." when the expansion is recurring
- it can read a recurring expansion and convert it :

Can you try the following input in your program and tell me the output (I don't have a python interpreter around currently)

```
1.0606 / 3
```

---

### Post by Bichromat on 2008-05-11
> **Verminox said:**
> Can you try the following input in your program and tell me the output (I don't have a python interpreter around currently)

```
1.0606 / 3
```

[-X Always have your towel with you ! :lol:

the output is 0.3535(3)

---

### Post by tatrefthekiller on 2008-05-11
@ mssever :
This is not due to my program, but to the bash... if I make a test program that prints arguments, and I run it with the command "./Main.exe 1 * 4", here is the output :
```
1
Fraction.cs
Main.cs
Main.exe
4
```

EDIT : I didn't see that your running your scripts using :./Main.exe "1" "*" "4"

---

### Post by Bichromat on 2008-05-11
You have to put quotes around the operator (look at the first post) ;-)
Edit: too late !

---

### Post by Verminox on 2008-05-11
> **Bichromat said:**
> [-X Always have your towel with you ! :lol:

the output is 0.3535(3)

Ahhh. When I read your code I thought that it had a slight bug in it that might give the output as 0.{35}. But I am mistaken, it's fine. Cheers ;)

---

### Post by WW on 2008-05-11
Bichromat, Verminox, unutbu: Very cool!

But be careful that the notation that you use for a repeating decimal doesn't cause your program to fail mssever's test.  Perhaps it should only use the repeating decimal notation when explicitly told to do so; the default behavior should be to just print some finite number of digits.

---

### Post by Verminox on 2008-05-11
> **WW said:**
> Bichromat, Verminox, unutbu: Very cool!

But be careful that the notation that you use for a repeating decimal doesn't cause your program to fail mssever's test.  Perhaps it should only use the repeating decimal notation when explicitly told to do so; the default behavior should be to just print some finite number of digits.

Good point.

**mssever**: Would you prefer us to take away the functionality of grouping recurring digits and the trailing elipses (...) for unfinished decimals? Let us know so we can edit our posts.

---

### Post by Bichromat on 2008-05-11
I added an option to do pretty print or not. The default behavior of the test program now corresponds to what is asked in the first post :

acfl.py:
```

def gcd(a,b):
   """Computes the GCD of two numbers with the Euclidian algorithm"""
   while b:
      a,b=b,a%b
   return a

class frac:
   """
   A fraction class that can do basic arithmetic operations on rationals
   without loss of precision
   """

   def __init__(self,numer=0,denom=1):

      if isinstance(numer,frac):
         assert denom==1
         num=numer.num
         denom=numer.denom
      elif isinstance(numer,int) or isinstance(numer,long):
         assert denom!=0
         num=numer
      elif isinstance(numer,str) or isinstance(numer, float):
         assert denom==1
         strnum=str(numer).strip()

         if strnum[0]=="-":
            sign=-1
            strnum=strnum[1:]
         else:
            sign=1
         
         rec_num=0
         rec_denom=1
         dot=strnum.find(".")
         paren=strnum.find("(")
         if paren!=-1:
            assert strnum[-1]==")"
            recur=strnum[paren+1:-1]
            strnum=strnum[:paren]
            rec_num=int(recur)
            rec_denom=(10**len(recur)-1)*10**(paren-dot-1)
            
         if dot==len(strnum)-1:
            strnum=strnum[:-1]
         elif dot!=-1:
            denom=10**(len(strnum)-dot-1)
            strnum=strnum[:dot]+strnum[dot+1:]

         num=(int("0"+strnum)*rec_denom+rec_num*denom)*sign
         denom*=rec_denom
      else:
         raise TypeError("Cannot convert %s to frac!"%(num))

      pgcd=gcd(num,denom)
      self.num=num/pgcd
      self.denom=denom/pgcd
      self=self

   def __pow__(self,exponent):
      """Integer power of a fraction"""
      assert isinstance(exponent,int)
      return frac(self.num**exponent,self.denom**exponent)
   
   def __mul__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return frac(self.num*other.num,self.denom*other.denom)

   def __rmul__(self,other):
      return self*other

   def __div__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return self*frac(other.denom,other.num)
   
   def __rdiv__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return other/self
   
   def __add__(self,other):
      if not isinstance(other,frac): other=frac(other)
      return frac(self.num*other.denom+other.num*self.denom,self.denom*other.denom)
   
   def __radd__(self,other):
      return self+other
      
   def __neg__(self):
      return frac(-self.num,self.denom)
   
   def __sub__(self,other):
      return self+(-other)
   
   def __rsub__(self,other):
      return other+(-self)

   def __cmp__(self,other):
      if not isinstance(other, frac): other=frac(other)
      num=(self-other).num
      return cmp(num,0)

   def __str__(self):
         if self.denom==1 : return "%d" % (self.num)
         return "%d/%d" % (self.num,self.denom)

   def __repr__(self):
      return str(self)

   def __float__(self):
      return self.num/float(self.denom)

   def ex(self,decimals=16,pretty=True):
      """Decimal expansion of a fraction"""
      sign="-"*(self.num<0)
      q,r=divmod(abs(self.num),self.denom)
      expansion=sign+str(q)
      if r==0: return expansion
      expansion+="."
      remainders={r:len(expansion)}

      for i in xrange(decimals):
         q,r=divmod(r*10,self.denom)
         expansion+=str(q)
         if r==0 : break
         
         if pretty:
            if r in remainders:
               pos=remainders[r]
               r=0
               expansion=expansion[:pos]+"("+expansion[pos:]+")"
               break
            else: remainders[r]=len(expansion)
            
      if r!=0 and pretty: expansion+="..."

      return expansion

```

test_acfl.py :
```

from acfl import *
import sys

decimals=16
pretty=False

# Read command line parameters:
number1=frac(sys.argv[1])
operator=sys.argv[2]
number2=frac(sys.argv[3])

# Optional arguments:
if "-n" in sys.argv : decimals=int(sys.argv[sys.argv.index("-n")+1])
pretty=("-p" in sys.argv)

# Use a nice python builtin:
result=eval("number1"+operator+"number2")

print result.ex(decimals,pretty)

```

The program takes optional arguments at the end of the command line :
```

$ python test_acfl.py "-1.0606" "/" "3"
-0.3535333333333333
$ python test_acfl.py "-1.0606" "/" "3" -p
-0.3535(3)
$ python test_acfl.py "-1.0606" "/" "3" -n 6
-0.353533

```

---

### Post by mssever on 2008-05-11
> **Verminox said:**
> **mssever**: Would you prefer us to take away the functionality of grouping recurring digits and the trailing elipses (...) for unfinished decimals? Let us know so we can edit our posts.
As long as it doesn't use special notation for non-terminating decimals (such as 0.3), there shouldn't be any trouble. My tests don't use any repeating or non-terminating decimals; I left that area undefined.

---

### Post by mssever on 2008-05-12
[edit]The entry numbers below refer to the post number where they were submitted[/edit]

Thanks to everyone who participated in this challenge. In all, there were 12 entries to this contest. Five were disqualified because they failed my test script (14, but was documented; 27, but was fixed and no longer disqualified), were untestable (14, 23, 30), or didn't meet the basic purpose of this challenge (37 used built-in floating-point division to convert from a fraction to a decimal, but the challenge was to represent floats accurately without using built-in language features).

In the end, it came down to post 51 by Bichromat (I actually chose this post over Bichromat's later post) and post 54 by Verminox. Both approaches were very similar. They represented floats as rational numbers, and they added a way to represent repeating and irrational numbers (which is a really nice extra).

Bichromat's code handled type conversion for math operations automatically, whereas Verminox's code assumed the proper type. In addition, Bichromat implemented a larger set of mathematical operations. However, all this is really a rehash of [Programming Challenge 2]("http://ubuntuforums.org/showthread.php?t=709218"). The biggest deficiency of Bichromat's code is that __float__() uses Python's floating-point division, which has been demonstrated to be inaccurate. The ex() method saved this code from automatic disqualification, but it should have been worked into __float__() since the challenge was to accurately represent floats. Also, I had to slightly modify Bichromat's test file before I could run it with my test script since it was missing the shebang line.

Verminox's code was written in a more readable style, including spaces between operators and other goodies. Plus, it was commented better. Verminox's code had nice type casts between strings and rational numbers. Another small advantage is that Verminox used {} for repeating digits instead of (); the advantage here is that curly braces have fewer other uses.

In the end, **Verminox is the winner of Programming Challenge 10**. Congratulations, Verminox! It's now your turn to pose the next challenge.

PS: For the record, here's my test script and input:
floats_test:[php]#!/usr/bin/env ruby

# Command line argument: the name of the program to test
$program = ARGV[0]

which_operation = if $program == '--list'
                    :print_expressions
                  elsif $program == '--list-answers'
                    :print_answers
                  else
                    :test
                  end
$pass = true
expressions = nil
File.open('expressions.txt') { |f| expressions = f.read }
expressions = expressions.chomp.split("\n")
expressions.collect! { |i| i.strip }
expressions.delete_if { |i| i =~ /[a-zA-Z]/ }

def test(first, op, second, answer)
  result = `./#{$program} '#{first}' '#{op}' '#{second}'`.chomp.gsub(/[0]+$/,'')
  unless result == answer || result =~ /not supported/i
    $stderr.puts "%s %s %s = %s (correct answer: %s)" % [
      first,
      op,
      second,
      result,
      answer,
    ]
    $pass = false
  end
end

def print_expressions(first, op, second, answer)
  puts "#{first} #{op} #{second}"
end

def print_answers(first, op, second, answer)
  puts answer
end

expressions.each do |exp|
  first, second, sum, difference, product, quotient = exp.split(/[\s]+/) # regexp should read backslash s, but the forum software doesn't display it properly
  send which_operation, first, "+", second, sum
  send which_operation, first, "-", second, difference
  send which_operation, first, "*", second, product
  send which_operation, first, "/", second, quotient unless quotient =~ /~/
end

unless $pass
  exit(1)
end[/php]expressions.txt:
```
Accurate floats test file
Any line containing letters is a comment. Blank lines are forbidden.
The ~ before a number marks it as approximate
Format: First number, second number, sum, difference, product, quotient
                                                                        z
  num1     num2     +        -           *        /
  1.1      1.2      2.3      -0.1        1.32     ~0.91666667
  2        4.2      6.2      -2.2        8.4      ~0.47619048
  3.432   -2.0      1.432     5.432     -6.864    -1.716
 -1.259    3        1.741    -4.259     -3.777   ~-0.41966667
  0.32     0.1      0.42      0.22       0.032     3.2
321.3      6.4    327.7     314.9     2056.32     50.203125
-34.6      5.5    -29.1     -40.1     -190.3     ~-6.2909091
  0.7     -2.8     -2.1       3.5       -1.96     -0.25
  9.9      2.0     11.9       7.9       19.8       4.95
```

---

### Post by Bichromat on 2008-05-12
Congratulations Verminox ! I'm looking forward to your challenge :)

But, being a sore loser ( :lolflag: ), I'd like to comment your comments, mssever :
> **mssever said:**
> 
The biggest deficiency of Bichromat's code is that __float__() uses Python's floating-point division, which has been demonstrated to be inaccurate. The ex() method saved this code from automatic disqualification, but it should have been worked into __float__() since the challenge was to accurately represent floats.

I wanted the method to return a <type 'float'> because it is what it's supposed to do. Perhaps I should have had __repr__ and __str__ return the expansion instead.

> **mssever said:**
> 
Verminox's code had nice type casts between strings and rational numbers.
? My code converts strings too. And floats : frac("1.2") and frac(1.2) both yield 6/5 (beware : the second expression casts the float to a string and therefore has limited precision). 

> **mssever said:**
> Another small advantage is that Verminox used {} for repeating digits instead of (); the advantage here is that curly braces have fewer other uses.
I used () because it is a standard used in mathematics to represent repeating digits.

But I have to agree, my code is quite dirty. Verminox's entry is much cleaner.

---

### Post by Verminox on 2008-05-12
mssever: Thank you very much ;)

Bichromat: I liked your code a lot too. Here's some :popcorn: for you.

This is my [second victory at a programming challenge]("http://ubuntuforums.org/showthread.php?t=323609") :D

I will post the next challenge shortly (already have an idea).

---

### Post by mssever on 2008-05-12
In reality, Bichromat, the decision between your code and Verminox's was very difficult. Your entries were so similar that I felt like I had to resort to nitpicking in order to choose a winner. Perhaps I even had to be a little arbitrary... :)

---

