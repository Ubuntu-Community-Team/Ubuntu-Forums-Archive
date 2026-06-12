---
title: "C++ question"
date: 2009-07-17
forum: Programming Talk
---

### Post by C++buntu on 2009-07-17
Hi everyone,

I'm trying to resolve this weird error C2466 on Visual C++ Studio 2008...(yeah, i know...it's a windows IDE). 

```

#include <iostream>
#include <fstream>
#include <cstdlib>
#include <ctime>
#include "ex01ch11file3.h" // include Vector class

signed int main(void)
{
	// Using directives
	using std::cout;
	using std::cin;
	using std::endl;

	// Seed the random-number generator
	srand(time(0));

	// Initializing Vector objects
	VECTOR::Vector vStep(0.0, 0.0);
	VECTOR::Vector vResult(0.0, 0.0);
	
	// Initializing variables
	double dStep = 0.0;			// step length
	double dDirection = 0.0;	// angle
	
	// Number of steps
	unsigned int ulSteps = 0L;

	// Prompt user for number of trials
	cout << "Enter the desired number of trials: ";
	unsigned int uiTrial = 0u; cin >> uiTrial;

        // error C2466 is here, can't allocate a 0 length array
	==> unsigned long int ulResult[uiTrial]; <==
	
	// Prompt user for maximum distance
	cout << "Enter target distance (q to quit): ";
	double dTarget = 0.0; cin >> dTarget;

	// Prompt user for the step length
	cout << "Enter step length: ";
	unsigned long int ulSteps = 0L; 

	while(!(cin >> dStep))
	{
		cout << "Please enter a valid step length: ";
	}
		
	// Display results on-screen
	cout << "Target distance: " << dTarget << ", Step size: " << dStep << endl;

	// Loop processing
	for (unsigned int uii = 0; uii < uiTrial; ++uii)
	{
			//fout << "Target distance: " << dTarget << ", Step size: " << dStep << endl;
			while (vResult.MagnitudeValue() < dTarget)
			{
				cout << ulSteps << ": " << vResult << endl;

				//fout << ulSteps << ": " << vResult << endl;
				dDirection = rand() % 360;		// 0 <= dDirection < 360
				vStep.Set(dStep, dDirection, 'p');
				vResult = vResult + vStep;
				ulSteps++;
			}
			
			ulResult[uii] = ulSteps;
			cout << "After " << ulSteps << " steps, the subject has the following location:\n";
			cout << vResult << endl;
			vResult.Polar2DMode();
			cout << " or\n" << vResult << endl;
			cout << "Average outward distance per step = " << vResult.MagnitudeValue()/ulSteps << endl;

// 			fout << "After " << ulSteps << " steps, the subject has the following location:\n";
// 			fout << vResult << endl;
// 			vResult.Polar2DMode();
// 			fout << "or\n" << vResult << endl;
// 			fout << "Average outward distance per step = " << vResult.MagnitudeValue()/ulSteps << endl << endl;

			ulSteps = 0L;
			vResult.Set(0.0, 0.0);
			//cout << "Enter target distance (q to quit): ";
	}

	cout << "Bye!\n";

	//fout.close();

	return 0;
}
```

How can i resolve this problem? I think i can use a new statement to dynamically allocate the array, but i want to know if there is another way around.

error C2466: cannot allocate an array of constant size 0...

Any suggestions?

C++buntu

---

### Post by JordyD on 2009-07-17
Might help if you posted the error as well.

**EDIT:** Never mind, I see you've now added it.

---

### Post by typedef on 2009-07-17
Yes, dynamically allocating the array will fix your problem. You should not try to allocate an array on the stack with a non-constant identifier as you are trying to do with your initialization to zero then cin. Of course you could always use a container class from the STL if you don't want to deal with explicit array management, but that's another thing.

---

### Post by c0mput3r_n3rD on 2009-07-18
What's wrong with just saying 
```

using namespace std;

```and 
```

#include <vector>

```
?

---

