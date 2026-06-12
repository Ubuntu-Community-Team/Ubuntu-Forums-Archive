---
title: "Using setjmp/longjmp to implement a generator"
date: 2011-05-25
forum: Programming Talk
---

### Post by DBQ on 2011-05-25
Hi everybody.  I am trying to use setjmp/longj,p in C++ to implement a generator.  My generator basically just iterates through the vector and returns successive values each time its called.  However, it seems that the environment is somehow not being restored correctly. Here is my code:

```

/* longjmp example */
#include <stdio.h>
#include <stdlib.h>
#include <setjmp.h>
#include <vector>
#include <iostream>
using namespace std;

jmp_buf genBuffer;
jmp_buf caller;

int generator(vector<int>& v)
{
        int i = 0;
        int val;



        while(i != v.size())
        {
                int ret = setjmp(genBuffer);

                if(ret != 0)
                {
                        ++i;

                }
                else
                {
                        cerr << "The value of i inside the function: " << i << endl;
                        cerr << "Size of the vector: " << v.size() << endl;
                        return v.at(i);
                }



        }

        return -1;

}


int main()
{
        vector<int> v;

        for(int i = 0; i < 10; ++i)
                v.push_back(i);

        cerr << "Value returned from the generator: " << generator(v) << endl;
        longjmp(genBuffer, 5);

        return 0;
}

```

I get this output:

```

The value of i inside the function: 0
Size of the vector: 10
Value returned from the generator: 0
The value of i inside the function: 1
Size of the vector: 4294967295
Segmentation fault

```

Any ideas?

---

### Post by DBQ on 2011-05-25
Any idea?

---

### Post by GeneralZod on 2011-05-25
I imagine you're falling foul of this:

[quote=man setjmp]
The stack context will be invalidated if the function which called setjmp() returns.
[/quote]

(from [here](http://linux.die.net/man/3/setjmp)).

---

### Post by ve4cib on 2011-05-25
Why are you using long jumps in the first place?  You could accomplish the same task using more conventional constructs, which would lead to more maintainable, easier to read code.

Is there a specific reason for using long jumps in this situation?

---

### Post by psusi on 2011-05-25
setjmp/longjump is an ancient C hack that has fallen out of use.  You certainly shouldn't be using it in C++.

---

### Post by ve4cib on 2011-05-25
I agree that they shouldn't be used in C++ unless you have some very specific needs that cannot easily be satisfied with other tools.  I wrote a post about one particularly interesting use for long jumps [here](http://ubuntuforums.org/showthread.php?t=1737660).

Anyway, assuming the OP is dead-set on long jumps, let's take a walk through the code and find out why it's breaking....

I think the problem is that with your longjmp call you're jumping from one function to another.  You have local variables defined within the generator function that will never be initialized when you longjmp into the function.

The reason this is breaking is because you return from generator *before* you can ever call longjmp.  As soon as you return the local variables inside generator are popped off the stack.  Then you longjmp back into a function whose scope has already been destroyed.

I've always found it useful to think of longjmp and setjmp as similar to try/catch/throw concepts in languages like C++, Java, Python, C#, etc...:

```

int ret = setjmp(jmp_buffer);
if (!ret)  // TRY
{
    // do stuff that might call a longjmp
    someFunction();
}
else  //CATCH
{
    // do stuff that handles the non-zero argument passed to longjmp
    printf("Received error code %d\n",ret);
}

...

void someFunction()
{
    // do stuff
    ...
    if(some_error)
    {
        longjmp(jmp_buffer, error_code);   // THROW
    }
}

```

Doing a simple replacement of the long jump code with try/catch blocks we get something like this:

```

try
{
    // do stuff that might throw an exception
    someFunction();
}
catch(Exception e)
{
    // do stuff that handles the exception
    printf("Received error code %d\n",e.value);
}

...

void someFunction()
{
    // do stuff
    ...
    if(some_error)
    {
        throw new Exception(error_code);
    }
}

```


You can see the similarities pretty easily.  When you call a longjmp you remove *everything* from the stack that came *after* the setjmp.  This includes nested function calls, local variables, etc, etc...

If we try to apply this try/catch similarity to the OP's code we see that it just doesn't work:

```

/* longjmp example */
#include <stdio.h>
#include <stdlib.h>
#include <setjmp.h>
#include <vector>
#include <iostream>
using namespace std;

jmp_buf genBuffer;
jmp_buf caller;

int generator(vector<int>& v)
{
        int i = 0;
        int val;



        while(i != v.size())
        {
                //int ret = setjmp(genBuffer);

                try //if(ret != 0)
                {
                        ++i;

                }
                catch(Exception e) //else
                {
                        cerr << "The value of i inside the function: " << i << endl;
                        cerr << "Size of the vector: " << v.size() << endl;
                        return v.at(i);
                }

        }

        return -1;

}


int main()
{
        vector<int> v;

        for(int i = 0; i < 10; ++i)
                v.push_back(i);

        cerr << "Value returned from the generator: " << generator(v) << endl;

        // the problem is right here: we're effectively
        // throwing an exception that gets caught by the function
        // we just returned from; the scope is backwards,
        // which causes all sorts of problems -- like segfaults
        throw new Exception(5); //longjmp(genBuffer, 5);

        return 0;
}

```

Does that explanation make any sense and/or help clear things up?


__________________

EDIT:

I also noticed that you're using "v.__" and not "v->__"  I'm a little rusty on my C++ syntax, but doesn't "vector<int>& v" mean that v is a pointer to a vector?  If so, you need to dereference the pointer before you can access the members of the vector.

---

