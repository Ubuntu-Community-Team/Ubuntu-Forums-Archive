---
title: "Need some C++ help"
date: 2008-02-13
forum: Programming Talk
---

### Post by skipsbro on 2008-02-13
Hello all! I'm just getting into C++ programming and I need a bit of help with one of my first scripts 

```
#include<stdio.h>

    int main()
{
    int f;
    f = 440;
    
    int p;
    p = 69 + 12* LOG(f/440:2); 

    if (p == 69)
    {
        printf("The frequency is A440\n");
    }
    if (p > 69)
    {
        printf("The frequency is higher than A4\n");
    }
    if (p < 69)
    {
        printf("The frequency is lower than A4\n");
    }
}

```

That's what I have so far, and the problem is with the formula above that P is set to. I would also like to know how to get F to be asked where it can be changed each time the program is used. Thanks in advance!

---

### Post by t3hi3x on 2008-02-13
well...a couple things

To use LOG() you need to include math.h

To pull a number in you can use std::cin >> f;
but you need to include iostream.

I'm sure this can be done with just c, but I don't know C all that well :)

if this doesnt compile, then let me know

so...```


#include<stdio.h>
#include<math.h>
#include<iostream>

int main()
{
int f;
//f = 440;

//get f

printf("What is f?\n");

std::cin >> f;

int p;
p = 69 + 12* LOG(f/440:2);

if (p == 69)
{
printf("The frequency is A440\n");
}
if (p > 69)
{
printf("The frequency is higher than A4\n");
}
if (p < 69)
{
printf("The frequency is lower than A4\n");
}
}


```

---

### Post by LittleLORDevil on 2008-02-13
Just a style thing but "else if" statements are a little better style.

---

### Post by PaulFr on 2008-02-14
I think

1. LOG should be log.
2.```
p = 69 + 12 * log(f/**440:2**);
```does not look right. What is **440:2** ?

---

### Post by vishzilla on 2008-02-14
the program doesnt make sense, the program will return an integer, you have to include 'return 0;' and what is **440:2**

---

### Post by pedro_orange on 2008-02-14
I concur.

You're missing the application return code, return 0;
Because you've set this application as int main() you must return an integer. 0 is telling the OS your application completed successfully.

Is 420:2 some kind of ratio? :P Perhaps it's just a typo.
That will surely return an error.

```
if(condition){
}
else if(condition){
}
else{
}
```

is acceptable. Or you could try a switch if you wanted to be fancy:

```
switch(condition){

case 1:
//blah
break;

case2:
break;

case3:
break;

default:
break;
}
```

Also, instead of printf you can use cout which gives you more formatting options. But you need to include <iostream> library (Although you should be including this if you're trying to use cin!)

---

### Post by amingv on 2008-02-14
Why are you using stdio.h? Are you trying to program this in C or C++?

---

### Post by mike_g on 2008-02-14
From what I have heard there is no need to add "return 0;" to the end of main as this is assumed by the compiler.

Also when compiling using math.h via CL you need to link it by adding: -lm

---

### Post by LaRoza on 2008-02-14
> **mike_g said:**
> From what I have heard there is no need to add "return 0;" to the end of main as this is assumed by the compiler.


It depends on the compiler, but it isn't standard.

I just compiled a program without a return value, and it returned "15" for some reason. I doubt that is what you want.

Follow the standards and don't rely on bugs.

---

### Post by pedro_orange on 2008-02-14
The return value from an application tells the Operating system how the application exited. 
ie, if there was an error and didn't complete successfully. 

I don't know what a return code of 15 means without looking it up. But I guess Laroza's point was that if you don't tell it how to exit, it can exit in any number of ways. 

Remember kids, always return 0! (Unless you don't want it to complete successfully!)

---

### Post by CptPicard on 2008-02-14
It's possible that it even returns whatever is in the memory location where main's return value is expected to be on the (empty) stack...but just a wild guess.

---

### Post by LaRoza on 2008-02-14
> **CptPicard said:**
> It's possible that it even returns whatever is in the memory location where main's return value is expected to be on the (empty) stack...but just a wild guess.

I thought so too, and I reran it, it was 15 again, so I recompiled it. It was still 15.

Maybe that error code means "Someone who doesn't follow standards".

---

### Post by CptPicard on 2008-02-14
You mean a bit like [doctor slang]("http://news.bbc.co.uk/2/hi/health/3159813.stm")? :)

---

### Post by LaRoza on 2008-02-14
> **CptPicard said:**
> You mean a bit like [doctor slang]("http://news.bbc.co.uk/2/hi/health/3159813.stm")? :)

Nice article. (Now I have to go speak to my doctor...)

Actually, once I was at the dentist with a tiny surface cavity (my first one), and I am afraid of dentists....

