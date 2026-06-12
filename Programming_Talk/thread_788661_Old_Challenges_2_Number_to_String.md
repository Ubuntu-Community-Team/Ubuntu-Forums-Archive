---
title: "Old Challenges 2: Number to String"
date: 2008-05-09
forum: Programming Talk
---

### Post by JupiterV2 on 2008-05-09
I chose C++ for my plan of attack this time around. I haven't looked at anyone else's responses in the old thread yet but I'm sure there is a better way to have done this. Some of the features of Python strike me as being better suited to the task but since I'm still learning Python...

**Constructive** criticism welcome. :)

[php]
#include <iostream>
#include <sstream>
#include <cstdlib>

std::string create_hundred(int num)
{
	const char* single_d[10] = {"zero", "one", "two", "three", "four", "five", 
		"six", "seven", "eight", "nine"};	
	const char* teen_d[9] = {"eleven", "twelve", "thirteen", "fourteen", 
		"fifteen", "sixteen", "seventeen", "eighteen", "nineteen"};
	const char* double_d[9] = {"ten", "twenty", "thirty", "forty", "fifty", 
		"sixty", "seventy", "eighty", "ninety"};
	
	int mod, remainder;
	
	std::ostringstream os;
	
	for(int x = 100; x >= 0; x /= 10)
	{
		mod = num / x;
		remainder = num - (mod * x);

		if( mod > 0 )
		{
			switch(x)
			{
				case 1: os << single_d[mod]; break;
				case 10: 
					if( num > 19 ) 
					{
						os << double_d[mod - 1];
						if( remainder ) os << "-";
					}
					else 
					{
						os << teen_d[remainder - 1];
						if( mod ) os << " ";
						remainder = 0;
					}
					break;
				case 100: 
					os << single_d[mod] << " hundred"; 
					if( remainder ) os << " "; 
					break;
			}
		}
		if( !(num = remainder) ) break;
	}
	
	return os.str();
}

std::string int_to_alpha(int num)
{	
	int mod, remainder;
	
	std::ostringstream os;
	
	for(int x = 1000000; x >= 0; x /= 1000)
	{
		mod = num / x;
		remainder = num - (mod * x);
	
		if( mod > 0 )
		{
			os << create_hundred(mod);
			
			switch(x)
			{
				case 1000: 
					if( mod) os << " ";
					os << "thousand"; 
					if( remainder ) os << ",";
					break;
				case 1000000: 
					os << " million";
					if( remainder ) os << ",";
					break;
			}
			if( mod ) os << " ";
		}
		if( !(num = remainder) ) break;
	}
	
	return os.str();
}

int main(int argc, char** argv)
{
	
	if( argc != 2 )
	{
		std::cout << "Usage: test <number>\n";
		return 1;
	}

	int num = atoi(argv[1]);
	std::cout << num << " = " << int_to_alpha(num) << std::endl;
	return 0;
}[/php]

---

### Post by Wybiral on 2008-05-09
Why not just reply to the old challenge instead of starting a new thread?

---

