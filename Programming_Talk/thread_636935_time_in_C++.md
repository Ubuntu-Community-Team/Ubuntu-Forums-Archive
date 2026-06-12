---
title: "time in C++"
date: 2007-12-10
forum: Programming Talk
---

### Post by fourthdimension on 2007-12-10
Hey All

I'm trying to write a really simple program in C++ that uses the time function.  All I want it to do is output the current time.
Here's what I have so far:
```

#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <cstring>
#include <ctime>

int main()

{	int time();
	cout<< time;
	return 0;	
}

```  

First, do I need to include everything I did?  And second, I get this compiler error:
```

timeTest.cpp:11: error: ‘cout’ was not declared in this scope

```
I'm in the process of writing simple programs that use each new thing I learn, and I constantly amaze myself with how badly I can mess up three lines of code! :lolflag:
Thanks.

---

### Post by iharrold on 2007-12-10
use "std::cout"

Also:  Time returns a "time_t" type and you never declared the variable name for your time storing variable.

i.e:
```

#include <iostream>
#include <ctime>

int main(int argc, char* argv[])
{	
        std::time_t t1 = std::time(0);
	std::cout<< t1;
	return 0;	
}

```

---

### Post by meatpan on 2007-12-10
The compiler cannot find a suitable declaration for 'cout'.  Since there is no mention of 'namespace std' (via a using declaration, or a fully qualified 'std::cout'), the compiler is searching the global namespace and not findiing a match.  Somehow you need to tell the compiler about the namespace that cout belongs to.

Consider using 'std::cout' instead of just 'cout', and see if this fixes your problem.

---

### Post by LaRoza on 2007-12-10
Your code doesn't make sense.

You declare a function prototype, within another function, and try to output a nonexistant variable.

---

### Post by iharrold on 2007-12-10
Also, time_t is a typdef of a generally a 32 bit signed integer... however, you should still use the proper type.  Either way though the output will just be a number.  You must manipulate the number (actually number of seconds since Jan 1, 1970 0:00 GMT) to make it more meaningful.

Edit: and if you wanted some error handling in the code:

```

#include <iostream>
#include <ctime>
#include <cerrno>

int main(int argc, char* argv[])
{	
        std::time_t t1 = std::time(0);
	if (t1 == std::time_t(-1))
        {
             std::cerr<<"Bad time\n";
             exit(1);
         }
        std::cout<< t1;
	return 0;	
}

```

---

### Post by fourthdimension on 2007-12-10
Thanks for the quick response!  Yeah, I'm learning as I go here, so I sort of expect most of my code to not make sense at first.
I fixed those problems and now I have this code:
```

#include <iostream>
#include <ctime>
#include <cerrno>

int main(int argc, char* argv[])
{	
        std::time_t t1 = std::time(0);
	if (t1 == std::time_t(-1))
        {
             std::cerr<<"Bad time\n";
             exit(1);
         }
        std::cout<< t1;
	return 0;	
}

```

My only problem now is that, as mentioned earlier, I get the time in some sort of raw format.  Any ideas on how to convert that to the traditional hours, mins, secs etc?  The reason I'd like to know is that this code is going to be part of a larger program that will run certain programs at certain times in the day, or countdown to a certain time then run a program.  I know there are already programs out there I could use, but I wanted the learning experience of writing my own.
Thanks again.

---

### Post by iharrold on 2007-12-10
[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)
[http://www.cppreference.com/](http://www.cppreference.com/)

Both sights will be invaluable to you.

To answer your question transform the time_t into a tm struct via gmtime.

i.e.
```

tm * gt = gmtime(&t1);

```

I'll let you figure out how to display it.  This is just one of many possible approaches.  I'm not giving the full answer, because it smells like a homework assignment and I cannot spoon feed it to you, but I will help and point you in the right directions ;)

---

### Post by fourthdimension on 2007-12-13
OK, thanks a lot for the references!  
No, it's not a homework assignment lol!  I'm homeschooled, so I don't have programming classes or anything.  I'm just teaching myself because it will be useful for me to know C++ before I start my software engineering courses next September.

---

