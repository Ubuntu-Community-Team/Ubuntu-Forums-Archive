---
title: "C++ Compililer Errors"
date: 2008-01-04
forum: Programming Talk
---

### Post by oops1644 on 2008-01-04
When I attempt to compile with G++ I keep getting the following compiler error

> VariblesandConstants.cpp: In function ‘int main()’:
VariblesandConstants.cpp:7: error: expected primary-expression before ‘=’ token
VariblesandConstants.cpp:15: error: expected primary-expression before ‘=’ token


Although I am just starting to learn C++, I cannot figure out why this error is being created.  

```
#include <iostream>
#include <string>
using namespace std;

#define MYNAME = "Peter Temporal"; 
int main(){
	string outString = MYNAME + "\n";	
	cout << outString;
		
	int a;
	int b;
		
	a = 2008;	
	b = 1986;
	outString = MYNAME + "'s age is " + (a-b);

	cout <<  outString;
	return 0;
}
```

---

### Post by aJayRoo on 2008-01-04
I don't think the equals sign is used for preprocessor directives (the #define statement) try removing it.

EDIT: actually there are other issues here too. Firstly it would be better to declare a string myname instead of using define to ensure the behaviour you are expecting. Also you cant treat an integer as a string, conversion is needed.

---

### Post by oops1644 on 2008-01-04
Nope still getting the errors, thanks though

EDIT: Tried your edit suggestions, and now its working fine thanks for your help!

---

### Post by Fixman on 2008-01-04
There are two errors:

a) In C++, a phrase in "" (like "hi, my name is") is not of type string but of type const char *. But, theres a string constructor that works for const char *, the problem here is that you can't sum a const char * to another const char * (albeit you can sum a string to a const char * and vice versa). So, to fix line 5 you could do

```

string outString = MYNAME ;
outString += "\n" ;

```

Or, you could also do

```

string outString = MYNAME + string("\n") ;

```

Now, the second error (line 15) is because of this and because you **can't sum a string and an integer on C++**. To correct this, you could use a class called stringstream.

```

#include <sstream>
//.......
stringstream outString (MYNAME + string("'s age is)) ;
outString << (a - b) ;

cout << outString.str() ; //remember of .str() here

```

The full code could be quickly and easily made by

```

#include <iostream>

using namespace std;

#define MYNAME = "Peter Temporal"; 
int main(){
	cout << MYNAME << "\n" ;
		
	int a;
	int b;
		
	a = 2008;	
	b = 1986;

	cout <<  MYNAME << "'s age is " << (a - b) ;
	return 0;
}

```

EDIT: dammit, late for few seconds!

---

### Post by Wybiral on 2008-01-04
No, the "=" sign in the preprocessor directive is one of the problems as aJaRoo pointed out. But you also cannot add two C character arrays with the "+" operator, you need to instantiate them as C++ strings, then use the string "+" operator. You also cannot "+" an integer into a string, you need to convert it to a string, then concatenate it with "+".

I suggest using a string stream for the integer and putting string("my C array") around your literals (or C-style character arrays).

EDIT:

lol, beat by both of you guys/girls.

---

### Post by Jessehk on 2008-01-04
Your problem is the #define directive.

```

#define NAME = "Joe Smith";

```

doesn't do what you think it does.

#define simply perform text substitution  that is done **before** the source is fed to the compiler.

It works in the form:
```

#define *thing* *replacement*

```

In C, along with enums, this is the only way to define constants. In C++ however, there are better alternatives.
This would be the correct replacement code:

```

const std::string name( "Joe Smith" );

```

:)

---

### Post by aJayRoo on 2008-01-04
I think I would probably have done it this way rather than using the define statement and joining strings together. Just create a constant string and use the output stream to put everything together. Of course this is not the only way, the joy of programming is figuring out your own way to do things!

[php]#include <iostream>
#include <string>
using namespace std;

int main()
{
    int a, b;

    const string myName = "Peter Temporal";
	cout << myName << endl;

    a = 2008;
    b = 1986;
    cout << myName << "'s age is " << a-b << endl;
		
	return 0;
}[/php]

EDIT: Although if you did want to use the #define directive then you could remove the line ```
const string myName = "Peter Temporal";
``` and insert the definition ```
#define myName "Peter Temporal"
``` in the appropriate place.

---

### Post by Kadrus on 2008-01-04
I think the code should be like this:
```

#include <iostream>
#include <string>
using namespace std;

#define MYNAME  "Peter Temporal"; 
int main(){
	string outString = MYNAME + "\n";	
	cout << outString;
		
	int a;
	int b;
		
	a = 2008;	
	b = 1986;
	outString = MYNAME + "'s age is " + (a-b);

	cout <<  outString;
	return 0;
}

```
You shouldn't put the equal sign when defining the name..
Hope this helped :)

---

### Post by jespdj on 2008-01-04
> **Kadrus said:**
> I think the code should be like this:
```

#include <iostream>
#include <string>
using namespace std;

#define MYNAME  "Peter Temporal"; 
// ...

```
You shouldn't put the equal sign when defining the name..
Hope this helped :)
You also should not put a semi-colon after the #define line. It should be like this:
[php]#include <iostream>
#include <string>
using namespace std;

// NOTE: No semi-colon
#define MYNAME  "Peter Temporal"

// ...[/php]

---

### Post by Kadrus on 2008-01-04
> **jespdj said:**
> You also should not put a semi-colon after the #define line. It should be like this:
[php]#include <iostream>
#include <string>
using namespace std;

// NOTE: No semi-colon
#define MYNAME  "Peter Temporal"

// ...[/php]
I think you should..you will get errors..
[php]
ex.cpp: In function ‘int main()’:
ex.cpp:7: error: invalid operands of types ‘const char [15]’ and ‘const char [2]’ to binary ‘operator+’
ex.cpp:15: error: invalid operands of types ‘const char [15]’ and ‘const char [11]’ to binary ‘operator+’
[/php]

---

### Post by aJayRoo on 2008-01-04
It certainly compiles with the semi colon at the end of the define but it does NOT do what is intended, the reason is mentioned earlier in the post. The correct define statement would be:
```
#define MYNAME "blah blah"
```
The reason it has errors if the semi colon is removed is due to errors in the code of the main function.

---