### Post by dwhitney67 on 2008-05-09
Interesting code, however I believe (actually I'm certain) that you have a bug at this line:
[PHP]if( !(num = remainder) ) break;[/PHP]
You need to use the '==' for comparisons.  Try deciphering the number 90 with your existing code; you will see the bug first hand.

---

### Post by JupiterV2 on 2008-05-10
> **Wybiral said:**
> Why not just reply to the old challenge instead of starting a new thread?

The first thread was locked so I assumed they all were. I'll do so from now on, thanks.

> 
Interesting code, however I believe (actually I'm certain) that you have a bug at this line:
PHP Code:
if( !(num = remainder) ) break; 
You need to use the '==' for comparisons. Try deciphering the number 90 with your existing code; you will see the bug first hand. 

I'm not sure what output you receive when you run the program but it works as intended for me.

[PHP]if( !(num = remainder) ) break;[/PHP]

...evaluates to if 'number', which now equals 'remainder', is zero then break.

My output:
```
$ ./ubu_ita 90
90 = ninety
```

---

### Post by dwhitney67 on 2008-05-10
Sorry, my bad... try running with the number 10.  Then the error is apparent.

```
$ a.out 10
10 = ninety 
```

---

### Post by rye_ on 2008-05-10
Edit

---

### Post by JupiterV2 on 2008-05-10
> **dwhitney67 said:**
> Sorry, my bad... try running with the number 10.  Then the error is apparent.

```
$ a.out 10
10 = ninety 
```

Awesome, thanks for helping me find the error!

After a brainstorm last night while lying in bed I decided to modify the for loop in int_to_alpha() instance, as well.

I wanted to make it easily expandable. Now, if I want to make it go to billion or trillion I can simply increase the initial value of x in the for loop and add the appropriate case whereas before I would have had to use overly large numbers (1,000,000,000,000).

I could have modified the code in create_hundred() but it didn't seem a worthwhile investment of CPU time considering there is no reason to allow for expansion.

Here is the new code with modifications noted:

[PHP]#include <cmath>
#include <cstdlib>
#include <iostream>
#include <sstream>

/* swapped "ten" from double_d to teen_d an made appropriate adjustments */
std::string create_hundred(int num)
{
	const char* single_d[10] = {"zero", "one", "two", "three", "four", "five", 
		"six", "seven", "eight", "nine"};	
	const char* teen_d[10] = {"ten", "eleven", "twelve", "thirteen", "fourteen", 
		"fifteen", "sixteen", "seventeen", "eighteen", "nineteen"};
	const char* double_d[8] = {"twenty", "thirty", "forty", "fifty", 
		"sixty", "seventy", "eighty", "ninety"};
	
	int mod, remainder;
	
	std::ostringstream os;
	
	for(int x = 100; x >= 0; x /= 10)
	{
		mod = num / x;
		remainder = num - (mod * x);

		if( mod > 0 )
		{
			switch(x)
			{
				case 1: os << single_d[mod]; break;
				case 10: 
					if( num > 19 ) 
					{
						os << double_d[mod - 2];
						if( remainder ) os << "-";
					}
					else 
					{
						os << teen_d[remainder];
						if( mod ) os << " ";
						remainder = 0;
					}
					break;
				case 100: 
					os << single_d[mod] << " hundred"; 
					if( remainder ) os << " "; 
					break;
			}
		}
		if( !(num = remainder) ) break;
	}
	
	return os.str();
}

/* To handle numbers up to a trillion, change int to long and increase the
 * initial value of x within the for loop and add the appropriate case's in
 * the switch statement */
std::string int_to_alpha(int num)
{	
	int mod, remainder;
	
	std::ostringstream os;
	
	for(int x = 2; x >= 0; x--)
	{
		int y = (int) pow(1000, x);
		mod = num / y;
		remainder = num - (mod * y);
	
		if( mod > 0 )
		{
			os << create_hundred(mod);
			
			switch(x)
			{
				case 1: 
					if( mod) os << " ";
					os << "thousand"; 
					if( remainder ) os << ",";
					break;
				case 2: 
					os << " million";
					if( remainder ) os << ",";
					break;
			}
			if( mod ) os << " ";
		}
		if( !(num = remainder) ) break;
	}
	
	return os.str();
}

int main(int argc, char** argv)
{
	
	if( argc != 2 )
	{
		std::cout << "Usage: test <number>\n";
		return 1;
	}

	int num = atoi(argv[1]);
	std::cout << num << " = " << int_to_alpha(num) << std::endl;
	return 0;
}[/PHP]

---

### Post by dwhitney67 on 2008-05-10
A couple of more suggestions that perhaps I should have noted earlier.  In the following statements:
[PHP]mod = num / x;
remainder = num - (mod * x);[/PHP]

the variable name 'mod' is confusing because it actually represents the whole number, not the modulo of the operation (which is the remainder).

Also, to compute the remainder, it would be easier to construct a statement like:
[PHP]remainder = num % x;    // % is the modulo operator.[/PHP]

So, 150 % 100 = 50; similarly, 1010 % 1000 = 10.

Anyhow, I personally would have named the variables 'div' and 'mod', but that's merely my opinion.

Good luck with the rest of your programming exercises!

---

### Post by WW on 2008-05-11
> **Wybiral said:**
> Why not just reply to the old challenge instead of starting a new thread?

LaRoza is pretty quick to close threads that are revived after being dormant for a year or so.  The old palindrome thread was closed a little while ago.  LaRoza, what's up with that?  What's wrong with continuing a thread that has been dormant for a while?

---

### Post by JupiterV2 on 2008-05-11
> **WW said:**
> LaRoza is pretty quick to close threads that are revived after being dormant for a year or so.  The old palindrome thread was closed a little while ago.  LaRoza, what's up with that?  What's wrong with continuing a thread that has been dormant for a while?

I was wondering the same thing. I wanted to change my code I submitted because my make_palindrome() function was just...well...terrible. ;)

---

### Post by dwhitney67 on 2008-05-11
I figure I would also attempt to solve the "Number to String" problem.  Below is my solution.  I handles number from 0 to 99,999,999... at least I think so.  I couldn't possibly test every number.

Num2Str.cpp:
[PHP]#include "NumString.h"

#include <iostream>
#include <unistd.h>

using std::cout;
using std::endl;


void printUsage( const char *appName );


int main( int argc, char **argv )
{
  if ( argc < 2 )
  {
    printUsage( argv[0] );
    return 1;
  }
  --argc; ++argv;

  NumString num2str;

  for ( unsigned int arg = 0; arg < argc; ++arg )
  {
    const unsigned int number = atoi( argv[ arg ] );

    cout << "The number " << number << " is: " << num2str.convertNumber( number ) << endl;
  }

  return 0;
}

void printUsage( const char *appName )
{
  cout << "Usage: " << appName << " <number> [number] ... [number]" << endl;
}[/PHP]

NumString.h:
[PHP]#ifndef NUM_STRING_H
#define NUM_STRING_H

#include <map>
#include <string>


class NumString : public std::map<unsigned int, std::string>
{
  public:
    NumString();

    std::string convertNumber( unsigned int number );

    std::string operator[]( const unsigned int key );
};

#endif[/PHP]

NumString.cpp:
[PHP]#include "NumString.h"
#include <sstream>

using std::pair;
using std::string;
using std::ostringstream;


NumString::NumString()
{
  this->insert( pair<unsigned int, string>( 0, "zero" ) );
  this->insert( pair<unsigned int, string>( 1, "one" ) );
  this->insert( pair<unsigned int, string>( 2, "two" ) );
  this->insert( pair<unsigned int, string>( 3, "three" ) );
  this->insert( pair<unsigned int, string>( 4, "four" ) );
  this->insert( pair<unsigned int, string>( 5, "five" ) );
  this->insert( pair<unsigned int, string>( 6, "six" ) );
  this->insert( pair<unsigned int, string>( 7, "seven" ) );
  this->insert( pair<unsigned int, string>( 8, "eight" ) );
  this->insert( pair<unsigned int, string>( 9, "nine" ) );
  this->insert( pair<unsigned int, string>( 10, "ten" ) );
  this->insert( pair<unsigned int, string>( 11, "eleven" ) );
  this->insert( pair<unsigned int, string>( 12, "twelve" ) );
  this->insert( pair<unsigned int, string>( 13, "thirteen" ) );
  this->insert( pair<unsigned int, string>( 14, "fourteen" ) );
  this->insert( pair<unsigned int, string>( 15, "fifteen" ) );
  this->insert( pair<unsigned int, string>( 16, "sixteen" ) );
  this->insert( pair<unsigned int, string>( 17, "seventeen" ) );
  this->insert( pair<unsigned int, string>( 18, "eighteen" ) );
  this->insert( pair<unsigned int, string>( 19, "nineteen" ) );
  this->insert( pair<unsigned int, string>( 20, "twenty" ) );
  this->insert( pair<unsigned int, string>( 30, "thirty" ) );
  this->insert( pair<unsigned int, string>( 40, "forty" ) );
  this->insert( pair<unsigned int, string>( 50, "fifty" ) );
  this->insert( pair<unsigned int, string>( 60, "sixty" ) );
  this->insert( pair<unsigned int, string>( 70, "seventy" ) );
  this->insert( pair<unsigned int, string>( 80, "eighty" ) );
  this->insert( pair<unsigned int, string>( 90, "ninety" ) );
  this->insert( pair<unsigned int, string>( 100, "hundred" ) );
  this->insert( pair<unsigned int, string>( 1000, "thousand" ) );
  this->insert( pair<unsigned int, string>( 1000000, "million" ) );
}


std::string
NumString::convertNumber( unsigned int number )
{
  ostringstream os;

  if ( number == 0 )
  {
    os << (*this)[ number ];
  }
  else
  {
    for ( unsigned int i = 1000000; i > 0; i /= 10 )
    {
      unsigned int div = number / i;
      unsigned int mod = number % i;

      if ( div != 0 )
      {
        switch ( i )
        {
          case 1:
              os << (*this)[ div ] << " ";                  // for [1, 9]
              break;

          case 10:
              if ( mod == 0 )                               // for [20, 90], no remainder
              {
                os << (*this)[ div * i ] << " ";
                i = 0;
              }
              else if ( div * i + mod < 20 )                // for [11, 19]
              {
                os << (*this)[ div * i + mod ] << " ";
                i = 0;
              }
              else                                          // for [20, 90], with remainder
              {
                os << (*this)[ div * i ] << " ";
                number -= div * i;
              }
              break;

          case 100:
              os << (*this)[ div ] << " " << (*this)[ i ] << " ";
              number -= div * i;
              break;

          case 1000: 
          case 1000000:
              if ( (*this)[ div ] == "?" || div >= 100 )
              {
                os << convertNumber( div ) << (*this)[ i ] << " ";
                number = mod;
              }
              else
              {
                os << (*this)[ div ] << " " << (*this)[ i ] << " ";
                number -= div * i;
              }
              break;
        }
      }
    }
  }

  return os.str();
}


string
NumString::operator[]( const unsigned int key )
{
  NumString::iterator iter = this->find( key );

  if ( iter == this->end() )
    return "?";

  return iter->second;
}[/PHP]

---

### Post by JupiterV2 on 2008-05-11
> **dwhitney67 said:**
> I figure I would also attempt to solve the "Number to String" problem.  Below is my solution.  I handles number from 0 to 99,999,999... at least I think so.  I couldn't possibly test every number.

Actually, it handles up to 999,999,999. =) All the numbers I tested it with worked.

I learned 2 things: When I switched my solution from C to C++ I should have taken more advantage of the STL. Second, I never would have thought to inherit the map STL in that way. I would have made the map a variable within NumString but your solution is much more intuitive. Nice!

Question: When inserting the number/word pairs within the constructor, is not *this implied (ie: this->insert(...) vs. insert(...))? Or, did you do this for clarity/robustness?

---

### Post by dwhitney67 on 2008-05-11
I used the "this->" in the constructor (for my sake) for clarity.

---

### Post by dwhitney67 on 2008-05-11
I entered 9,999,999,999, and atoi() correctly returned the max 32-bit unsigned integer of 2,147,483,647.  My code correctly decoded the value and printed to correct string.  Woo hoo!

---

### Post by Wybiral on 2008-05-12
> **JupiterV2 said:**
> The first thread was locked so I assumed they all were. I'll do so from now on, thanks.

Sorry about that advice, I thought the mods would be more interested in stopping duplicate threads than stopping old threads from coming back... I was wrong :(

---