### Post by C++buntu on 2009-07-18
Well, it's just that in my readings, i have not encountered the vector class yet, so i don't use it in the practice problems ;).

Thanks for your reply.

---

### Post by c0mput3r_n3rD on 2009-07-18
> **C++buntu said:**
> Well, it's just that in my readings, i have not encountered the vector class yet, so i don't use it in the practice problems ;).

Thanks for your reply.

And why not using namespace std;   I'm just curious.  I don't get why not to put it in.  Makes it easier to read and a lot less typing

---

### Post by c0mput3r_n3rD on 2009-07-18
```

    using std::cout;
    using std::cin;
    using std::endl;

```

Instead of just:
```

using namespace std;

```Which is just good programmingstyle.

And the vector header too? Why do you make it harder for yourself?

---

### Post by lisati on 2009-07-18
Some kind of sanity check when accepting user input is often a good idea.

---

### Post by C++buntu on 2009-07-18
because when you add using namespace std; you effectively import all the names in std; so it's not a "good" way to program, just import what you need like using std::cin, using std::cout and the like.

---

### Post by C++buntu on 2009-07-18
> **c0mput3r_n3rD said:**
> ```

    using std::cout;
    using std::cin;
    using std::endl;

```

Instead of just:
```

using namespace std;

```Which is just good programmingstyle.

And the vector header too? Why do you make it harder for yourself?

Sorry for the misleading #include "ex07ch11file3.h"...i've defined my own vector class, not the one in STL.

---

### Post by c0mput3r_n3rD on 2009-07-18
Ok I guess you give that stretch, I'll accept that, but what about the vector header file? 

-Aren't we in the times of quad core processors and multi GB's of memory and terabyte HDD? What does it matter too much if you get a few extra std's?

---

### Post by lisati on 2009-07-18
> **c0mput3r_n3rD said:**
> Ok I guess you give that stretch, I'll accept that, but what about the vector header file? 

-Aren't we in the times of quad core processors and multi GB's of memory and terabyte HDD? What does it matter too much if you get a few extra std's?
Readbiility, together with clean and efficient code.

---

### Post by c0mput3r_n3rD on 2009-07-18
It's no more clean nor efficient though.

using namespace std;

apposed to
std::cin
std::cout
std::endl

and
#include <vector>

apposed to

#inlcude "some hex number" // comment so you know what it is...

???

---

### Post by MadCow108 on 2009-07-18
not using namespace std; makes sence in this case
if he imports the whole std namespace the code will get confusing when he uses his vector class and the stl vector (although that would probably make little sense :) ).

importing only part of a namespace or everything is just a matter of style and has no effect on the performance or efficiency of the compiled program.

an argument for just importing what you need is that you see in the first line what is going to be used in the file.
importing everything needs less typing.
What you use is up to the programmer or coding convention of the project.

---

### Post by Kazade on 2009-07-18
Importing the entire std namespace is a very bad thing to do because it completely messes with name lookups. For example, if you defined your own own method called "find" and then you import the entire std namespace, you will hit conflicts with std::find. There are a lot of more obscure issues that you can hit including picking up the wrong operator methods and a bunch of other stuff. Basically it's a Very Bad Idea, don't do it. Just import what you need.

---

### Post by ibuclaw on 2009-07-18
The problem with your code is that it doesn't follow ANSI/ISO C++ standards.

I don't get a problem with this in g++ because it is rather lax about it all.

Here is my test program:
[PHP]
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

int main()
{
    cout << "Enter the desired number of trials: ";
    unsigned int uiTrial = 0u; cin >> uiTrial;
    unsigned long int ulResult[uiTrial];
    unsigned int ulSteps = 0L;
    
    for (unsigned int uii = 0; uii < uiTrial; ++uii)
    {
        ulSteps++;
        ulResult[uii] = ulSteps;
        cout << "Results: " << ulResult[uii] << endl;
    }

    return 0;
}
[/PHP]
And here is g++ compiling + running it.
```

iain@jstdio:~$ g++ c2466.cc 
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 0
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 3
Results: 1
Results: 2
Results: 3
iain@jstdio:~$ 

```

