---
title: "Help  me with C++ anyone?"
date: 2007-12-30
forum: Programming Talk
---

### Post by kool_kat_os on 2007-12-30
I just wrote this and I am new at c++:

[HTML]// Temprature Converter

#include <iostream>
using namespace std;

#define NEWLINE '\n'

int main ()
{
int temp1;
cout << "Please select a conversion: ";
cout << NEWLINE;
cout << "1 for F to C";
cout << NEWLINE;
cout << "2 for C to F";
cin >> temp1;

if (temp1 == 1); 
  int temp;
  cout << "Please enter temprature that you would like to convert: ";
  cin >> temp;
  cout << "The value you entered is " << temp << " degrees fahrenheit";
  cout << NEWLINE;
  cout << "The temprature is in celcius is " << (temp-32)*5/9 << " degrees";
  cout << NEWLINE;
  system ("PAUSE");
  return 0;

if (temp1 == 2);
  int temp2;
  cout << "Please enter temprature that you would like to convert: ";
  cin >> temp2;
  cout << "The value you entered is " << temp2 << " degrees celcius";
  cout << NEWLINE;
  cout << "The temprature is in fahrenheit is " << temp2*9/5+32 << " degrees";
  cout << NEWLINE;
  system ("PAUSE");
  return 0;
}


[/HTML]

I know I screwed up bad in here , can someone help me fix it? Thanks

---

### Post by thornmastr on 2007-12-30
What happens when you run the program?

What compiler are you using? Have you run it under the control of a debugger?

In short, what's wrong with it? 

I don't think anyone here will do your homework for you although all of us would probably help you solve "specific" and clearly "documented" problems.

Robert

---

### Post by kool_kat_os on 2007-12-30
When I press 2 it still goes to option 1

---

### Post by johnl on 2007-12-30
The problem is with the syntax of your if statement.

A proper if statement looks like this:
```

if (condition)
    do something;

```
OR

```

if (condition)
{
   do something;
   do something else;
}

```

What you've written is:

```

if (condition);
do something;

```
Where what you want to do is not associated with the if statement -- it's an empty if statement (as indicated by the semi colon).

---

### Post by kool_kat_os on 2007-12-30
This is what I changed it to:

[HTML]// Temprature Converter

#include <iostream>
using namespace std;

#define NEWLINE '\n'

int main ()
{
int temp1;
cout << "Please select a conversion: ";
cout << NEWLINE;
cout << "1 for F to C";
cout << NEWLINE;
cout << "2 for C to F";
cin >> temp1;

if (1); 
  int temp;
  cout << "Please enter temprature that you would like to convert: ";
  cin >> temp;
  cout << "The value you entered is " << temp << " degrees fahrenheit";
  cout << NEWLINE;
  cout << "The temprature is in celcius is " << (temp-32)*5/9 << " degrees";
  cout << NEWLINE;
  system ("PAUSE");
  return 0;

if (2);
  int temp2;
  cout << "Please enter temprature that you would like to convert: ";
  cin >> temp2;
  cout << "The value you entered is " << temp2 << " degrees celcius";
  cout << NEWLINE;
  cout << "The temprature is in fahrenheit is " << temp2*9/5+32 << " degrees";
  cout << NEWLINE;
  system ("PAUSE");
  return 0;
}
[/HTML]

Still same problem

---

### Post by CptPicard on 2007-12-30
Your if blocks are empty. You need to use braces to include whatever is supposed to be inside the if. Like...

```

if (something) {
    do stuff;
    do more stuff;
}

```

And you do not need to "#define NEWLINE", use "endl" from the namespace std... like 

```

cout << "Hello world!" << endl;

```

EDIT: I really, really suggest you read up on basic syntax first... your ifs are completely hosed. A C++ block is delimited by {   }. And the contents of the conditions are wrong too, both 1 and 2 are just simply "true" in C++. You need to compare something... if (var == 1) { dothings; }

---

### Post by kool_kat_os on 2007-12-30
Now it says that there is a problem in it.

[HTML]// Temprature Converter

#include <iostream>
using namespace std;

