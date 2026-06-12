---
title: "[SOLVED] C++ compiling with header"
date: 2008-10-14
forum: Programming Talk
---

### Post by jspolen on 2008-10-14
Hi, this is probably an easy problem but I can't seem to figure it out. Just started playing around with C++ and have divided my program into three files. 

First is main.cpp 

```

#include <iostream>
#include <vector>
#include <string>
using namespace std;

#include "longest.h"

int main()
{
	string test = "abc";
	vector<string> current;
	vector<string> newOnes;
		
	while( test.size() > 1) {
		cout << "Enter a string: ";
		cin >> test;
		if( test.size() > 1 ) {
			current.push_back( test );
		}
	}
	
	newOnes = longest( current );
	for( int i = 0; i < newOnes.size(); i++ )
		cout << newOnes[i] << endl;
			
	return 0;
}

```

then i have my header file longest.h

```
vector<string> longest( const vector<string> & strings );
```

And finally longest.cpp

```

#include "longest.h"

vector<string> longest( const vector<string> & strings )
{
	int currentMaxSize = 0;
	vector<string> theLongOnes;
	
	for( int i = 0; i < strings.size(); i++ ) {
		if( strings[i].length() > currentMaxSize )
			currentMaxSize = strings[i].length();
	}
	
	for( int i = 0; i < strings.size(); i++ ) {
		if( strings[i].length() == currentMaxSize )
			theLongOnes.push_back( strings[ i ] );
	}
	
	return theLongOnes;

}

```

The program is intended to find the longest string in a vector and return a new vector containing the longest of them. It works if I put it in one file, but can't seem to compile and link it like this.

Can anyone see what I'm doing wrong?

---

### Post by WW on 2008-10-14
> **jspolen said:**
> 
It works if I put it in one file, but can't seem to compile and link it like this.

Can anyone see what I'm doing wrong?
When you ask a question like this, it would be very helpful if you included the commands that you tried, and the error messages that resulted from those commands.

It looks like you haven't included all the necessary header files in longest.cpp. Just like the main program, it uses vectors and strings (in the std namespace), so it also needs these lines:
```

#include <vector>
#include <string>
using namespace std;


```

---

### Post by jspolen on 2008-10-14
okay, I've now included these lines at the top of my longest.cpp file.
```

#include <vector>
#include <string>
using namespace std;

```

and tried to compile it with *g++ longest.cpp -o longest.o* which gives me the error:
```
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

```

if I try to compile main with *g++ main.cpp -o main.o* I get:
```

/tmp/cc4Mdesz.o: In function `main':
main.cpp:(.text+0x2cc): undefined reference to `longest(std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > const&)'
collect2: ld returned 1 exit status

```

---

### Post by WW on 2008-10-14
Try this:
```

g++ -c longest.cpp
g++ -c main.cpp
g++ main.o longest.o -o main

```
The first two commands compile the code to object files.  The third links the object files to create the executable. To run the program:
```

./main

```

---

### Post by jspolen on 2008-10-14
Ah perfect!

Works great!

Thank you!

---

### Post by dwhitney67 on 2008-10-14
> **jspolen said:**
> 
...
[php]
#include <iostream>
#include <vector>
#include <string>
using namespace std;

#include "longest.h"
...
[/php]
...


WW was correct with his analysis.  But here's another tidbit that many programmers (even experienced ones) neglect to see...

ALWAYS include local header files before system header files.  Had you done the following:
[PHP]#include "longest.h"

#include <iostream>
#include <vector>
#include <string>
using namespace std;
...[/PHP]
then perhaps your errors would have surfaced sooner.


P.S.  When compiling one or two (maybe three) modules, it can be done in one step.  For instance:
```
g++ a.cpp b.cpp main.cpp -o exec
```

If you have to make your exec many times, then I suggest you rely on a Makefile.

---

