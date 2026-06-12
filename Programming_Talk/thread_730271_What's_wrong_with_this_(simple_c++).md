---
title: "What's wrong with this (simple c++)?"
date: 2008-03-20
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-03-20
i'm a beginning c++ "student" - self-teaching.

anyway, i entered some code as i was told to by the book i'm learning from, and when i try to compile, i seem to get all sorts of errors. i know what they mean; what i want to know is why they're there and what needs to be done to fix it.

any help would be great, thank you.

```
#include <iostream>
using namespace std;

int main()
{
	enum sizes (small, medium, large, jumbo);	// declares a variable type named 'sizes'
	sizes drinkSize, popcornSize;				// declares the variables 'drinkSize' and 'popcornSize' with a data type of 'sizes'
	
	drinkSize = large;
	popcornSize = jumbo;
	
	if (drinkSize == large)
	{
		cout << "You would have a jumbo for just a quarter more.\n";
	}
	if ( (popcornSize == jumbo) && (drinkSize != jumbo) )
	{
		cout << "You need more drink to wash down a jumbo popcorn.\n";
	}
	
	return 0;
}

```

Error-log:
[code]
enumtest.cpp: In function ‘int main()’:
enumtest.cpp:28: error: use of enum ‘sizes’ without previous declaration
enumtest.cpp:28: error: expected primary-expression before ‘enum’
enumtest.cpp:28: error: expected `;' before ‘enum’
enumtest.cpp:29: error: ‘sizes’ was not declared in this scope
enumtest.cpp:29: error: expected `;' before ‘drinkSize’
enumtest.cpp:31: error: ‘drinkSize’ was not declared in this scope
enumtest.cpp:31: error: ‘large’ was not declared in this scope
enumtest.cpp:32: error: ‘popcornSize’ was not declared in this scope
enumtest.cpp:32: error: ‘jumbo’ was not declared in this scope
[\code]

---

### Post by Sinkingships7 on 2008-03-20
wow. i'm dumb. never mind.

in case there's ever another blind person trying to learn how to program, the error was in the parentheses around the possibilities for sizes.

```
enum sizes (small, medium, large, jumbo);
```

those parentheses should be braces.


sorry for the interruption. continue your programming :p

---

### Post by Curtisc on 2008-03-20
Edit: Good catch, I was a little slow in my reply.

---

