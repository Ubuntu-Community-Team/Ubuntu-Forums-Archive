---
title: "c++ Fastest way to convert int to string of char?"
date: 2011-04-13
forum: Programming Talk
---

### Post by akvino on 2011-04-13
I know there are functions that do it such as itoa, sprintf, etc...

What would be the fastest way to convert int to char string?
int a = 12345; into char b[6] = "12345";

Any intelligent ways to do this faster than sprintf or itoa?

---

### Post by PaulM1985 on 2011-04-13
Have a look at ostringstream.

```

#include <iostream>
#include <sstream>
#include <string>
using namespace std;

int main () {

  ostringstream oss;
  string mystr;

  oss << 12345;
  mystr=oss.str();

  cout << mystr;

  return 0;
}

```

Note: This is untested but I think it works. If you really need chars, I think there is a method on "string" which will allow this.

Paul

---

### Post by akvino on 2011-04-13
> **PaulM1985 said:**
> Have a look at ostringstream.

```

#include <iostream>
#include <sstream>
#include <string>
using namespace std;

int main () {

  ostringstream oss;
  string mystr;

  oss << 12345;
  mystr=oss.str();

  cout << mystr;

  return 0;
}

```

Note: This is untested but I think it works. If you really need chars, I think there is a method on "string" which will allow this.

Paul


Thanks Paul, but I am trying to really stick to c string/ array type of solution. I did some benchmarks and in every way std::string was at least 10 times slower than regular c type operations on array or a c string.

---

### Post by Npl on 2011-04-13
use itoa or write your own version thereof

---

### Post by Simian Man on 2011-04-13
Here's what I cam up with, but I very much doubt it's more efficient than sprintf.  Just because you write a function yourself doesn't make it magiacally faster than something from a library (usually the opposite).

```
void myitoa(int x, char* dest) {
  int i = (int) log10((double) x);
  while(x > 0) {
    dest[i] = (x % 10) + '0';
    x = x / 10;
    i = i - 1;
  }
  dest[i] = '\0';
}

```

[quote=akvino]
Thanks Paul, but I am trying to really stick to c string/ array type of solution. I did some benchmarks and in every way std::string was at least 10 times slower than regular c type operations on array or a c string.[/quote]
**10 times** slower??  I'm sorry, but I have to call BS on that one unless you post your tests.  std::string is implemented very efficiently.  There may be some drop off, but there is no way in hell it's even a 2X dropoff.  Also keep in mind that some operations (such as std::string::length vs. strlen) are *asymptotically* faster with the C++ std::string class.

---

### Post by BkkBonanza on 2011-04-13
You may find this interesting. It compares various method speeds. 
On VC++ streams are way slower but on g++ they not too bad.
Spirit.Karma wins here, about 2x faster.