To mimic how the VSC++ compiler reacts to such a line, I had to turn on the -pedantic flag to ensure that the compiler followed strict ANSI compliance.
```

iain@jstdio:~$ g++ -pedantic c2466.cc 
c2466.cc: In function &#8216;int main()&#8217;:
c2466.cc:10: error: ISO C++ forbids variable length array &#8216;ulResult&#8217;

```


To work around, I suggest using a more industry standard approach.
[PHP]
#include <iostream>
#include <vector>

using std::cout;
using std::cin;
using std::endl;
using std::vector;

int main()
{
    cout << "Enter the desired number of trials: ";
    unsigned int uiTrial = 0u; cin >> uiTrial;

    /* Note the change here */
    vector<unsigned int> ulResult(uiTrial);

    unsigned int ulSteps = 0L;
    
    for (unsigned int uii = 0; uii < uiTrial; ++uii)
    {
        ulSteps++;
        ulResult[uii] = ulSteps;
        cout << "Results: " << ulResult[uii] << endl;
    }

    return 0;
}
[/PHP]

And here is g++ compiling + running it.
```

iain@jstdio:~$ g++ c2466fix.cc 
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 0
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 3
Results: 1
Results: 2
Results: 3
iain@jstdio:~$ 

```
And finally with the -pedantic flag.
```

iain@jstdio:~$ g++ -pedantic c2466fix.cc 
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 0
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 3
Results: 1
Results: 2
Results: 3
iain@jstdio:~$ 

```
And the moral of the story is ...  just #include <vector>

Regards
Iain

---

### Post by dwhitney67 on 2009-07-18
> **tinivole said:**
> ...

And the moral of the story is ...  just #include <vector>

Regards
Iain

Did the OP not state that he has not come across a discussion of the vector class in his studies?  That is probably why he is using his own version of it.  For all we know, he is taking course-work in which his instructor has told them to define their own vector class.

I will grant the he should rename his header file to something more intelligible.

Anyhow, there are software systems where the use of STL is unacceptable due to performance issues and the unpredictability of having an exception fling the processing of the application to Timbuktu.  In such cases, where the OOP aspects of C++ is desired, one can adhere to the Embedded-C++ standard.

If a programmer does not have an appreciation on how to develop a homemade-vector object, or a list object, or some other STL container, then they might not have the necessary skills to compete in the workplace.

Take this assignment for instance, that I was once given for a pre-screening for a job:
```

Below is the problem description for the test.  As the first step, please read the problem and decide on the approach you will take. Then write an explanation on what your approach will be to solve the problem.  Please include your expected running time (in big-O notation or equivalent).  The main purpose of the email is to check that your solution is heading in the right direction and that its runtime will be less than O(N^2).  (Programs with a runtime of O(N^2) or slower in the size of the input will fail the automated test suite.)

Afterwards, start on the implementation.

A couple of comments that might get you headed in the right direction:

1) While your final submission cannot use STL containers to store the data, nothing precludes you from using them in earlier submissions.  Previous candidates have achieved success this way. They were able to iron out their parsing and output code independently of the data store.  Obviously, you must balance this against the overhead involved in transitioning from one implementation to another.

2) In your design, consider the full range of data structures available to you.  Many C++ programmers will be drawn toward data structures based on trees.  That can work.  There are also simpler data structures that solve the problem.  I have seen list, vector and tree based solutions work too.

3) Be mindful of the fact that you only have 6 hours to design, implement, test, debug and submit your solution.  The earlier you make your first submission, the more time you'll have to react and respond if something isn't right.

```
```

Text File Indexer
=================

The goal of this problem is to create a program for indexing the words
in a set of files.  This document describes the behavior of the
program and its inputs and outputs.


Problem Description:
--------------------

The program which you need to write (which we will refer to as
"indexer") takes a list of filenames on the command line and prints an
index with an entry for each unique word in the files.  This index is
written to the standard output.

Each entry in the index starts with a line containing just the indexed
word.  This is followed by one line for each file in which the word
occurred.  Each "file line" starts with a tab character (ASCII
character 9), the filename as specified on the command line, and a
space separated list of line numbers on which the word occurs.

An example output for the program follows:

	$ cat foo.txt
	orange

	apple
	$ cat bar.txt
	apple orange
	orange
	orange
	$ cat ./baz.txt

	apple
	$ ./indexer foo.txt bar.txt ./baz.txt
	apple
		./baz.txt 2
		bar.txt 1
		foo.txt 3
	orange
		bar.txt 1 2 3
		foo.txt 1

The entries should be sorted by the indexed word, the file lines
within an entry should be sorted by filename, and the line numbers
should be sorted numerically.  For purposes of this problem, string
sorting is based off of the "POSIX" or "C" locale sort order (as for
example, the C library function strcmp uses).

For purposes of the basic problem, a word is any sequence of letters
or numbers, and any nonalphanumeric character delimits the word.  Words
are case sensitive.


Evaluation:
-----------

In addition to the evaluation criteria in the "general_description"
document, note that submitted programs are run against an automated
test suite.  This means that exact formatting is essential for
correctness.



Additional Information:
-----------------------

See the general description document for additional information
including evaluation criteria and more.

```

