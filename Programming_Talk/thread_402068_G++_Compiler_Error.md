---
title: "G++ Compiler Error"
date: 2007-04-05
forum: Programming Talk
---

### Post by Peter1234123 on 2007-04-05
I bought a few books on C++, "Sam's Learn C++ In 10 Minutes" "Sam's Teach Yourself C++ in 21 Days", and I attempted to make a program listed in the book, I copied it exactly, and G++ is giving me an error message, here is the code: 
```
#include <iostream>

using namespace std;

int main(int argc, char* argv[])
{
	
	count << ((6/2)+3) << end1;
	return 0;
}

```
 
and here is what G++ says: 
```
peter@laptop:~$ g++ project.cpp -o project
project.cpp: In function ‘int main(int, char**)’:
project.cpp:8: error: invalid operands of types ‘<unknown type>’ and ‘int’ to binary ‘operator<<’
project.cpp:8: error: ‘end1’ was not declared in this scope
```

Any tips?

---

### Post by LaRoza on 2007-04-05
It is not "count" but "cout" pronounces "see-out".

Try it again.

---

### Post by LaRoza on 2007-04-05
I foresee trouble...


#include <iostream>

int main();
int main()
{

	
std::cout << ((6/2)+3) << std::endl; // it is endl not end1. endl as in "end line"

return 0;
}

Copy and paste this, compile, run

---

### Post by Peter1234123 on 2007-04-05
Ahh, that gets rid of one error, still get 
```
peter@laptop:~$ g++ project.cpp -o project
project.cpp: In function &#8216;int main(int, char**)&#8217;:
project.cpp:8: error: &#8216;end1&#8217; was not declared in this scope
```

though

---

### Post by LaRoza on 2007-04-05
endl
ee-en-dee-ell


not end1
ee-en-dee-one

This is a great site:

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by Monk-e on 2007-04-05
-"count" should be "cout"
-"end1" should be "endl" (as in lowercase L)

---

### Post by Peter1234123 on 2007-04-05
Lol, the book was typed in monotype (whatever it's called), and l looks like 1, :P

---

### Post by LaRoza on 2007-04-05
I know the feeling...

Sometimes programming books have typos. It is hell for a beginner to debug what you are learning from. Sams is usually a good series, I have several of their books.

The programs in the books you have will run on Windows, but you have to compile them again. in Windows.

Are you new to programming? What other languages have you studied?

---

### Post by Peter1234123 on 2007-04-05
I'm totally new to C++, Ive done BASIC in the past, but it's pretty much useless :P.

---

### Post by tokj on 2007-04-05
Sorry, but isn't this thread a dupe of [this](http://ubuntuforums.org/showthread.php?t=402067)?

There is no need to open more than one thread for the same problem.

---

### Post by Peter1234123 on 2007-04-05
By the way, are there any XML IDEs for Ubuntu?

---

### Post by LaRoza on 2007-04-05
Have fun learning C++.

You might want to try Python, too. It is interpreted so you don't have to compile. I just started learning.

See the "Power of Python" thread.

---

### Post by LaRoza on 2007-04-05
XML IDE? Gedit has syntax  highlighting for XML, if that is what you want.

---

### Post by frodon on 2007-04-05
Duplicated threads merged

---

### Post by Peter1234123 on 2007-04-05
Thanks

---

### Post by Peter1234123 on 2007-04-05
Yeah, accidentally hit submit twice, sorry.
I also ran into another problem, I typed this into a C++ IDE, compiled it, and got a 3 page error message :P. 

```
#include <iostream>

using namespace std;

int main(int argc, char* argv[])
{
	cout << ((6/2)+3) <<endl

	char StopCharacter;
	cout << endl < "Press a key and \"Enter\": ";
	cin >> StopCharacter;

	return 0;
}
```

---

### Post by LaRoza on 2007-04-05
I am using comments to show you the errors and I corrected them


#include <iostream>

using namespace std;

int main(int argc, char* argv[])
{
	cout << ((6/2)+3) <<endl;                           //no semi-colon ;

	char StopCharacter;
	cout << endl << "Press a key and \"Enter\": "; //Missing <<
	cin >> StopCharacter;                                   //This is not an error but is dangerous 

	return 0;
}

---

### Post by LaRoza on 2007-04-05
If you want you can email me with individual questions. For the moment you are doing simple programs, so there is little need to ask everybody. I also am using multiple tabs to view different forums so coming back to this thread takes a while, Firefox Portable is slow so having a single tab to deal with this would be easier.

---

### Post by Peter1234123 on 2007-04-05
Ahh, thanks, I rewrote the code to be:



```
using namespace std;

int main(int argc, char* argv [])
{
	const int Dividend = 6;
	const int Divisor =2;

	int Result = (Dividend/Divisor);
	Result = Result +3;
	
	cout << Result << endl;
	
	char StopCharacter;

	cout <<endl << "Press a key and \"Enter\": ";
	cin >> StopCharacter;

	return 0;
```
and it works perfectly now.

---

### Post by LaRoza on 2007-04-05
cin is dangerous to use. You can easily crash the program.

for this:

char myChar;
cin >> myChar;

use this:

char myChar;
getline(cin,myChar);

---

### Post by pmasiar on 2007-04-05
> **Peter1234123 said:**
> I'm totally new to C++, Ive done BASIC in the past, but it's pretty much useless :P.

Python is *much* simpler language for beginners, in opinion of many.

Check [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart) - I just added link to interesting Python videos on ShowMeDo, and promised cheatsheets

---

### Post by LaRoza on 2007-04-05
I recommended Python as well, but since I started with C++ I won't try to change anyone's mind.

[http://diveintopython.org/index.html](http://diveintopython.org/index.html)

I just downloaded this book. I haven't read it yet though.

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

This is a good online tutorial for C++.

I have no trouble learning more than one language at a time though...

I am currently studying C++,Python,SQL (MySQL).

Python may make it easier to learn C++, but
Python is even easier to learn if you study C++ first.

---