[http://tinodidriksen.com/2010/02/07/cpp-convert-int-to-string-speed/](http://tinodidriksen.com/2010/02/07/cpp-convert-int-to-string-speed/)

(This result set makes VC++ look ridiculous but in either case it's the overhead of new string that seems to be heavy)

Also found this related to Boost Spirit.Karma tests,

[http://www.boost.org/doc/libs/1_46_1/libs/spirit/doc/html/spirit/karma/performance_measurements/numeric_performance/int_performance.html](http://www.boost.org/doc/libs/1_46_1/libs/spirit/doc/html/spirit/karma/performance_measurements/numeric_performance/int_performance.html)

-----
This google code module has a function that seems fast too though I still would have thought there was some trick possible that could make a faster method. It really is much the same as the "naive" function above.

[http://code.google.com/p/stringencoders/wiki/NumToA](http://code.google.com/p/stringencoders/wiki/NumToA)

---

### Post by PaulM1985 on 2011-04-13
Out of interest, why is this conversion needed to be so quick?  Are there other areas of your program which you could refine?  Why do the numbers need to be converted to strings?

---

### Post by Arndt on 2011-04-13
> **Simian Man said:**
> 
Also keep in mind that some operations (such as std::string::length vs. strlen) are *asymptotically* faster with the C++ std::string class.

What does that mean? That it's faster for 1000 character strings, but may be slower for six character ones?

---

### Post by Arndt on 2011-04-13
> **Simian Man said:**
> Here's what I cam up with, but I very much doubt it's more efficient than sprintf.  Just because you write a function yourself doesn't make it magiacally faster than something from a library (usually the opposite).

```
void myitoa(int x, char* dest) {
  int i = (int) log10((double) x);
  while(x > 0) {
    dest[i] = (x % 10) + '0';
    x = x / 10;
    i = i - 1;
  }
  dest[i] = '\0';
}

```




FPU's are fast too, but I'd guess that the log10 there would dominate the time taken for this algorithm.

I could be wrong.

---

### Post by BkkBonanza on 2011-04-13
> **Arndt said:**
> FPU's are fast too, but I'd guess that the log10 there would dominate the time taken for this algorithm.

I could be wrong.

Ya, the question is whether it's faster to reverse the string after or use the log function. My guess would be reverse the string, but I just don't know on these newer CPUs if the log is actually really fast. 

I'm pretty curious too about how that Intel compiler generated code that was almost twice as fast as the gcc one. According to the Intel site users who write non-commercial code can download the Linux compiler for free. The commercial version is $599.

---

### Post by akvino on 2011-04-13
> **Simian Man said:**
> Here's what I cam up with, but I very much doubt it's more efficient than sprintf.  Just because you write a function yourself doesn't make it magiacally faster than something from a library (usually the opposite).

```
void myitoa(int x, char* dest) {
  int i = (int) log10((double) x);
  while(x > 0) {
    dest[i] = (x % 10) + '0';
    x = x / 10;
    i = i - 1;
  }
  dest[i] = '\0';
}

```


**10 times** slower??  I'm sorry, but I have to call BS on that one unless you post your tests.  std::string is implemented very efficiently.  There may be some drop off, but there is no way in hell it's even a 2X dropoff.  Also keep in mind that some operations (such as std::string::length vs. strlen) are *asymptotically* faster with the C++ std::string class.

My operation requires int to char conversion, insertion, and then clearing or zeroing operatoion on the string. 
I ran std::string solution through 'for' loop 9000 000 000 times. Operation inserted the value, and then removed it, on a string that used std::string::reserve function for memory efficiency. I tried std::string::erase, std::string::replace, and some other functions with time benchmark close to 58 seconds.
I did the same with strncpy and memset(where memset was the slowest perfroming part and can be beat by inserting '/0' at the desired place in the string), and it did it in 5.9 seconds. Test was very simple, but very valuble. 

I am writing a normalization tool that has some pretty crazy requriements regarding speed. We mesure performance on fast protocols in nanoseconds, and this one being ASCII will probably run in microseconds. Thus far I used 'sprintf' since it returns number of characters converted and does it preaty fast, but if you have custom requriement and known set of inputs, I find custom inlined code to be faster then standard library code, even if it is inlined. Now this is not always the case, but every once in a while, you come accross condition that can beat the performance of well known functions.

Regarding your code sample - yes I have something similar to that as well.

---

### Post by akvino on 2011-04-13
> **BkkBonanza said:**
> You may find this interesting. It compares various method speeds. 
On VC++ streams are way slower but on g++ they not too bad.
Spirit.Karma wins here, about 2x faster.

[http://tinodidriksen.com/2010/02/07/cpp-convert-int-to-string-speed/](http://tinodidriksen.com/2010/02/07/cpp-convert-int-to-string-speed/)

(This result set makes VC++ look ridiculous but in either case it's the overhead of new string that seems to be heavy)

Also found this related to Boost Spirit.Karma tests,

[http://www.boost.org/doc/libs/1_46_1/libs/spirit/doc/html/spirit/karma/performance_measurements/numeric_performance/int_performance.html](http://www.boost.org/doc/libs/1_46_1/libs/spirit/doc/html/spirit/karma/performance_measurements/numeric_performance/int_performance.html)


-----
This google code module has a function that seems fast too though I still would have thought there was some trick possible that could make a faster method. It really is much the same as the "naive" function above.

[http://code.google.com/p/stringencoders/wiki/NumToA](http://code.google.com/p/stringencoders/wiki/NumToA)


Thanks for those links. :popcorn:

---

### Post by akvino on 2011-04-13
> **PaulM1985 said:**
> Out of interest, why is this conversion needed to be so quick?  Are there other areas of your program which you could refine?  Why do the numbers need to be converted to strings?

Everything in the program has to be quick. Yes I try to optimize everything where performance counts. If I need to preload data sets or read file, I can do it with the easiest tool for the job, but once I start real time processing - it needs to be as fast as possible.

That is why I LOVE c++ ):P

---

### Post by stchman on 2011-04-13
If only everything was as beautiful as Java where pretty much every Class has a toString method.

[php]
public class ConvertIntToString {
    public static void main( String[] args ) {
        int number = 12345;
        
        // convert an int to a String
        String text = Integer.toString( number );
        
        System.out.println( text );
    }
}

[/php]

---

### Post by Some Penguin on 2011-04-13
*shrug*

You could always do something like the following.

1.  Precompute the following array.  Use a script to write the initializers.

    char *hundredThousandStrings[] = { "0" ... "99999" };

Tradeoff one:   memory vs speed
Tradeoff two:   more arrays => more comparisons


2.  Function looks something like following

```

   if negative,
       append - and recurse with abs value

   int rest = value / 100000;
   if (rest == 0) {   
      then simply copy the whole string; 
   } else {
      copy the string minus the \0, and recurse on rest
   }

```

This might be slightly faster because it does significantly fewer divisions if most of your numbers are not small, and divisions by non-power-of-two tends to be expensive.

For more fun, write a script that writes horrible C code of the type

```


switch(part % 100000) {
case 0:  
   write '0\n' to string
   break;
...
case '99999':
   write '99999' into string
   break;
}

if larger than 10000
   recurse
else 
   append '\0';

```

This may conceivably be faster because every string write uses a constant string, making it possible for the script that writes the code to also specify precisely how long each string is and how far to advance the destination char*.  This means that you don't need to perform the 'is this the zero byte?' check.

---

### Post by Npl on 2011-04-13
Well, good compilers should be able to optimize the division by small constant values away (just checked and atleast MSVC does this). For this reason a itoa with a fixed base should be faster.

Heres my take, should handily beat most library code. You can unroll the loop more than 2 times of course, which should help a bit for bigger numbers, would need some measurements for optimal value
```
// assuming 8 bit per byte
#define MINBUFFERSIZE(type) ((((sizeof(type) * 8) << 16) + 217704) / 217705 + 1 + 1)

// szText needs to be a big enough Buffer, returns pointer to first written character within said Buffer
char* myitoa(int val, char *szText){
	
	char *pWrite = szText + MINBUFFERSIZE(val) - 2;
	char special = '\0';
	szText[MINBUFFERSIZE(val) - 1] = '\0';

	if (val <= 0) {
		special = (val == 0) ? '0' : '-';
		val = -val;
	} 
	
	// loopunrolling to keep multiple execution units happy	
	while (val >= 10) {
		int nextVal = (val / 100);
		pWrite[0]  = (val / 1 ) % 10 + '0';
		pWrite[-1] = (val / 10) % 10 + '0';
		val = nextVal;
		pWrite -= 2;
	}
	if (val)
		*pWrite-- = val + '0';
	if (special != '\0')
		*pWrite-- = special;

	return pWrite + 1;
}

#include <stdio.h>

int main() {
	char szText[MINBUFFERSIZE(int)];
	int somevalue = -1237784;
	printf("value is %d == %s\n", somevalue, myitoa(somevalue, szText));
	return 0;
}
```

---

### Post by Arndt on 2011-04-14
> **akvino said:**
> Everything in the program has to be quick. Yes I try to optimize everything where performance counts. If I need to preload data sets or read file, I can do it with the easiest tool for the job, but once I start real time processing - it needs to be as fast as possible.

That is why I LOVE c++ ):P

Is converting numbers to decimal form a central part of what the program does? Can you for example convert to hexadecimal instead (which is faster), and do the decimal conversion at a later stage?

---

### Post by BkkBonanza on 2011-04-14
I was very curious about the method described above using an array of constant strings so I wrote a short test function, and combined it in with the test code from the int_gen.cpp given for the Boost Spirit.Karma library.

Here is my results, (on a Core2Duo 1.6 laptop)

```

Converting 10000000 randomly generated int values to strings.
sprintf:	2.72156 [s]
iostreams:	2.69426 [s]
Boost.Format:	27.1962 [s]
Spirit.Karma:	4.67847 [s]
cvtint:		1.01976 [s]

```

My function "cvtint" actually performs better than the others. I'm very surprised to see that Spirit.Karma does NOT perform well on my machine. I don't know why.

As for my code I first generated a cvtint3.h constant string table with these bash commands (seemed easiest way to do it, and 3 digits seems like a good compromise):

```

echo "const char *cvtmap[] = {">cvtint3.h
for x in {0..999}; do echo -e "\"$x\"," >>cvtint3.h;done
echo "};">>cvtint3.h

```

And here's my function. I unrolled the loop since it only goes a few times and the last time is a special case anyway. 

```

#include "cvtint3.h"

void cvtint(int val, char *str)
{
	int div = 10000000;
	if(val < 0) {
		*str++ = '-';
		val = -val;
		}
	
	char *s = (char *)cvtmap[val / div];
	if(s != cvtmap[0])
		while(*s)
			*str++ = *s++;
			
	val %= div;
	div /= 1000;
	s = (char *)cvtmap[val / div];
	if(s != cvtmap[0])
		while(*s)
			*str++ = *s++;

	val %= div;
	div /= 1000;
	s = (char *)cvtmap[val / div];
	if(s != cvtmap[0])
		while(*s)
			*str++ = *s++;
			
	val %= div;
	div /= 10;
	s = (char *)cvtmap[val / div];
	while(*s)
		*str++ = *s++;
						
	*str = 0;
}

```

The final test program goes from 180k to 188k when I add my code. Around 80k of that is contributed by the Boost.Format library (not needed by my code)! 

If you want the test code and my build commands, just ask.

EDIT: Two sad notes... 
**1.** There's a bug in my code above for some numbers! I wonder if you can see it. 
**2.** I compiled with optimization -O2 and found that the code is much faster but *sigh* the Spirit.Karma code is close to mine. New speeds:

```

Using -O2,
Converting 10000000 randomly generated int values to strings.
sprintf:	2.69994 [s]
iostreams:	2.35942 [s]
Boost.Format:	17.0569 [s]
Spirit.Karma:	0.519185 [s]
cvtint:		0.489085 [s]

```

BTW the reason sprintf is used instead of ltoa is that I'm compiling with gcc and it doesn't have ltoa apparently. There may be a way to enable ltoa but I haven't come across that yet. This may also be why gcc appears slower then VC++ in the other results linked above. Not sure.

---

### Post by Arndt on 2011-04-14
If the speed of this is really so important, it seems it's time to study the assembler code generated, and see if you can improve the speed by writing in assembler.

---

### Post by akvino on 2011-04-14
> **BkkBonanza said:**
> I was very curious about the method described above using an array of constant strings so I wrote a short test function, and combined it in with the test code from the int_gen.cpp given for the Boost Spirit.Karma library.

Here is my results, (on a Core2Duo 1.6 laptop)

```

Converting 10000000 randomly generated int values to strings.
sprintf:	2.72156 [s]
iostreams:	2.69426 [s]
Boost.Format:	27.1962 [s]
Spirit.Karma:	4.67847 [s]
cvtint:		1.01976 [s]

```

My function "cvtint" actually performs better than the others. I'm very surprised to see that Spirit.Karma does NOT perform well on my machine. I don't know why.

As for my code I first generated a cvtint3.h constant string table with these bash commands (seemed easiest way to do it, and 3 digits seems like a good compromise):

```

echo "const char *cvtmap[] = {">cvtint3.h
for x in {0..999}; do echo -e "\"$x\"," >>cvtint3.h;done
echo "};">>cvtint3.h

```

And here's my function. I unrolled the loop since it only goes a few times and the last time is a special case anyway. 

```

#include "cvtint3.h"

void cvtint(int val, char *str)
{
	int div = 10000000;
	if(val < 0) {
		*str++ = '-';
		val = -val;
		}
	
	char *s = (char *)cvtmap[val / div];
	if(s != cvtmap[0])
		while(*s)
			*str++ = *s++;
			
	val %= div;
	div /= 1000;
	s = (char *)cvtmap[val / div];
	if(s != cvtmap[0])
		while(*s)
			*str++ = *s++;

	val %= div;
	div /= 1000;
	s = (char *)cvtmap[val / div];
	if(s != cvtmap[0])
		while(*s)
			*str++ = *s++;
			
	val %= div;
	div /= 10;
	s = (char *)cvtmap[val / div];
	while(*s)
		*str++ = *s++;
						
	*str = 0;
}

```

The final test program goes from 180k to 188k when I add my code. Around 80k of that is contributed by the Boost.Format library (not needed by my code)! 

If you want the test code and my build commands, just ask.

EDIT: Two sad notes... 
**1.** There's a bug in my code above for some numbers! I wonder if you can see it. 
**2.** I compiled with optimization -O2 and found that the code is much faster but *sigh* the Spirit.Karma code is close to mine. New speeds:

```

Using -O2,
Converting 10000000 randomly generated int values to strings.
sprintf:	2.69994 [s]
iostreams:	2.35942 [s]
Boost.Format:	17.0569 [s]
Spirit.Karma:	0.519185 [s]
cvtint:		0.489085 [s]

```

BTW the reason sprintf is used instead of ltoa is that I'm compiling with gcc and it doesn't have ltoa apparently. There may be a way to enable ltoa but I haven't come across that yet. This may also be why gcc appears slower then VC++ in the other results linked above. Not sure.

This is very interesting - I might try this...

---

### Post by akvino on 2011-04-14
> **Arndt said:**
> Is converting numbers to decimal form a central part of what the program does? Can you for example convert to hexadecimal instead (which is faster), and do the decimal conversion at a later stage?

Where I have known values I always use hex:
Example
char m_delimiter = 0x01;
later on
buffer[i] = m_delimiter;

However it would be less efficient to convert integer to hex and then char. If you know a fast way to do that, I am all ears.

---

### Post by akvino on 2011-04-14
BkkBonanza - have you tracked down why spirit.karma has such flacky performance? Is it the chipset or the compiler?

---

### Post by BkkBonanza on 2011-04-14
I think it's just a matter of optimization. Probably the benchmarks in that link were with -O2 (or equivalent) and I initially did not turn that on. Later when I did, the spirit.karma performance improved to about the same level as reported, relative to other methods.

I rewrote my last test code to fix my bug and it's quite different, not as nice, but it does perform about the same as spirit.karma. I kind of left it at that. I thought spirit.karma does amazingly well considering it's generated code and not specialized to the task and not using a large lookup table.

Interestingly I found that the spirit.karma speed varied depending on whether Boost.Format was compiled in or not. I had commented that section out for a while because it's so slow at runtime it bogs down the testing (17-30 seconds). When I added it in again the spirit.karma numbers got worse, so it was affected. Must be some interaction between libraries.

I also noticed that in the benchmark code there was statements added to convert the char buffer back to str objects after "to be fair" to the iostream test. But that final conversion actually cost around 30% more time! So I ran tests without that line as I don't see why the need to end with a string object if trying to maximize speed.

Edit - here is my last code and the times I got with it. I changed the cvtint3.h to be a single string of 0 padded values rather than an array. This was easier to use in fixing problems with "mid digit 0s"...

```

void cvtint(int val, char *str)
{
    if(val < 0) {
        *str++ = '-';
        val = -val;
        }
        
    int n;
    char *s0 = str;
    *s0 = 0;
    
    if(n = val / 10000000 * 3) {
        if(n >= 300) *str++ = cvtmap[n];
        if(n >= 30) *str++ = cvtmap[n+1];
        *str++ = cvtmap[n+2];
    }
    val %= 10000000;
    if((n = val / 10000 * 3) || *s0 )  {
        if(*s0 || n >= 300) *str++ = cvtmap[n];
        if(*s0 || n >= 30) *str++ = cvtmap[n+1];
        *str++ = cvtmap[n+2];
    }
    val %= 10000;
    if((n = val / 10 * 3 ) || *s0) {
        if(*s0 || n >= 300) *str++ = cvtmap[n];
        if(*s0 || n >= 30) *str++ = cvtmap[n+1];
        *str++ = cvtmap[n+2];
    }
    *str++ = '0' + val % 10;
    *str = 0;
}

```

bash steps to create new cvtint3.h
```

printf "char cvtmap[]=\"" > cvtint3.h
for x in {0..999}; do printf "%03d" $x >>cvtint3.h; done
printf "\";" >> cvtint3.h

```

Times:
```

Converting 10000000 randomly generated int values to strings.
sprintf:	2.68784 [s]
iostreams:	2.36409 [s]
Boost.Format:	16.6129 [s]
Spirit.Karma:	0.51694 [s]
cvtint:		0.501351 [s]

```

It's been fun messing with this and reading the spirit.karma docs.

---

### Post by Arndt on 2011-04-14
> **akvino said:**
> Where I have known values I always use hex:
Example
char m_delimiter = 0x01;
later on
buffer[i] = m_delimiter;

However it would be less efficient to convert integer to hex and then char. If you know a fast way to do that, I am all ears.

What syntax you use in the source code doesn't affect the speed of the program.

Converting integers to their decimal representation requires dividing by 10. Converting to hex or octal only requires bit shifting.

I don't know what you mean by "integer to hex and then char". There is only one representation of numbers in the memory of the running program, regardless of how you specified them in the source code.

I'm still curious what application would require conversion of numbers to decimal in real time.

---

### Post by BkkBonanza on 2011-04-14
I don't know what the OP is doing but an example, maybe, of converting int to string could be a logging function where the data is coming in very quickly and you don't want the logging to affect the data performance - eg. perhaps network filtering.

I thought you had a good idea with the hex as an intermediate step as outputing hex values would be very fast compared to decimal. But I don't know what the intention is - I'm just playing with this for my own amusement. as I wanted to do some test compiles to see how that spirit.karma thing works.

---

### Post by akvino on 2011-04-14
> **Arndt said:**
> What syntax you use in the source code doesn't affect the speed of the program.

Converting integers to their decimal representation requires dividing by 10. Converting to hex or octal only requires bit shifting.

I don't know what you mean by "integer to hex and then char". There is only one representation of numbers in the memory of the running program, regardless of how you specified them in the source code.

I'm still curious what application would require conversion of numbers to decimal in real time.

As I stated earlier I am normalizing streaming data on higher level network protocols. I sometimes need to send response back, according to protocl specs, and pending how fast I generate message, I need to convert internal integer information into ASCII, since the protocol is ASCII.

---

### Post by Arndt on 2011-04-14
> **akvino said:**
> As I stated earlier I am normalizing streaming data on higher level network protocols. I sometimes need to send response back, according to protocl specs, and pending how fast I generate message, I need to convert internal integer information into ASCII, since the protocol is ASCII.

Is this some standard protocol?

I would think that the cost of sending a packet, or even of just making one 'write' call to the kernel is much higher than converting a number to decimal (but maybe the whole thing is done in one single context). Have you done measurements?

---

### Post by akvino on 2011-09-27
> **Npl said:**
> Well, good compilers should be able to optimize the division by small constant values away (just checked and atleast MSVC does this). For this reason a itoa with a fixed base should be faster.

Heres my take, should handily beat most library code. You can unroll the loop more than 2 times of course, which should help a bit for bigger numbers, would need some measurements for optimal value
```
// assuming 8 bit per byte
#define MINBUFFERSIZE(type) ((((sizeof(type) * 8) << 16) + 217704) / 217705 + 1 + 1)

// szText needs to be a big enough Buffer, returns pointer to first written character within said Buffer
char* myitoa(int val, char *szText){
	
	char *pWrite = szText + MINBUFFERSIZE(val) - 2;
	char special = '\0';
	szText[MINBUFFERSIZE(val) - 1] = '\0';

	if (val <= 0) {
		special = (val == 0) ? '0' : '-';
		val = -val;
	} 
	
	// loopunrolling to keep multiple execution units happy	
	while (val >= 10) {
		int nextVal = (val / 100);
		pWrite[0]  = (val / 1 ) % 10 + '0';
		pWrite[-1] = (val / 10) % 10 + '0';
		val = nextVal;
		pWrite -= 2;
	}
	if (val)
		*pWrite-- = val + '0';
	if (special != '\0')
		*pWrite-- = special;

	return pWrite + 1;
}

#include <stdio.h>

int main() {
	char szText[MINBUFFERSIZE(int)];
	int somevalue = -1237784;
	printf("value is %d == %s\n", somevalue, myitoa(somevalue, szText));
	return 0;
}
```


Can you explain why 217704 and 217705 +1 +1, in the following #define?

#define MINBUFFERSIZE(type) ((((sizeof(type) * 8) << 16) + 217704) / 217705 + 1 + 1)

---

### Post by akvino on 2012-04-19
> **Arndt said:**
> Is this some standard protocol?

I would think that the cost of sending a packet, or even of just making one 'write' call to the kernel is much higher than converting a number to decimal (but maybe the whole thing is done in one single context). Have you done measurements?

The protocol in mind uses multicast as the underlying standard protocol part, everything else is standard only in the customers universe. :-)

---

### Post by 11jmb on 2012-04-19
> **akvino said:**
> Where I have known values I always use hex:
Example
char m_delimiter = 0x01;
later on
buffer[i] = m_delimiter;

However it would be less efficient to convert integer to hex and then char. If you know a fast way to do that, I am all ears.

hex is just a different (and much more computationally efficient) way to format the string. try using %X instead of %d in your sprintf benchmark. I bet you will see a huge speed increase, especially for larger numbers.

Knowing how much more efficient hex is, would formatting your ints as such work for you?

---

### Post by akvino on 2012-04-19
> **11jmb said:**
> hex is just a different (and much more computationally efficient) way to format the string. try using %X instead of %d in your sprintf benchmark. I bet you will see a huge speed increase, especially for larger numbers.

Knowing how much more efficient hex is, would formatting your ints as such work for you?

I understand where you coming from but either way you can't escape conversion.

---

### Post by 11jmb on 2012-04-20
Right, but bit shifts are much more efficient than dividing by 10, and you haven't answered the question: are strings formatted as hex ints acceptable for your program?


For example, will the program choke anywhere if it gets "0xF4240" instead of "1000000"?

---