---

### Post by c0mput3r_n3rD on 2009-07-18
> **Kazade said:**
> Importing the entire std namespace is a very bad thing to do because it completely messes with name lookups. For example, if you defined your own own method called "find" and then you import the entire std namespace, you will hit conflicts with std::find. There are a lot of more obscure issues that you can hit including picking up the wrong operator methods and a bunch of other stuff. Basically it's a Very Bad Idea, don't do it. Just import what you need.

That's not true.  I never heard in any of my C++ programming classes that's it's a bad idea to include the whole name space.  I have two text books on C++ and they say nothing in them at all about not using the whole name space.  That's because performance and efficiency are not  affected what so ever.  I have not gotten any issues with puting the whole thing in there.  I have never heard of any issues, seen any issues, or be warned about any issues.  I think some programmers just like to make their code look more complicated and advanced than it is.  Ever heard of K.I.S.S. (not the rock band).  Keep It Simple Stupid.

---

### Post by Kazade on 2009-07-18
> **c0mput3r_n3rD said:**
> That's not true.  I never heard in any of my C++ programming classes that's it's a bad idea to include the whole name space.  I have two text books on C++ and they say nothing in them at all about not using the whole name space.  That's because performance and efficiency are not  affected what so ever.  I have not gotten any issues with puting the whole thing in there.  I have never heard of any issues, seen any issues, or be warned about any issues.  I think some programmers just like to make their code look more complicated and advanced than it is.  Ever heard of K.I.S.S. (not the rock band).  Keep It Simple Stupid.

Wow, well seeing as you have a whole TWO text books you must be right < / sarcasm>

It IS true. It's simple logic. The point of a namespace is to prevent naming conflicts. Typing using namespace std; completely obliterates the point of having a std namespace in the first place. You want some proof:

[http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5](http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5)

I know Scott Meyers mentions it in one of his Effective C++ books but I can't find the page number or item atm. Just trust me on this, you are wrong.

"using namespace X" doesn't affect efficiency or performance. It affects compilation and is bad practice. You know those errors that occur, and you don't know why, so you rearrange the code a bit and then it seems to work and you never understood why. These types of errors are normally caused by importing a function/variable/structure/class from somewhere you don't intend.

So, sorry your text books don't tell you this, you need to buy better text books or do some research before you start telling people they are wrong.

---

### Post by dribeas on 2009-07-18
> **Kazade said:**
> 
So, sorry your text books don't tell you this, you need to buy better text books or do some research before you start telling people they are wrong.

Text books require reading and understanding. I am sure that all c++ textbooks explicit that namespaces exists to avoid name conflicts and that adding the 'using namespace' into your code makes all the symbols in the namespace searchable by the compiler. Whether the textbook states it or not, the direct consequence of this is that the compiler can find ambiguities in the code where there were none.