I am in the reclining chair, this light is in my face, he looks into my mouth (and I have this tool of unknown use in there already) and he says "Ah, POC". I look at the assistant (don't know formal title) with a worried look and say "What does that mean?!", actually, because of the thing in my mouth of unknown use it came out "Wah dah thah mean?". It only meant "Piece of Cake", for those that aren't use to this phrase, it means it will be simple to fix.

---

### Post by pmasiar on 2008-02-14
@OP:

Looks like you are beginner programmer just learning C++? You may want to read [New to C and programming](http://ubuntuforums.org/showthread.php?t=395403). Summary: C or C++ good and useful languges to know, but not the best languages to start learning programming. :-)

IMHO that thread should be linked from FAQs, and you should read FAQs anyway...

---

### Post by aks44 on 2008-02-14
> **CptPicard said:**
> It's possible that it even returns whatever is in the memory location where main's return value is expected to be on the (empty) stack...but just a wild guess.

The convention both on Linux & Windows is to return values in eax (plus edx for 64 bit values) unless the value doesn't fit in those registers, in which case the stack *may* be used (and/or the heap IIRC, depending the compiler).

Calling conventions, name-mangling etc for various compilers & platforms:
[http://www.agner.org/optimize/calling_conventions.pdf](http://www.agner.org/optimize/calling_conventions.pdf)


Back to LaRoza's return value of 15... well, your program left that value in eax. ;)

---

### Post by LaRoza on 2008-02-14
> **aks44 said:**
> Back to LaRoza's return value of 15... well, your program left that value in eax. ;)

On every compile and time I ran it?

Tried again, this time using tcc, and it still returns 15, and even when being interpreted.

---

### Post by aks44 on 2008-02-14
> **LaRoza said:**
> On every compile and time I ran it?

Looks like the last time eax is updated in your program, it is given (for some reason) the value 15.
This could be a result of a previous function, or because that register is used as a temporary storage. eax is part of the "scratch" registers, so it is not necessarily changed by *your* code, it can be changed by anything that your code calls.
Without tracing at the ASM level (including the library calls) it will be hard to tell where exactly...


> **LaRoza said:**
> Tried again, this time using tcc, and it still returns 15, and even when being interpreted.

This is not a matter of compiler, since this return convention comes from C, which makes it a de-facto standard.
The "even when interpreted" part is a bit intriguing though, but I have no single clue about tcc's interpreter architecture...

:)

---

### Post by LaRoza on 2008-02-14
> **aks44 said:**
> This is not a matter of compiler, since this return convention comes from C, which makes it a de-facto standard.
The "even when interpreted" part is a bit intriguing though, but I have no single clue about tcc's interpreter architecture...

:)

Some compilers make main return an int, even if it is declared void, gcc is supposed to return 1 if nothing is explicitly stated. (Reading the gcc docs, that may be old)

Some return 0, however, tcc, and gcc make it 15 for some reason. Unless that number is permanently stuck in eax, there must be a reason for it.

---

### Post by aks44 on 2008-02-14
> **LaRoza said:**
> Some compilers make main return an int, even if it is declared void, gcc is supposed to return 1 if nothing is explicitly stated.

```
int whatever()
{
  return 42;
}

int main()
{
  int x = whatever();
  x = 0;
}
``````
$ gcc -o test test.c
$ ./test ; echo $?
42
```

----------------------------------------

```
int main()
{
}
``````
$ gcc -o test test.c
$ ./test ; echo $?
52
$ ./test ; echo $?
148
$ ./test ; echo $?
20
```

----------------------------------------

I believe this is enough to show that gcc itself doesn't enforce a specific return value when no return statement is present.


> **LaRoza said:**
> Some return 0, however, tcc, and gcc make it 15 for some reason. Unless that number is permanently stuck in eax, there must be a reason for it.
Again, that reason is either in the code you wrote, or in the library calls you make. It just happens that, due to the executed code, eax always equals to 15 before leaving your program. We've seen much stranger things... ;)


EDIT: BTW, we're dealing with plain *Undefined Behaviour* here (not *Implementation Defined*, mind you), so no wonder gcc's behaviour is a bit irrational... ;)

---

### Post by LaRoza on 2008-02-14
[php]
void main(void)
{
;
}
[/php]

This returns 1 just like the gcc docs stated, when compiled with gcc. It returns 0 when interpreted by tcc.

You are right, it was the function call in the code.

---

### Post by skipsbro on 2008-02-14
Thank you so much for the help so far

> **PaulFr said:**
> I think

1. LOG should be log.
2.```
p = 69 + 12 * log(f/**440:2**);
```does not look right. What is **440:2** ?

the "log(f/440:2)" Is the only way I know of to do a Log base 2

---

### Post by Jessehk on 2008-02-14
There is a log2 function in <cmath>, but I'd probably do something like this:
```

#include <cmath>
#include <iostream>

template <int base>
float log( float x ) {
    return std::log( x ) / std::log( base );
}

int main() {
    std::cout << log<2>( 440 ) << std::endl;
}

```

---

### Post by hod139 on 2008-02-14
> **Jessehk said:**
> There is a log2 function in <cmath>, but I'd probably do something like this:
```

#include <cmath>
#include <iostream>

template <int base>
float log( float x ) {
    return std::log( x ) / std::log( base );
}

int main() {
    std::cout << log<2>( 440 ) << std::endl;
}

```

