---
title: "C++ error: no member function declared in class"
date: 2011-02-09
forum: Programming Talk
---

### Post by Asdra on 2011-02-09
Hello,

I am writing a calculator program using arbitrary precision arithmetic in C++.  I'm currently shifting from a single-file implementation to a multi-file implementation by making an APAnum class to implement the numbers themselves so I can keep track of all the important information I need to know about the numbers and overload the arithmetic operators.

I've gotten APAnum.h to compile, but whenever I attempt to compile APAnum.cpp I get the following error:

no member function declared in class 'APAnum'

I get this error for all of my functions that overload operators.  I've tried everything I can think of, and I couldn't find anything on this error specifically...what's going on?

Thanks in advance!

Here's the code related to the overloaded operators:

APAnum.h
```

#include <cstdlib>
#include <iostream>
#include <cmath>
#include <fstream>
#include <cstring>
#include <sstream>
#include <vector>
#include <assert.h>

class APAnum
{
    private:
    //variables
    
    public:
    //constructors and other functions
    friend const APAnum operator >(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator <(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator >=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator <=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator +(const APAnum &num2);
    friend const APAnum operator -(const APAnum &num2);
    friend const APAnum operator *(const APAnum &num2);
    friend const APAnum operator /(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator %(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator +=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator -=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator *=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator /=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator %=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator ==(const APAnum &num1, const APAnum &num2);
};

```APAnum.cpp
```

#include <cstdlib>
#include <iostream>
#include <cmath>
#include <fstream>
#include <cstring>
#include <sstream>
#include <vector>
#include <assert.h>
#include "APAnum.h"

using namespace std;

const APAnum APAnum::operator >(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator <(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator >=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator <=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator +(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator -(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator *(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator /(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator %(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator +=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator -=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator *=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator /=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator %=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator ==(const APAnum &num2)
{
    //finish
}

```I know that the functions don't have anything in them in the .cpp, but if I'm still getting an error before I've filled the functions in I figure I should fix that first.

---

### Post by cipherboy_loc on 2011-02-09
Try removing the Const before the implementations in the .cpp file.



Cipherboy

---

### Post by worksofcraft on 2011-02-09
> **Asdra said:**
> Hello,

I am writing a calculator program using arbitrary precision arithmetic in C++.  I'm currently shifting from a single-file implementation to a multi-file implementation by making an APAnum class to implement the numbers themselves so I can keep track of all the important information I need to know about the numbers and overload the arithmetic operators.

I've gotten APAnum.h to compile, but whenever I attempt to compile APAnum.cpp I get the following error:

no member function declared in class 'APAnum'

I get this error for all of my functions that overload operators.  I've tried everything I can think of, and I couldn't find anything on this error specifically...what's going on?

Thanks in advance!

Here's the code related to the overloaded operators:

APAnum.h
```

#include <cstdlib>
#include <iostream>
#include <cmath>
#include <fstream>
#include <cstring>
#include <sstream>
#include <vector>
#include <assert.h>

class APAnum
{
    private:
    //variables
    
    public:
    //constructors and other functions
    friend const APAnum operator >(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator <(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator >=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator <=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator +(const APAnum &num2);
    friend const APAnum operator -(const APAnum &num2);
    friend const APAnum operator *(const APAnum &num2);
    friend const APAnum operator /(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator %(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator +=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator -=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator *=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator /=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator %=(const APAnum &num1, const APAnum &num2);
    friend const APAnum operator ==(const APAnum &num1, const APAnum &num2);
};

```APAnum.cpp
```

#include <cstdlib>
#include <iostream>
#include <cmath>
#include <fstream>
#include <cstring>
#include <sstream>
#include <vector>
#include <assert.h>
#include "APAnum.h"

using namespace std;

const APAnum APAnum::operator >(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator <(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator >=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator <=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator +(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator -(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator *(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator /(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator %(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator +=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator -=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator *=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator /=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator %=(const APAnum &num2)
{
    //finish
}

const APAnum APAnum::operator ==(const APAnum &num2)
{
    //finish
}

```I know that the functions don't have anything in them in the .cpp, but if I'm still getting an error before I've filled the functions in I figure I should fix that first.

IDK about the error message but you will have to return something from the friendly operators...

p.s. actually yes I do know the friends are NOT members so you need to remove the APAnum:: like this:
[php]
const APAnum operator >(const APAnum &num1, const APAnum &num2)
{
    return APAnum();
}
[/php]

---

### Post by ibuclaw on 2011-02-09
Look at the function signatures in APAnum.h, look at the function signatures in APAnum.cpp

What do you notice about the parameters each function takes?

---

### Post by matt_symes on 2011-02-09
Hi

Declaration...

```
friend const APAnum operator >(const APAnum &num1, const APAnum &num2);
```

!=

Definition...

```
const APAnum APAnum::operator >(const APAnum &num2)
{
}
```

Either have them as member functions or not; although i would suggest helper functions for these.

Kind regards

---

### Post by Asdra on 2011-02-09
Hello again,

Thanks for the help!  What worksofcraft and matt_symes suggested worked!  I was basing this code off of code I had received in a C++ class I took recently, but I've been discovering as of late that any code from that course has a tendency to explode when I try to replicate it anywhere else...Thanks again!

---

### Post by nvteighen on 2011-02-10
What I don't understand is why you want those operators as friends... You could declare them to be methods (well, that means that you'll have to change the signatures back to APAnum::... :P).

Befriended operators are used when you need to overload an operator that already exists outside your class. The classic example is the overloading of the global operator<< to make a class be printable for std::cout.

---

### Post by Asdra on 2011-02-10
Well, all those operators do exist outside of my class, and they didn't work with string arguments until I overloaded them.  Making them friends of the class seemed like a smart way to go about writing this code, as the member variables are private.

Maybe I just need to learn more of the nitty-gritty details about C++, but this seemed like a perfectly acceptable way to get my class running.

Though, I do have another issue that's come up: I keep getting some error when I compile the .cpp file (now with the previous error fixed) that reads:

/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18 ): undefined reference to `main'
collect2: ld returned 1 exit status

Any idea where that could be coming from?

---

### Post by ibuclaw on 2011-02-11
That means there's no 'main' function in your program. And if there is, you're not including it in the final link stage. :)

---

### Post by Asdra on 2011-02-11
Fair enough.  Thanks for the help guys!

---