---

### Post by lisati on 2009-07-18
My $0.02:

Having written programs for computers with seriously less RAM available at run time than today's machines, I would hesitate to import stuff into my code that wasn't really needed. There's only so much that that the optimization built in to compilers can do, and automatic optimization is not a good excuse for sloppy habits.

---

### Post by dribeas on 2009-07-18
> **lisati said:**
> My $0.02:

Having written programs for computers with seriously less RAM available at run time than today's machines, I would hesitate to import stuff into my code that wasn't really needed. There's only so much that that the optimization built in to compilers can do, and automatic optimization is not a good excuse for sloppy habits.

This is a common misunderstanding. The 'using namespace XXX' declaration does not import more stuff into the code. It only tells the compiler that when it finds an identifier, it must also search the XXX namespace, in case the symbol is defined there. This can sum up in compile time (not much though), should not have an impact in compilation memory usage and has no impact whatsoever on the generated binary.

---

### Post by c0mput3r_n3rD on 2009-07-19
> **dribeas said:**
> This is a common misunderstanding. The 'using namespace XXX' declaration does not import more stuff into the code. It only tells the compiler that when it finds an identifier, it must also search the XXX namespace, in case the symbol is defined there. This can sum up in compile time (not much though), should not have an impact in compilation memory usage and has no impact whatsoever on the generated binary.
And that's what my professor with 30 years industry and 10 years private business taught us.  Just include the whole using namespace std. and it will take what it needs when it needs it. 

And the whole creating your own vector class.... That's like reinventing the wheel... Which is what OOP programming is all about, not having to do that....

---

### Post by Oler1s on 2009-07-19
On a few different forums, in the past few days, I've seen threads repeatedly on the topic of namespaces, the using directive, and practices regarding the directive.

The debate seems to center around convenience, when in fact, the reason for namespaces is to avoid name collisions. Why is Kazade the only one who has brought up this issue?

Namespaces were introduced to help resolve name lookups. If your default approach in every source file is to have a using directive (for the std namespace) at file scope, how do you intend to deal with name collisions?

You could try and argue name collisions aren't an issue, but they are. Name a function sort, a common sensible name for say, sorting an array of some type, and you could find yourself facing a bizarre error (because the std::sort function is being called instead).

So how do you deal with it instead? Basically, people start prefixing identifiers to ensure that name collisions do not occur. Do we agree on this? If you don't rely or can't rely on something that the language provides, you must augment identifiers (a source level name mangling, basically). Do we like the way this is going?

---

### Post by lisati on 2009-07-19
I'm not a C++ programmer, so I'll leave the discussion of what namespaces are for to others who have actually used C++ for something more than doing "Hello World" programs. 

What I'm seeing here, perhaps mistakenly, is what looks like a call to produce what could turn into bloatware. This could be avoided with some careful program design.

---

### Post by Sockerdrickan on 2009-07-19
Namespaces were brought to C++ to help solve a **problem**. Now, novices strive to neglect this problem. Why not just use ansi C if you are not going to use C++ to its full extent?

I don't get it really.

---

### Post by dwhitney67 on 2009-07-19
When reading technical guides that suggest one thing vs another because of potential gotchas, one needs to carefully determine the probability of having a compilation error.

Many of the posts I have read in this thread, including the ParaShift coding standards offered in an earlier post, use the words "could", "can", and "should".  These are not very strong words; imagine if these were replaced with "would", "will", and "shall", respectively.  Perhaps then I would heed the advice offered; otherwise I am siding with those that have stated that a "using namespace std;" is a-ok in a source file.

If one can show an example, of name clash between a function declared in std and one in their C++ code, I'd be more than willing to reconsider my position.  But seriously, when programming, how often do you think one will come up with a naming clash?  It is probably a rare event.

To come up with a function name clash, not only would you have to have two functions with the same name, but also with the same "signature" (ie parameters, return type, etc).  An example, as cited earlier, is the std::sort() method.  Take a look at the API... that's not something typical that programmers throw together every day.