I like the use of the specialized (partialized?) template parameter, but why did you stop there?  Why are you using a float instead of a double?  Why not template that type, or just use a double instead of the float (you won't see a performance loss on a modern cpu using a double instead of a float)?

```

template <int base, typename T>
T log( T x ) {
    return std::log( x ) / std::log( base );
}

```
or
```

template <int base>
  double log( double x ) {
    return std::log( x ) / std::log( base );
}

```

---

### Post by t3hi3x on 2008-02-15
Very informative conversation. Thanks.

---

### Post by skipsbro on 2008-02-18
Alright, I've made the changes that have been suggested, and I think I've created a monster. 
```
#include<stdio.h>
#include<math.h>
#include<cmath>
#include<iostream>

	template <int base, typename T>
	T log( T x ) 
{
    return std::log( x ) / std::log( base );
}

	int main()
{
	int f;
	printf("What is f?\n");
	std::cin >> f;
	
	int a;
	a = std::cout << log<2>( 440 ) << std::endl;

	int p;
	p = 69 +  12 * a

	if (p == 69)
	{
		printf("The frequency is A440\n");
	}
	if (p > 69)
	{
		printf("The frequency is higher than A4\n");
	}
	if (p < 69)
	{
		printf("The frequency is lower than A4\n");
	}

	return 0;
}

```

I obviously need more help and am beginning to question if I was ready for this kind of script

---

### Post by Zwack on 2008-02-18
> **skipsbro said:**
> Alright, I've made the changes that have been suggested, and I think I've created a monster. 


You shouldn't be mixing stdio and iostream so complete the conversion

```

#include<cmath>
#include<iostream>

template <int base, typename T>
        T myLog( T x )
{
    return std::log( x ) / std::log( base );
}

        int main()
{
        using namespace std;

        int f;
        cout << "What is f? " << endl;

        cin >> f;

        int a;
        a = myLog<2>(440); // Where does f go?

        int p;
        p = 69 +  12 * a;

        if (p == 69) {
                cout << "The frequency is A440" <<endl; //Should this be A4?
        }
        else if (p > 69) {
                cout << "The frequency is higher than A4" << endl;
        }
        else {  // If it's not greater than 69, or equal to 69 why test...
                cout << "The frequency is lower than A4" << endl;
        }

        return 0;
}


```

The big problem is you're not using f at all now... Sure you get someone to tell you what f is but then you don't use it.  I also put some missing ; in, removed the use of iostream in the setting of a, and did some small amounts of tidying up... and I renamed your log template so that I could use the std namespace to save me some typing...

And most of the numbers you are dealing with are integers, so if you're interested in fractional results (e.g. f/440) then you should take that into account.

Z.

---

### Post by Jessehk on 2008-02-18
> **skipsbro said:**
> Alright, I've made the changes that have been suggested, and I think I've created a monster. 
```
#include<stdio.h>
#include<math.h>
#include<cmath>
#include<iostream>

	template <int base, typename T>
	T log( T x ) 
{
    return std::log( x ) / std::log( base );
}

	int main()
{
	int f;
	printf("What is f?\n");
	std::cin >> f;
	
	int a;
	a = std::cout << log<2>( 440 ) << std::endl;

	int p;
	p = 69 +  12 * a

	if (p == 69)
	{
		printf("The frequency is A440\n");
	}
	if (p > 69)
	{
		printf("The frequency is higher than A4\n");
	}
	if (p < 69)
	{
		printf("The frequency is lower than A4\n");
	}

	return 0;
}

```

I obviously need more help and am beginning to question if I was ready for this kind of script

There are so many errors in that code, that rather than try to help you fix it, why don't you explain *what* exactly you're trying to write? :)

---

### Post by Zwack on 2008-02-18
> **Jessehk said:**
> There are so many errors in that code, that rather than try to help you fix it, why don't you explain *what* exactly you're trying to write? :)

If nobody shows him where he went wrong then he's not going to learn...

Thus the correcting of errors...

There weren't that many... a few missing semi-colons...

a = cout << .... 

is odd and I can only guess that there was originally a cout << ... that was changed to a=...

a and p can be recombined now, but I want to know what happened to f...

Z.

---

### Post by Zwack on 2008-02-18
Reading the original and doing some selective googling it looks like there is a conversion into midi notes going on...

The formula I found to convert from a frequency (f) to a midi note X is

X=69 + (440 * 2^(f/12))

Presumably this is intended to work back to the frequency fron the midi note...

But the comparison at the end belies that...(A above middle C is 440Hz is midi note 69)

Z.

---

### Post by Jessehk on 2008-02-18
> **Zwack said:**
> If nobody shows him where he went wrong then he's not going to learn...

Thus the correcting of errors...

There weren't that many... a few missing semi-colons...

a = cout << .... 

is odd and I can only guess that there was originally a cout << ... that was changed to a=...

a and p can be recombined now, but I want to know what happened to f...

Z.

You're missing the point. The code is so error-full that he clearly does not understand what the code is actually doing. Instead of simply fixing his errors, he should  be able to clearly explain what the code should actually do.