#define NEWLINE '\n'

int main ()
{
int temp1;
cout << "Please select a conversion: ";
cout << NEWLINE;
cout << "1 for F to C";
cout << NEWLINE;
cout << "2 for C to F";
cin >> temp1;
}
    
    if (temp1 == 1) { 
       int temp;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees fahrenheit";
       cout << NEWLINE;
       cout << "The temprature is in celcius is " << (temp-32)*5/9 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
    
    if (temp1 == 2) { 
       int temp2;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp2;
       cout << "The value you entered is " << temp2 << " degrees celcius";
       cout << NEWLINE;
       cout << "The temprature is in fahrenheit is " << temp2*9/5+32 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
[/HTML]

---

### Post by Majorix on 2007-12-30
Could you please paste the code in [php] tags? Your code looks disturbing in those tags.

Also you should consider pasting the error output too, instead of just saying "this code produces errors", as we are no geniuses who can see errors at first sight.

Sorry if I sound rude, but I have seen you around often enough and thought you would have known about the php tags by now, also I have asked numerous people that they post the error output.

---

### Post by kool_kat_os on 2007-12-30
Sorry, i forgot...

[PHP]using namespace std;

#define NEWLINE '\n'

int main ()
{
int temp1;
cout << "Please select a conversion: ";
cout << NEWLINE;
cout << "1 for F to C";
cout << NEWLINE;
cout << "2 for C to F";
cin >> temp1;
}
    
    if (temp1 == 1) { 
       int temp;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees fahrenheit";
       cout << NEWLINE;
       cout << "The temprature is in celcius is " << (temp-32)*5/9 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
    
    if (temp1 == 2) { 
       int temp2;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp2;
       cout << "The value you entered is " << temp2 << " degrees celcius";
       cout << NEWLINE;
       cout << "The temprature is in fahrenheit is " << temp2*9/5+32 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}[/PHP]
Here are the errors:

expected unqualified-id before "if"
expected `,'or`;' before "if"

---

### Post by CptPicard on 2007-12-30
Uh, you do not need fancy syntax coloring or compiler barf to see that the if blocks are actually *outside the main function*... :)

Try, uh, writing them inside it? C++ is not like Python where you can just delimit by indentation. You use {   }  to tell where a block begins and ends. Your main() ends before your ifs, which are completely outside of... well.. anything that is legitimate C++.

---

### Post by Majorix on 2007-12-30
Your if's are outside of main(). Outside of main there can only be global vars and functions.

[php]using namespace std;

#define NEWLINE '\n'

int main ()
{
int temp1;
cout << "Please select a conversion: ";
cout << NEWLINE;
cout << "1 for F to C";
cout << NEWLINE;
cout << "2 for C to F";
cin >> temp1;
if (temp1 == 1) { 
       int temp;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees fahrenheit";
       cout << NEWLINE;
       cout << "The temprature is in celcius is " << (temp-32)*5/9 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
    
else if (temp1 == 2) { 
       int temp2;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp2;
       cout << "The value you entered is " << temp2 << " degrees celcius";
       cout << NEWLINE;
       cout << "The temprature is in fahrenheit is " << temp2*9/5+32 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
} [/php]

I have added an else at the start of second if so that it doesn't get executed after the first if no matter what.

I also arranged the places of the {}'s so the if's are exec'ed.

Hope it helps.

---

### Post by kool_kat_os on 2007-12-30
ok

---

### Post by xtacocorex on 2007-12-30
For starters, take out the system ("PAUSE");  You don't need them.

Your program stucture should be like:
```

#include <includes>

int main()
{
    // CODE HERE

    return 0;
}

```
Before you start your if statements, you close your main function with a }, remove that.

Also, make your if's an if..elseif
```

    if (temp1 == 1)
    {
        // CODE HERE
    }
    elseif (temp1 == 2)
    {
        // CODE HERE
    }
    else
    {
        std::cout << "INCORRECT OPTION" << std::endl;
        exit(1);
    }

```

---

### Post by Majorix on 2007-12-30
> **CptPicard said:**
> Uh, you do not need fancy syntax coloring or compiler barf to see that the if blocks are actually *outside the main function*... :)

I usually don't even look at unreadable codes :)

---

### Post by Majorix on 2007-12-30
> **xtacocorex said:**
> Also, make your if's an if..elseif

You mean "if-else if" right? Because there is no elseif or elif or whatever in C++ :)

---

### Post by CptPicard on 2007-12-30
Is "elseif" without space legitimate? I don't think so?

And just to nitpick, the else is redundant, because if temp was 1, it can't be 2. :) You're saving one test. Not sure which one is simpler for a beginner to understand...

---

### Post by jespdj on 2007-12-30
> **xtacocorex said:**
> 
Also, make your if's an if..elseif
```

    if (temp1 == 1)
    {
        // CODE HERE
    }
    elseif (temp1 == 2)
    {
        // CODE HERE
    }

```
No, there is no "elseif" keyword in C++. You need to put a space between "else" and "if".
```
if (...)
{
  // CODE HERE
}
else if (...)
{
  // CODE HERE
}
```

---

### Post by kool_kat_os on 2007-12-30
I did this :

[PHP]using namespace std;

#define NEWLINE '\n'

int main ()
{
int temp1;
cout << "Please select a conversion: ";
cout << NEWLINE;
cout << "1 for F to C";
cout << NEWLINE;
cout << "2 for C to F";
cin >> temp1;
if (temp1 == 1)  
{  
       int temp;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees fahrenheit";
       cout << NEWLINE;
       cout << "The temprature is in celcius is " << (temp-32)*5/9 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
    
else if (temp1 == 2)  
{     
       int temp2;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp2;
       cout << "The value you entered is " << temp2 << " degrees celcius";
       cout << NEWLINE;
       cout << "The temprature is in fahrenheit is " << temp2*9/5+32 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
}  
[/PHP]

I got these errors:
 
Line 8 `cout' undeclared (first use this function)
Line 13`cin' undeclared (first use this function)  
Line 23`system' undeclared (first use this function)

---

### Post by Wybiral on 2007-12-30
> **CptPicard said:**
> Uh, you do not need fancy syntax coloring or compiler barf to see that the if blocks are actually *outside the main function*... :)

lol, "compiler barf", well said.

---

### Post by Lacrimstein on 2007-12-30
Hmmm, seems like you're missing #include <iostream>

---

### Post by CptPicard on 2007-12-30
You're missing headers. #include <iostream> and then #include whatever gives that "system" call, which you don't need.

And seriously, drop the #define NEWLINE, and move to "endl" because you already have iostream and namespace std :)

---

### Post by Majorix on 2007-12-30
You have to include the headers. At the very beginning of the code, paste these:
[php]#include <iostream>
#include <cstdlib>[/php]

---

### Post by kool_kat_os on 2007-12-30
Thanks for your help everybody. It works now.

---

### Post by kool_kat_os on 2007-12-30
it worked without the 
[HTML]#include <cstdlib> [/HTML]
do I still need to put it?

---

### Post by bobbocanfly on 2007-12-30
you need to include the libraries containing the functions you are getting undefined errors with.

I dont know C++ but im guessings it will be something like this

```
#include <iostream>
```

---

### Post by Majorix on 2007-12-30
> **kool_kat_os said:**
> it worked without the 
[HTML]#include <cstdlib> [/HTML]
do I still need to put it?

No I only wrote it so that you could do the System call. Also, the proper way to include the standard library is like #include <stdlib.h>.

---

### Post by CptPicard on 2007-12-30
<snip/> whoops, no you don't. :)

---

### Post by Majorix on 2007-12-30
EDIT: Lol.

---

### Post by kool_kat_os on 2007-12-30
> No I only wrote it so that you could do the System call. Also, the proper way to include the standard library is like #include <stdlib.h>.

huh.. Is it better to include?:

[HTML]#include <stdlib.h>[/HTML]

---

### Post by Majorix on 2007-12-30
You have to include it if you keep the System call.

Otherwise you don't.

And I was doing a correction, it's not called #include <cstdlib>, but #include <stdlib.h>.

---

### Post by rye_ on 2007-12-30
firstly, I admire your attempt at learning c++, this is something I started a couple of years ago.

But I would advise you first take a course in straight c, in order to learn about function spaces, headers, makefiles etc.  The problem with learning C++ before C is that you tend to get used to using the quick fix c++ solutions which bypass elements of the base language.

For instance, C++ loves its string library and hates pointers.
I on the other hand found c++ strings infuriating when doing complex tasks and pointers as a very clever way of getting things done.

just my 2 cents, best of luck.

p.s. a good C book is the original " A book on C", by kernighan and ritchie.

Ryan

---

### Post by rye_ on 2007-12-30
some of the previous posters have debated the aptness of using 
cstdlib and stdlib.h.  They are the same thing; cstdlib is the pc way of calling stdlib.h from within c++.

the same goes with cstring and string.h, both of which call a c library.

Ryan

---

### Post by Majorix on 2007-12-30
> **rye_ said:**
> But I would advise you first take a course in straight c

And I would actually advise sticking with it. C is the original, and C++ is the sequel. And you know the story with sequels.

But let's don't turn this into another "C or C++?" thread :)

---

### Post by kool_kat_os on 2007-12-30
What do you mean my "system call"?

---

### Post by rye_ on 2007-12-30
> **Majorix said:**
> And I would actually advise sticking with it. C is the original, and C++ is the sequel. And you know the story with sequels.

But let's don't turn this into another "C or C++?" thread :)

Not quite.  C++ is the C language in its entirety, to program in c is to program in c++.  C++ introduction of OOP, polymorphism etc is a wonderful additiob when required.  But on the otherhand such features can be wholly unnecessary and if you don't understand the advantages of the C++ feature you are using, then goodluck.

for instance, std.cin is a fairly blackbox command, which stores a buffer of input, which must be explicitly deleted, otherwise bugs arise.
when in its stead gets, scanf, fgets etc could be used with no such buffer.

---

### Post by Majorix on 2007-12-30
system("PAUSE") line.

---

### Post by kool_kat_os on 2007-12-30
Ok,

---

### Post by Majorix on 2007-12-30
I thought in order to use a system call you had to include the standard library. But if you don't then it's fine.

If it doesn't produce any errors and gives out the expected results then congrats :)

---

### Post by kool_kat_os on 2007-12-30
Ok, Does this look alright?

[PHP]//Temprature Conversion Program
using namespace std;
#include <iostream>
#define NEWLINE '\n'
int main ()
{
int temp;
cout << "Welcome to the Temprature Conversion Program";
cout << NEWLINE;
cout << "Please select a conversion: ";
cout << NEWLINE;
cout << "Press 1 for F to C";
cout << NEWLINE;
cout << "Press 2 for C to F";
cout << NEWLINE;
cout << "> ";
cin >> temp;
if (temp == 1)  
{  
       int temp;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees fahrenheit";
       cout << NEWLINE;
       cout << "The temprature is in celcius is " << (temp-32)*5/9 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
if (temp == 2)  
{     
       int temp;
       cout << "Please enter temprature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees celcius";
       cout << NEWLINE;
       cout << "The temprature is in fahrenheit is " << temp*9/5+32 << " degrees";
       cout << NEWLINE;
       system ("PAUSE");
       return 0;
}
}
  
[/PHP]

---

### Post by Majorix on 2007-12-30
Your if's should be in the form if-else if-else. Otherwise you will get unexpected results.

Also, don't use the NEWLINE global in other programs.

And finally, you could just as well remove system("PAUSE") as it does pretty much nothing.

---

### Post by kool_kat_os on 2007-12-30
the "if" thing works fine and if I dont have the PAUSE thing the program exits automatcally:-)

---

### Post by CptPicard on 2007-12-30
> **rye_ said:**
> Not quite.  C++ is the C language in its entirety, to program in c is to program in c++. 

I would have to take issue with this view... proper idiomatic C++ has a fairly different style of doing things, and the differences from C are enough that someone who makes it a point to learn C first and then C++ is going to end up a bit confused, and will probably start writing C-ish C++, which is not a good thing.

I don't really see why it would be a bad thing that C++ gives you higher-level constructs to work with, in particular stuff like safe strings. C++ can be used as a learner language too, by starting with the C-like basics (you do start with control flow etc in all languages anyway), without actually doing C and thus being tripped  by the differences when they do arise. You do get pointers etc when neccessary, but the whole point is that you should pretty much avoid raw pointers when you can, and C puts you in the mindset of playing with pointers all the time.

C++ works much better as a teacher towards C if and when required (if ever), than the other way around. The only difference is probably that C makes your interfacing with memory, be it on stack or on the heap, more explicit and perhaps easier to understand. But... an absolute beginner should start with a more higher-level language anyway, and that would mean neither C or C++. Once you are ready, absorbing pointers and references from C++ is not going to be too difficult.

This is really a case in point... it would perhaps be more beneficial to spend more time in a HLL like Python if one is going to stick ifs outside of main... no offense ;)

---

### Post by rye_ on 2007-12-30
kool_cat_os, I've added below one of the infinite number of solution to the problem your program solves.  just though you might like to see that a switch-case construct looks like.
note: interestingly for you, a switch-case logic operator can handle char comparisons, so your initial user input could be a char insead of an int.

As an aside, I wasn't suggesting that one should use c instead of c++, indeed the philosophies of the two laanguages are wholly different.  But to I just personally feel ignoring c leads to quite often a poor understanding of c++.

insofar as the suggestion of learning a very high level language goes, I certainly think this is a good idea.  It was only after learning ruby that I began to get my head around OOP.

//Temperature Conversion Program
using namespace std;
#include <iostream>
int main (){

/* 
	user interaction via console
*/

cout << "Welcome to the Temprature Conversion Program\n";
cout << "Please select a conversion: ";
cout << "Press 1 for F to C\n";
cout << "Press 2 for C to F\n";
cout << "> ";

/*
	take user input
*/

int temp1;
cin >> temp1;

/*
	take further user input
*/

cout << "Please enter temprature that you would like to convert: ";
int temp;
cin >> temp;

/*
	process input
*/

switch (temp1){
case 1:
       
       cout << "The value you entered is " << temp << " degrees fahrenheit\n";
       cout << "The temperature is in celcius is " << (temp-32)*5/9 << " degrees\n";
       break;
case 2:
       
       cout << "The value you entered is " << temp << " degrees celcius\n";
       cout << "The temperature is in fahrenheit is " << temp*9/5+32 << " degrees\n";
       break;
}

/* 
exit procedure
*/

return 0;

}

---

### Post by Majorix on 2007-12-30
> **kool_kat_os said:**
> the "if" thing works fine and if I dont have the PAUSE thing the program exits automatcally:-)

Of course the if would work, because you use the return statements in them, so after executing one of them, the system exits. But it's not good practice and can and will cause problems in the future.

And instead of the system("PAUSE") thingies you can use a cin, like this:
[php]//... As last statement, before exiting the program
string foo;
cin >> foo;[/php]

---

### Post by kool_kat_os on 2007-12-30
huhhh.....

How?:confused:

---

### Post by Majorix on 2007-12-30
1. You define a string called "foo".
2. You read a value into it from the terminal. It waits until an input occurs. What you input at this point into the variable foo is not important, but the point is that the program will wait for you to act and will not close until you say so.

---

### Post by rye_ on 2007-12-30
I think it may be our old friend the c++ std.cin buffer causing problems with using cin to halt the program at the end.

Case point.

---

### Post by Majorix on 2007-12-30
I don't think he tried cin already.

---

### Post by angryfirelord on 2007-12-30
A couple issues that I've noticed.

First, there's no need to use NEWLINE. Just use *endl* instead:
```
cout << "Welcome to the Temprature Conversion Program"<<endl;
```
It looks a lot better too.

Second, you do not need to declare the same variable three times. Once is sufficient. 

Finally, you only need to put *return 0* at the end of main. Only under certain circumstances will you have to put it somewhere else, but for now declare it once.

& as a tip, indent your code. It looks a lot nicer.

Here it is, all cleaned up:
```
//Temperature Conversion Program, modified
#include <iostream>
using namespace std;

int main ()
{
	int temp;
	cout << "Welcome to the Temperature Conversion Program"<<endl;
	cout << "Please select a conversion: "<<endl;
	cout << "Press 1 for F to C"<<endl;
	cout << "Press 2 for C to F"<<endl;
	cout << "> ";
	cin >> temp;
if (temp == 1)  
	{  
       cout << "Please enter temperature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees fahrenheit"<<endl;
       cout << "The temperature is in celsius is " << ((temp-32)*5/9) << " degrees"<<endl;
	}
if (temp == 2)  
	{     
       cout << "Please enter temperature that you would like to convert: ";
       cin >> temp;
       cout << "The value you entered is " << temp << " degrees celsius"<<endl;
       cout << "The temperature in fahrenheit is " << (temp*(9/5)+32) << " degrees"<<endl;
	}
return 0;
}

```

---

### Post by CptPicard on 2007-12-30
Indentation style in the above is inconsistent... I would do (using my preferred K&R style, but YMMV...)

[php]

//Temperature Conversion Program, modified
#include <iostream>
using namespace std;

int main () {

	int temp;
	cout << "Welcome to the Temperature Conversion Program"<<endl;
	cout << "Please select a conversion: "<<endl;
	cout << "Press 1 for F to C"<<endl;
	cout << "Press 2 for C to F"<<endl;
	cout << "> ";
	cin >> temp;

	if (temp == 1) {  
		cout << "Please enter temperature that you would like to convert: ";
		cin >> temp;
		cout << "The value you entered is " << temp << " degrees fahrenheit"<<endl;
		cout << "The temperature is in celsius is " << ((temp-32)*5/9) << " degrees"<<endl;
	}

	if (temp == 2) {
		cout << "Please enter temperature that you would like to convert: ";
		cin >> temp;
		cout << "The value you entered is " << temp << " degrees celsius"<<endl;
		cout << "The temperature in fahrenheit is " << (temp*(9/5)+32) << " degrees"<<endl;
	}

	return 0;
}


[/php]

---

### Post by xtacocorex on 2007-12-30
> **Majorix said:**
> You mean "if-else if" right? Because there is no elseif or elif or whatever in C++ :)
So I mistyped, I had been messing with C++ code all morning and my brain was shot when I answered the OP's question.

---

### Post by amingv on 2007-12-31
> **Majorix said:**
> Of course the if would work, because you use the return statements in them, so after executing one of them, the system exits. But it's not good practice and can and will cause problems in the future.

And instead of the system("PAUSE") thingies you can use a cin, like this:
[php]//... As last statement, before exiting the program
string foo;
cin >> foo;[/php]

At the risk of confusing the OP more than he is, I would rather suggest to use 'cin.get()' instead. I saves you from declaring a new variable and I feel it's more appropriate. Here's how to use it:

[PHP]#include <iostream>

using namespace std;

int main(){
    cout<<"Press ENTER to continue..." <<endl; //Of course, you don't need this prompt
    cin.get(); //This will hold the program until enter is hit
}[/PHP]

Not to say the cin>> method won't work. I just like this better.

@OP: Try not to get accustomed to using system calls (system()) unless it's truly necessary, just a suggestion.

---

### Post by LaRoza on 2007-12-31
> **amingv said:**
> 
@OP: Try not to get accustomed to using system calls (system()) unless it's truly necessary, just a suggestion.

Might as well confuse the OP even more...

system() is not a system call. [http://en.wikipedia.org/wiki/System_call](http://en.wikipedia.org/wiki/System_call)

---

### Post by rye_ on 2008-01-01
try something like following, of course altering it accordingly to make it more c++ than c in terms of the functions used.

int main (int argc, char * argv[]){

/*
Your Program 
*/ 

/*
Termination of program
*/

while ( getc(stdin) != '\n') {} // clear any keyboard input not utilised
printf("Press enter to exit the program\n"); // message to stdio
getc(stdin);

return 0;

}

---