The sort() API from the STL documentation:
```

template <class RandomAccessIterator>
  void sort ( RandomAccessIterator first, RandomAccessIterator last );

template <class RandomAccessIterator, class Compare>
  void sort ( RandomAccessIterator first, RandomAccessIterator last, Compare comp );

```
Anyhow, I for one will continue to state "using namespace std" when it suits me; otherwise, for small functions, I just prefix the functions and operators I call with the std namespace prefix.

---

### Post by Kazade on 2009-07-19
> **dwhitney67 said:**
> .

If one can show an example, of name clash between a function declared in std and one in their C++ code, I'd be more than willing to reconsider my position.  But seriously, when programming, how often do you think one will come up with a naming clash?  It is probably a rare event.


It does happen. It's not only about what might clash now, but what might clash in the future. If you write some code that imports a whole namespace (not necessarily just the std one) from a library and then a new name is defined in a later version of that library which you were using, your code will break. Yes, it *might* happen or it might not, but it's better practice to not take the risk.

> 
To come up with a function name clash, not only would you have to have two functions with the same name, but also with the same "signature" (ie parameters, return type, etc).  An example, as cited earlier, is the std::sort() method.  Take a look at the API... that's not something typical that programmers throw together every day.


It's not just matching signatures, it's signatures that contain types that are implicitly convertible to other types as well. You import everything in a namespace, you contaminate name lookups with every name in that namespace - you have NO clue what that will import or whether it will conflict now, or in the future. 

It takes a few more keystrokes to import only the names you need like this:

using std::vector;
using std::cout;
etc.

or just prefixing the "std::" to the name when you use it, and it will save you a load of headaches in the long run. When the C++ gurus like Scott Meyers and Herb Sutter (Page 127, Exceptional C++) frown on the use of "using namespace X" in global scope, so should you. 

If you *really* want to use "using namespace X" then do it locally in the method body, not globally. At least then you are only importing names to a limited scope.

I'm just giving you advice from experience, you can of course choose to ignore it to save you those few keystrokes, your choice.

---

### Post by C++buntu on 2009-07-19
the weird #include "ex07ch11file3.h" is my own implementation of a vector class, if i would use the STL one, i would use #include <vector>...i'm not dumb ;)

---

### Post by C++buntu on 2009-07-19
> **tinivole said:**
> The problem with your code is that it doesn't follow ANSI/ISO C++ standards.

I don't get a problem with this in g++ because it is rather lax about it all.

Here is my test program:
[PHP]
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

int main()
{
    cout << "Enter the desired number of trials: ";
    unsigned int uiTrial = 0u; cin >> uiTrial;
    unsigned long int ulResult[uiTrial];
    unsigned int ulSteps = 0L;
    
    for (unsigned int uii = 0; uii < uiTrial; ++uii)
    {
        ulSteps++;
        ulResult[uii] = ulSteps;
        cout << "Results: " << ulResult[uii] << endl;
    }

    return 0;
}
[/PHP]
And here is g++ compiling + running it.
```

iain@jstdio:~$ g++ c2466.cc 
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 0
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 3
Results: 1
Results: 2
Results: 3
iain@jstdio:~$ 

```

To mimic how the VSC++ compiler reacts to such a line, I had to turn on the -pedantic flag to ensure that the compiler followed strict ANSI compliance.
```

iain@jstdio:~$ g++ -pedantic c2466.cc 
c2466.cc: In function ‘int main()’:
c2466.cc:10: error: ISO C++ forbids variable length array ‘ulResult’

```


To work around, I suggest using a more industry standard approach.
[PHP]
#include <iostream>
#include <vector>

using std::cout;
using std::cin;
using std::endl;
using std::vector;

int main()
{
    cout << "Enter the desired number of trials: ";
    unsigned int uiTrial = 0u; cin >> uiTrial;

    /* Note the change here */
    vector<unsigned int> ulResult(uiTrial);

    unsigned int ulSteps = 0L;
    
    for (unsigned int uii = 0; uii < uiTrial; ++uii)
    {
        ulSteps++;
        ulResult[uii] = ulSteps;
        cout << "Results: " << ulResult[uii] << endl;
    }

    return 0;
}
[/PHP]