For example, 
```

loop 3 times
   get user input
   print the square of the input
end loop

```

If he can explain what the code **should** do, the members here can properly explain and teach him **how** to do it.

---

### Post by Zwack on 2008-02-18
> **Jessehk said:**
> You're missing the point. The code is so error-full that he clearly does not understand what the code is actually doing. Instead of simply fixing his errors, he should  be able to clearly explain what the code should actually do.


There are many styles of teaching...  Simply saying "There are too many errors" is not teaching.  

Yes, he needs to be able to explain what the code should actually do, but that doesn't belie the fact that he has produced some code that doesn't work.

Stating that it doesn't work doesn't tell him anything he doesn't know.

Pointing out that he's missing some semi-colons does.

As does correcting errors.  Presumably providing a diff would actually be a reasonable approach as it shows what needed changing...

Now he has a program that compiles, only has one warning and doesn't achieve what he wants.  Writing a program that does what he wants for him won't teach him to program. 

Presumably the task is not as important as the learning experience...  He didn't ask us to write a program for him that does X, but instead said "I've done this and it doesn't work", that implies that he wants to learn, not just that he wants a program that does X for him.

Z.

---

### Post by Jessehk on 2008-02-18
> **Zwack said:**
>  Writing a program that does what he wants for him won't teach him to program. 

Z.

Who said anything about writing programs for him? I think we're misunderstanding each other.

---

### Post by PaulFr on 2008-02-18
From **[http://crca.ucsd.edu/~msp/techniques/latest/book-html/node11.html]("http://crca.ucsd.edu/%7Emsp/techniques/latest/book-html/node11.html")** I found the formula for conversion to a MIDI pitch from a frequency as > m = 69 + 12 x log( f / 440 ) where log is to the base 2. Is this what you are attempting to do?

If so, something like ```
#include <cmath>
#include <iostream>

template <int base, typename T> T mylog( T x )
{
    return std::log( x ) / std::log( base );
}

int main()
{
    double f;
    printf("What is f? ");
    std::cin >> f;

    double a = mylog <2> ( f / 440.0 );

    int p = 69 + 12 * a;

    std::cout << std::endl;
    std::cout << "The pitch for frequency " << f << " is " << p << std::endl;

    if (p == 69)
        std::cout << "The frequency is A4" << std::endl;
    else if (p > 69)
        std::cout << "The frequency is higher than A4" << std::endl;
    else // if (p < 69)
        std::cout << "The frequency is lower than A4" << std::endl;

    return 0;
}
```Some comments:
1. You need to use semi-colon ( ; )  to terminate statements.
2. I changed your printf statements to cout statements as it is **better** not to mix stdio input/output and iostreams input/output.
3. I changed the type of f and a to double so that the actual log value is returned from mylog. Try changing either or both of them to int back to see what happens. Try adding a cout statement to print out the value of **a** just after line 15.
4. I think you should review the basics of the language before you attempt such programs. Try out more example programs and understand what each line does.

Good luck !

---

### Post by pmasiar on 2008-02-18
> **Zwack said:**
> Stating that it doesn't work doesn't tell him anything he doesn't know....

Presumably the task is not as important as the learning experience...  .

Exactly. 

And Jessehk IMHO correctly suggests that for us to help OP efficiently we need to know what he wants to accomplish. **Pseudocode first**. So we can pinpoint not only missing semicolons, but deeper errors, so OP can learn more that just fixing syntax errors and beating code collected from various snippets from internet into submission.

---

### Post by Zwack on 2008-02-18
I agree that he needs to be able to articulate what he is trying to achieve...

I am afraid I still disagree with the negative approach...

Yes, he needs to understand what he is doing and why.  

For example, while the log template is a neat idea, I'm not sure that it's better for a beginner than using "log(x) / log(base)"

I get the feeling that we're all, fundamentally, in agreement here, we're just disagreeing on the actual approach.

Z.

---

### Post by WitchCraft on 2008-02-19
Hmmm... I'm woundering about the cr** i see here...

Here is a better example. How you should do it:
[PHP]
#include <iostream> // iostream always first!
#include <cmath>


template <class DataType>
int intFuncLog(const int& intBase, const DataType& dt_Number)
{
	return (int) ( ( (double) std::log(dt_Number) ) / ((double) std::log( intBase ))) ;
}



// Doing a template like this is very ugly!
template <int base, typename T>
T mylog( T x ) 
{
    return std::log( x ) / std::log( base );
}




/*  Equation:

	X                     = 69 + (440 * 2^(f/12))
	<==>
	(X-69)/440            = 2^(f/12)
	<==>
	log2((X-69)/440)      = f/12
	<==>
	(log2((X-69)/440))*12 = f
*/

// argc and argv are command line arguments
// they are REQUIRED by some compilers
// in some compilers, omitting them is a syntax error...
int main(int intArgc, char* chrptr_chrarry_argv[])
{
	int intFrequency;
	int intWhatever;

	printf("What is f? ");
	std::cin >> intFrequency;
	std::cout << "\n" ;
	
	// You can output it using the normal way, using the printf functions from C
	// intWhatever = intFuncLog(2,intFrequency/440.0);
	// printf("a = %d\n", intWhatever);
	
	// This can also be written as:
	// printf("a = %d\n",intWhatever = intFuncLog(2,intFrequency/440.0)); //

	// Or you can use the following 2 lines in C++
	intWhatever = intFuncLog(2, intFrequency / 440.0);
	std::cout << "a = " << intWhatever << "\n" ;
	// Which is equivalent to
	// intWhatever = (int) mylog <2> ( intFrequency / 440.0 );
	// std::cout << "a = " << intWhatever << std::endl;
	 
	// The following thing is NOT allowed in C++, thus causing a compile error
	// std::cout << "a = " << intWhatever = intFuncLog(2, intFrequency / 440.0) << "\n" ;


    int p = 69 + 12 * intWhatever;

    //std::cout << std::endl; // no, add \n to the beginning of the next line...
    std::cout << "\nThe pitch for frequency " << intFrequency << " is " << p << std::endl;

	if (p == 69)
		printf("The frequency is A440\n"); // No brackets if there is only one instructions
	if (p > 69)
	{ // Bracket NOT necessary
		printf("The frequency is higher than A4\n"); 
	} // Bracket NOT necessary
	if (p < 69)
	{ // Bracket NOT necessary
		printf("The frequency is lower than A4\n");
	} // Bracket NOT necessary
	// system("pause") ; // To see the result in Visual C++

	return EXIT_SUCCESS ; // NOT return 0 !
}
// And a new line at the end of the last instruction, or you get errors on some compilers...
[/PHP]

---

### Post by Jessehk on 2008-02-19
> **WitchCraft said:**
> Hmmm... I'm woundering about the cr** i see here...

Here is a better example. How you should do it:


I disagree with almost every piece of advice in that code.

-Hungarion notation (or something close to it)?
-Naming standard options like argc and argv differently?
-Suggesting that ommitting the argc and argv in the declaration of main is an error?
-Not checking the validity of user input?
-Using C-casts instead of static_cast<T>() (and what's the deal with all the unnecessary casting?)
-Suggesting the use of cstdio rather than iostream?
-Using repeated *if*'s rather then *else if* and *else*?
-Suggesting that *return*'ing 0 is incorrect and that the use of the EXIT_SUCCESS macro is required?

At best these are subjective changes and at worst, they are errors.

I would post something that I feel is correct (and I don't claim to be an expert in C++ -- I'm still learning too), but I have yet to see the OP make any effort to refine the problem (i.e. actually describe what the program is supposed to be **doing**.)

---

### Post by Zwack on 2008-02-20
Jessehk I think that you missed the truly excellent combination of ....

```

    printf("What is f? ");
    std::cin >> intFrequency;
    std::cout << "\n" ; 

```

Which is neither pure c, nor pure c++.  Note the combination of printf, cin and cout... and even the cout and "\n" rather than endl...  It's not even really explicable as being less typing.

EXIT_SUCCESS is better than return 0, as it will work even if someone produces an OS which uses other than 0 as the successful return code... But that's even less likely than someone changing the numbers associated with particular signals...

And some compilers do warn about a lack of return at the end of the file...  But I've never seen it as an Error.

Z.

---

### Post by Zwack on 2008-02-20
So, in the interests of learning...

What if anything would you change about the following program and why?

```

#include <iostream>
#include <cmath>

int
main (int argc, char **argv)
{
 
  // Set the namespace as I'm only using std and I 
  // don't want to type it all the time
  using namespace std;

  // Get the frequency from the user
  double f;
  cout << "What is the frequency?" << endl;
  cin >> f;
  
  // Calculate the MIDI note number
  double p = 69 + 12 * (log(f/440.0) / log(2));

  // Now display the results
  cout << endl << "The midi note " << p;

  if (p < 69) {
    cout << " is lower than A4." << endl;
  } else if (p == 69) {
    cout << " is the same as A4." << endl;
  } else { // if (p > 69) 
    cout << " is higher than A4." << endl;   
  }

  return EXIT_SUCCESS;
}


```

Thanks...

Z.

---

### Post by pedro_orange on 2008-02-20
Theres always room for improvement; but I'd say "if it ain't broke don't fix it", howver if you were so inclined:

Your 'using namespace std;' is only relevant within the context of int main() , so if you were to write functions to break this up it would be out of scope.

You do no checking on the input from the user. What if they input "\\]'.,"?

Could do some Try/Catches for error handling.

---

### Post by WitchCraft on 2008-02-21
Why checking the input if you only use the program yourself?
That's superfluous...

PS: Mixing of C and C++ is allowed. At least as long as you use C++ ;-)

And renaming standard parameters is not forbidden; just because they are standard parameters that does not mean you have to always use the standard names.

And typecasting is necessary, because some compilers don't like the ISO standard.

And hungarian notation is quite useful, but that's my personal opinion.
And i don't understand why other people are not using it or something close to it. It's simply easier to detect type errors/problems.

For example you see immediately that you run into problems with the log function as it was implemented... But who cares about accurate calculations, since 5 / 2 = 2 , well that's about correct, and the floating point arithmetic is an unreliable joke anyway, ain't it?

---

### Post by Jessehk on 2008-02-21
> **WitchCraft said:**
> Why checking the input if you only use the program yourself?
That's superfluous...


I disagree completely.

> 
PS: Mixing of C and C++ is allowed. At least as long as you use C++ ;-)