And here is g++ compiling + running it.
```

iain@jstdio:~$ g++ c2466fix.cc 
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 0
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 3
Results: 1
Results: 2
Results: 3
iain@jstdio:~$ 

```
And finally with the -pedantic flag.
```

iain@jstdio:~$ g++ -pedantic c2466fix.cc 
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 0
iain@jstdio:~$ ./a.out 
Enter the desired number of trials: 3
Results: 1
Results: 2
Results: 3
iain@jstdio:~$ 

```
And the moral of the story is ...  just #include <vector>

Regards
Iain

Thanks for the input, i know that if i use the vector class i don't have this problem because a vector object can have a size of zero (like a string object in the string class), but, in the book i use (C++ Primer Plus - Stephen Prata), i'm not in the STL part yet...so we don't use it in the problems ;).

Another way around the problem is to dynamically allocate memory for my unsigned long int array...i will give it a shot ;)

---

### Post by C++buntu on 2009-07-19
> **c0mput3r_n3rD said:**
> That's not true.  I never heard in any of my C++ programming classes that's it's a bad idea to include the whole name space.  I have two text books on C++ and they say nothing in them at all about not using the whole name space.  That's because performance and efficiency are not  affected what so ever.  I have not gotten any issues with puting the whole thing in there.  I have never heard of any issues, seen any issues, or be warned about any issues.  I think some programmers just like to make their code look more complicated and advanced than it is.  Ever heard of K.I.S.S. (not the rock band).  Keep It Simple Stupid.

From the C++ Primer Plus book i read now, chapter 9 "Memory models and namespaces", Section "using Directives versus using Declarations".

To be read well:
using Directives = using namespace std;
using Declarations = using std::cout; ... etc

"Generally speaking, the using declaration is safer to use than a using directive because it shows exactly what names you are making available. And if the name conflicts with a local name, the compiler let's you know. The using directives adds all names, even ones you might not need. If a local name conflicts, it overrides the namespace version, and you aren't warned.
...
Namespace proponents hope that you will be more selective and use either the scope-resolution operator or the using declaration."

I think i can trust Stephen Prata ;)

---

### Post by C++buntu on 2009-07-19
> **c0mput3r_n3rD said:**
> And that's what my professor with 30 years industry and 10 years private business taught us.  Just include the whole using namespace std. and it will take what it needs when it needs it. 

And the whole creating your own vector class.... That's like reinventing the wheel... Which is what OOP programming is all about, not having to do that....

Like i've said, it's a beginner programming book and with this exercise, we don't come to the vector STL yet, so i don't use it. It's simple.

---

### Post by dribeas on 2009-07-19
> **c0mput3r_n3rD said:**
> And that's what my professor with 30 years industry and 10 years private business taught us.  Just include the whole using namespace std. and it will take what it needs when it needs it. 

And the whole creating your own vector class.... That's like reinventing the wheel... Which is what OOP programming is all about, not having to do that....

Now we are talking two different things: the cost of using the namespace with respect to performance of any type including compilation time --which is negligible I can admit it-- and the fact that namespaces are there to avoid collisions and that with the std::vector and user_defined::vector in place, the using declaration will produce name ambiguities to the compiler.

As dwhitney pointed, name collisions are not so common, but in this particular case there are two vector types in place. Admitedly there is not even a collision here, as the OP provided version starts with capital V: Vector, but at any rate, if some code includes the Vector header and the STL vector header, a simple 1 letter mistake (typing v instead of V or viceversa) will trigger a set of strange compilation errors.

At the end it is just a matter of style and what you are used to. I always fully qualify all std elements in my code (std:: are just 5 characters in for keyboard positions, easy to type), while I do use the using declarations for other libraries.

The world is neither white nor black, and mostly everything fits there. As long as you do not emply the using declaration in a header I would not complain in a code review with either style.

---