Yes, but you didn't even do it correctly.

> 
And renaming standard parameters is not forbidden; just because they are standard parameters that does not mean you have to always use the standard names.


You **can** rename them, but doing so is so unnecessary when so many C and C++ programmers are accustomed to the convention. It would be like naming the **self** parameter in Python to something else.

> And typecasting is necessary, because some compilers don't like the ISO standard.

I was taught to code to the standard, not to broken compilers.
You still didn't typecast properly using static_cast<T>.

> 
For example you see immediately that you run into problems with the log function as it was implemented... But who cares about accurate calculations, since 5 / 2 = 2 , well that's about correct, and the floating point arithmetic is an unreliable joke anyway, ain't it?

Fine, I'll give you that I didn't realize std::log dealt in double's rather than float's.

---

### Post by hod139 on 2008-02-21
> **WitchCraft said:**
> 
[php]
#include <iostream> // iostream always first!
#include <cmath>


template <class DataType>
int intFuncLog(const int& intBase, const DataType& dt_Number)
{
    return (int) ( ( (double) std::log(dt_Number) ) / ((double) std::log( intBase ))) ;
}
[/php]
This is not correct.  
1) You do not have to include iostream before cmath.
2) Why are you forcing FuncLog to return an int?
3) There is no reason to pass the int parameters as  const reference.  There is no performance or safety difference with passing intrinsic types by value or const reference
4) You are using c-style casts
5) You are casting the return of std::log to a double.  You don't need to do that (and it should have been cast to DataType not double), the return type of std::log will match the input type and casting could potentially lose precision.  
6) std::log only accepts float, double, or long double and returns the matching floating point type, so you do not need to worry about integer division with the return values.  Even though you think you are passing an int to std::log, it is automatically being converted to a float.  You really don't have to cast the return.
7) The function return type should match the input type.  Let the caller cast away precision from the return if they so desire.

> **WitchCraft said:**
> 
[php]
// Doing a template like this is very ugly!
template <int base, typename T>
T mylog( T x ) 
{
    return std::log( x ) / std::log( base );
}
[/php]How is ```
val = mylog<2>(100)
```uglier than ```
val = intFuncLog(2, 100)
```
> **WitchCraft said:**
> 
[php]
    printf("What is f? ");
    std::cin >> intFrequency;
    std::cout << "\n" ;
[/php]You should never advocate the use of printf in C++ code.  Printf is not type safe.  You should always use cout.


> **Jessehk said:**
> I
Fine, I'll give you that I didn't realize std::log dealt in double's rather than float's.

It works with float, double, and long double

---

### Post by hod139 on 2008-02-21
> **Zwack said:**
> So, in the interests of learning...

What if anything would you change about the following program and why?

```

#include <iostream>
#include <cmath>

int
main (int argc, char **argv)
{
 
  // Set the namespace as I'm only using std and I 
  // don't want to type it all the time
  using namespace std;

  // Get the frequency from the user
  double f;
  cout << "What is the frequency?" << endl;
  cin >> f;
  
  // Calculate the MIDI note number
  double p = 69 + 12 * (log(f/440.0) / log(2));

  // Now display the results
  cout << endl << "The midi note " << p;

  if (p < 69) {
    cout << " is lower than A4." << endl;
  } else if (p == 69) {
    cout << " is the same as A4." << endl;
  } else { // if (p > 69) 
    cout << " is higher than A4." << endl;   
  }

  return EXIT_SUCCESS;
}


```Thanks...

Z.

I would not use "using namespace std".  It pulls in the entire std namespace for 3 functions.  I would just prefix cout, endl, and log with std::.  If you really don't want to write the extra 5 chars (which really helps with readability since you know that you are not calling your own log function) you can always do
```

using std::cout;
using std::endl;
using std::log

```

---

### Post by Zwack on 2008-02-21
Thanks for both of the suggestions as to what could be improved.

As I say, it's a learning experience...    :-)

Z.

---

### Post by WitchCraft on 2008-02-21
> **Zwack said:**
> So, in the interests of learning...

What if anything would you change about the following program and why?

```

#include <iostream>
#include <cmath>

int
main (int argc, char **argv)
...

```

Thanks...

Z.

IMO, you should be careful if you write char **argv.
First, IMO, you should write char**  argv rather than char **argv, even if both is allowed.

Second, using char **argv implies the equivalence of  **argv with *argv[].
This is not the case. While it is all the same for read access, you will notice that with write-access, there is a difference between:
char* mystring  = "Hello World" ;
and
char mystring1[] = "Hello World" ;

because char* mystring <==>  const char*
while 
char mystring1[] <==> char[]

Now note that char* and char[] is a technical equivalent, because both are pointers, but note the bloody const. 
Writing to const. will result in, when not compile error, a runtime error, because of memory protection.

---

### Post by hod139 on 2008-02-21
> **WitchCraft said:**
> IMO, you should be careful if you write char **argv.
First, IMO, you should write char**  argv rather than char **argv, even if both is allowed.

Why?

> 
Second, using char **argv implies the equivalence of  **argv with *argv[].
This is not the case. 
Wrong.  They are equivalent. As a function parameter there is no difference.  If used as a value, or as a function parameter, an array is nothing more than a pointer to its first element. You can't pass arrays into functions.

> 
While it is all the same for read access, you will notice that with write-access, there is a difference between:
char* mystring  = "Hello World" ;
and
char mystring1[] = "Hello World" ;

because char* mystring <==>  const char*
while 
char mystring1[] <==> char[]

Now note that char* and char[] is a technical equivalent, because both are pointers, but note the bloody const. 
Writing to const. will result in, when not compile error, a runtime error, because of memory protection.I don't think you understand the difference.  See 
[http://www.c-faq.com/decl/strlitinit.html](http://www.c-faq.com/decl/strlitinit.html), or [http://ubuntuforums.org/showthread.php?t=357869](http://ubuntuforums.org/showthread.php?t=357869), or [http://ubuntuforums.org/showthread.php?t=696643](http://ubuntuforums.org/showthread.php?t=696643)

---

### Post by WitchCraft on 2008-02-22
> **hod139 said:**
> 
Why?


Because * is a pointer operator and a type declarator.
 

Imagine the following code (taken from Quake3):
```

void (*original_RE_RenderScene)(refdef_t*) ;

void modified_RE_RenderScene(refdef_t* fd)
{
	//if (urth_NoSniperZoom.integer)
	//{
		// Remove sniper zoom
	//	fd->fov_x = 90;
	//	fd->fov_y = 73.7398;
	//}
	//if( (fd->fov_x > 85) && (fd->fov_x < 110) )
	//{
		// relativity	
		//fd->fov_x = 150; 
	//	fd->fov_y = 90 ;		
	//}

	
	refdef = *fd;
	aimAt(vec3_playersHead[nearest]) ;
	original_RE_RenderScene(fd);
}

```

A thing to notice for newbies:
void (*original_RE_RenderScene)(refdef_t*) ;
is a declaration of a function pointer (which will be made point to the RE_RenderScene function);

Now notice the declaration of Re_RenderScene
void modified_RE_RenderScene(refdef_t* fd)
{...}

if you would write: 
void modified_RE_RenderScene(refdef_t *fd)
strictly (not to mention pedantic) seen, it implies * is the pointer operator and not the declaration operator, so...
strictly seen, this would result in a function pointer:
void (*original_RE_RenderScene)(refdef_t) ;

and that would be incorrect.
However it is of course allowed to write 
void modified_RE_RenderScene(refdef_t *fd)
{...}
because refdef_t* fd 
as well as
refdef_t * fd 
and
refdef_t *fd  
are (cough) 'equivalent'.

If you ever declare function pointers, if you declared refdef_t* fd you can just copy the original function and delete the variable name (fd in this case) to get the function pointer type, while with the * at fd, it implies * belongs to fd, and not refdef_t, and if you do such things many times you will miss the * sooner or later if you just copy and delete fd (because you will accidentially delete *), and you will then notice strange, hardly understandable compiler error messages...

Besides, it's easier that way to declare function pointers in an automated fashion, because you have a whitespace as separator in between, making it easier to get refdet_t* because you have a whitespace as split char.


> **hod139 said:**
> 
Wrong.  They are equivalent. As a function parameter there is no difference.  If used as a value, or as a function parameter, an array is nothing more than a pointer to its first element. You can't pass arrays into functions.

I don't think you understand the difference.  
See 
[http://www.c-faq.com/decl/strlitinit.html](http://www.c-faq.com/decl/strlitinit.html), or [http://ubuntuforums.org/showthread.php?t=357869](http://ubuntuforums.org/showthread.php?t=357869), or [http://ubuntuforums.org/showthread.php?t=696643](http://ubuntuforums.org/showthread.php?t=696643)


No, I think I understand that perfectly, you just misunderstood what I wanted to say. An array is always a pointer pointing to the address of the first array object.
The relevant question is: is it a pointer to a constant object (in read-only memory), or is it a pointer to a nonconstant object (in read-write memory).

But anyway, argc and argv are bad examples for that, because first of all, you probably never need to write on them, and second it depends on how their data is initialized in memory by the operating system (because argc and argv come 'right' from the command line interpreter).


Well, to clarify what I wanted to say,  let's examplify it, to be sure that there is no missunderstanding:

consider this program:
```

#include <iostream>

void StrTolower(char chrarr_MyString[])
{
	char* chrptr_MyString = chrarr_MyString ;
	for(; *chrptr_MyString != '\0'; chrptr_MyString++)
		*chrptr_MyString = tolower(*chrptr_MyString);
}

int main()
{
	char chrarr_MyString[] = "Hello World" ;
	StrTolower(chrarr_MyString);
	printf("MyString = %s\n", chrarr_MyString) ;
	system("pause");
	return EXIT_SUCCESS ;
}

```

This works flawlessly.

and now consider this example:
```

#include <iostream>

void StrTolower(char* chrarr_MyString)
{
	char* chrptr_MyString = chrarr_MyString ;
	for(; *chrptr_MyString != '\0'; chrptr_MyString++)
		*chrptr_MyString = tolower(*chrptr_MyString);
}

int main()
{
	char chrarr_MyString[] = "Hello World" ;
	StrTolower(chrarr_MyString);
	printf("MyString = %s\n", chrarr_MyString) ;
	system("pause");
	return EXIT_SUCCESS ;
}


```

This also works correctly, because char* and char[] are, as said, technically equivalent (=pointer to the first object).

The problem with:
void StrTolower(char* chrarr_MyString)
is, it implies chrarr_MyString has been initialized as char* and not as char chrarr_MyString[].

If that would be the case, the program would look like this:
```

#include <iostream>

void StrTolower(char* chrarr_MyString)
{
	char* chrptr_MyString = chrarr_MyString ;
	for(; *chrptr_MyString != '\0'; chrptr_MyString++)
		*chrptr_MyString = tolower(*chrptr_MyString);
}

int main()
{
	char* chrarr_MyString = "Hello World" ;
	StrTolower(chrarr_MyString);
	printf("MyString = %s\n", chrarr_MyString) ;
	system("pause");
	return EXIT_SUCCESS ;
}

```

This would result in a segault/runtime error 

> **Microsoft said:**
> 
Unhandled exception at 0x00411b44 in Lowercasetest.exe: 0xC0000005: Access violation writing location 0x004260d4.


Now if you write char* instead of char[], that's not so very bad, because, as said, they are equivalent, and implying read only to read-write will not result in any damage.
The problem is the opposite: 
if you have declared StrTolower this way:
void StrTolower(char chrarr_MyString[])
this implies  chrarr_MyString has been declared as array ([]) instead of a pointer (*), which implies read/WRITE access, while there is ONLY read access...

Got my point now?
It's a little bit something like an error in Hungarian notation, where char[] becomes const char[].
However, that's not yet that bad, because the data will remain char, and not become const...
But the opposite error is bad:
It's a little bit something like an error in Hungarian notation, where const char[] becomes char[].
And this results in segmentation faults or runtime errors...

---

### Post by hod139 on 2008-02-22
> **WitchCraft said:**
> 
No, I think I understand that perfectly, you didn't understand. An array is always a pointer pointing to the address of the first array object.
The relevant question is: is it a pointer to a constant object (in read-only memory), or is it a pointer to a nonconstant object (in read-write memory).
This statement illustrates that you really don't understand. See: 
[http://c-faq.com/aryptr/aryptrequiv.html](http://c-faq.com/aryptr/aryptrequiv.html)
and 
[http://c-faq.com/aryptr/aryvsadr.html](http://c-faq.com/aryptr/aryvsadr.html)

Section 8.3.4 of the C++ standard defines what an array is.  Section 4.2 describes conversions  affecting lvalues of array type

From the C++ standard (section 4.2):
> 
  4.2 Array-to-pointer conversion                                                                 [conv.array]
1    An lvalue or rvalue of type “array of N T” or “array of unknown bound of T” can be converted to an rvalue of type “pointer to T.” The result is a pointer to the first element of the array.

2    A string literal (2.13.4) that is not a wide string literal can be converted to an rvalue of type “pointer to char”; a wide string literal can be converted to an rvalue of type “pointer to wchar_t”. In either case, the result is a pointer to the first element of the array. This conversion is considered only when there is an explicit appropriate pointer target type, and not when there is a general need to convert from an lvalue to an rvalue. [Note: this conversion is deprecated. See Annex D. ] For the purpose of ranking in overload resolution (13.3.3.1.1), this conversion is considered an array-to-pointer conversion followed by a qualification conversion (4.4). [Example: "abc" is converted to “pointer to const char” as an array-to-pointer conversion, and then to “pointer to char” as a qualification conversion. ]



---

### Post by WitchCraft on 2008-02-23
> 
See: 
[http://c-faq.com/aryptr/aryptrequiv.html](http://c-faq.com/aryptr/aryptrequiv.html)
and 
[http://c-faq.com/aryptr/aryvsadr.html](http://c-faq.com/aryptr/aryvsadr.html)


Gobbledygook with no recognizable value whatsoever. 
If you have a point to make, then make it.

Should you mean that there are rvalue and lvalue issues, so you can't call them 'equivalent', yes that's true.
But that's rather due to illogical C grammar than to arrays and pointers not beeing equivalent.

I mean sometimes, the rvalue lvalue is just plain ridiculous, e.g. what sense does it make to implicitly declare a string as constant? 
That's just plain stupidity by the person who implemented C, rather than something else.

---

