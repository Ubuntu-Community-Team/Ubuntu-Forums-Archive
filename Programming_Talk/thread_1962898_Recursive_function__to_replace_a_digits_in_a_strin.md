---
title: "Recursive function  to replace a digits in a string"
date: 2012-04-21
forum: Programming Talk
---

### Post by mosesaro on 2012-04-21
Recursive Function that replaces a digit with a *

Can anybody help me understand how to write this, I am a beginner.

Write a recursive function which takes an integer as it's parameter, and 
prints out all the digits of this number in the same order, except replacing all the 7's with star.
ex:
7410747
*410*4*

7
*

243985
243985

---

### Post by DaviesX on 2012-04-21
What language ?

---

### Post by DaviesX on 2012-04-21
```

#include <stdio.h>

void StrMask ( char *string );

int main()
{
    char string[] = "7410747";
    StrMask ( string );
    printf ( "%s\n", string );
    return 0;
}

void StrMask ( char *string )
{
    if ( *string == 0 )
    {
        return ;
    }
    else if ( *string == '7' )
    {
        *string = '*';
    }

    string++;
    StrMask ( string );
}

```

I made this, and it seems work :)

---

### Post by mosesaro on 2012-04-21
Thanks it worked , Im just going to have to pick your brain a bit to understand how exactly this works.


So you keep incrementing the number at the end string++;?

by the way I'm using c

---

### Post by DaviesX on 2012-04-21
I use mixture of c and c++, I don't use OO though.
That is not increasing the number, it is increasing its starting address

---

### Post by DaviesX on 2012-04-21
For example, a string 
char str[12] = "mississippi";
and 
char *addr = str;
assume that the starting address is 1 which means addr is 1
and addr represents the string "mississippi"

addr++; means it moves the pointer to the next element and now its address is 2
where it represents the string "ississippi"

then when I do addr++; one more time
it will be "ssissippi"
and so on...

---

### Post by mosesaro on 2012-04-21
So basically this is just like a search and replace.
Is there a way to write this using 
function (int x)

---

### Post by DaviesX on 2012-04-21
I replace some pointer expression with array expression which might be easier to understand, I keep preceding the address of string[0] so that it always can get new character to be processed
```

#include <stdio.h>

void StrMask ( char *string );

int main()
{
    char string[] = "7410747";
    StrMask ( string );
    printf ( "%s\n", string );
    return 0;
}

void StrMask ( char *string )
{
    // When reaches the end, exits
    if ( string[0] == 0 )
    {
        return ;
    }
    else if ( string[0] == '7' )
    {
        string[0] = '*';
    }

    // points to next element
    string++;
    StrMask ( string );
}

```

---

### Post by DaviesX on 2012-04-21
> **mosesaro said:**
> So basically this is just like a search and replace.
Is there a way to write this using 
function (int x)

You can actually use a loop instead :)

```

#include <stdio.h>

void StrMask ( char *string );

int main()
{
    char string[] = "7410747";
    StrMask ( string );
    printf ( "%s\n", string );
    return 0;
}

void StrMask ( char *string )
{
    while ( string && *string )
    {
        if ( *string == '7' )
        {
            *string = '*';
        }
        string++;
    }
}

```

---

### Post by mosesaro on 2012-04-21
Whats the loop maybe I can write up a recursion I HAVE to use recursion. I thought of other ways of doing but I have to use recursion.

---

### Post by DaviesX on 2012-04-21
So you want to write it as function (int x) ?
but what could that means ?

---

### Post by mosesaro on 2012-04-21
instead of the parameter for the function being string it has to be an integer.

---

### Post by DaviesX on 2012-04-21
Ok, I get it, please give me some time

---

### Post by mosesaro on 2012-04-21
thank you so much

---

### Post by DaviesX on 2012-04-21
I'm sorry that I can't make exactly that form of function, but I can do the most similar like this
```

#include <iostream>
using namespace std;

void StrMask ( int number, char *string );

int main()
{
    char string[64];
    StrMask ( 7410747, string );

    return 0;
}

void StrMask ( int number, char *string )
{
    if ( number > 0 )
    {
        int temp = number%10;

        if ( temp == 7 )
        {
            *string = '*';
        }
        else
        {
            *string = '0' + temp;
        }

        StrMask ( (number - temp)/10, ++string );
    }
    else
    {
        *string = 0;
        return ;
    }

    cout << *(string - 1);
}

```

And I achieved correct result in gcc compiler

---

### Post by mosesaro on 2012-04-21
> **DaviesX said:**
> I'm sorry that I can't make exactly that form of function, but I can do the most similar like this
```

#include <stdio.h>

void StrMask ( int number, char *string );

int main()
{
    char string[64];
    StrMask ( 7410747, string );
    printf ( "%s\n", string );

    return 0;
}

void StrMask ( int number, char *string )
{
    if ( number > 0 )
    {
        int temp = number%10;

        if ( temp == 7 )
        {
            *string = '*';
        }
        else
        {
            *string = '0' + temp;
        }

        StrMask ( (number - temp)/10, ++string );
    }
    else
    {
        *string = 0;
        return ;
    }
}

```

And I achieved correct result in gcc compiler

Thanks,

what does printf ( "%s\n", string ); mean Im used to cout

---

### Post by DaviesX on 2012-04-21
By the way, if you take negative numbers into account, you can achieve by doing this
```

#include <stdio.h>

void StrMask ( int number, char *string );

int main()
{
    char string[64];
    StrMask ( -7410747, string );
    printf ( "%s\n", string );

    return 0;
}

void StrMask ( int number, char *string )
{
    if ( number > 0 )
    {
        int temp = number%10;

        if ( temp == 7 )
        {
            *string = '*';
        }
        else
        {
            *string = '0' + temp;
        }

        StrMask ( (number - temp)/10, ++string );
    }
    else if ( number < 0 )
    {
        *string = '-';
        StrMask ( -number, ++string );
    }
    else
    {
        *string = 0;
        return ;
    }
}

```

(This one is wrong, but I don't know how to delete it)

---

### Post by DaviesX on 2012-04-21
> **mosesaro said:**
> Thanks,

what does printf ( "%s\n", string ); mean Im used to cout

sure, you can do like this 
```

#include <iostream>
using namespace std;

void StrMask ( int number, char *string );

int main()
{
    char string[64];
    StrMask ( -7410747, string );
    cout << string;

    return 0;
}

```

---

### Post by mosesaro on 2012-04-21
Wow thanks this is great. So the number obviously holds the number that was inputed what about *string can it just return a * value?

---

### Post by mosesaro on 2012-04-21
OK I got the second put ```
#include "iostream"
#include "cstring"
using namespace std;

void StrMask ( int number);

int main()
{
    StrMask (7410747);
    
    return 0;
}

void StrMask ( int number)
{
    if ( number > 0 )
    {
        int temp = number%10;
        
        if ( temp == 7 )
        {
            cout << "*";
        }
        else
        {
            cout << 0 + temp;
        }
        
        StrMask ( (number - temp)/10);
    }
    else
        
    {
        return ;
    }
}
```

thanks for your help greatly appreciated.

---

### Post by DaviesX on 2012-04-21
Sorry, I have something messed up, wait a minute, I will remedy the mistake in my previous post

---

### Post by mosesaro on 2012-04-21
I see it, thats the same problem I had before.

this seams to solve the problem but it won't work with void
return x % 10 + 10 * StrMask(x/10);

---

### Post by DaviesX on 2012-04-21
I just change my post after having my dinner :)

---

### Post by Vaphell on 2012-04-21
admins must be asleep because that sounds an awful lot like a homework.

---

### Post by mosesaro on 2012-04-21
Yes I need help with my homework so whats the big deal I have been at this problem for the whole day and I am also contributing I'm not just asking him to do everything. I could show you other code that i wrote I'm just having problems with this one thing.

---

### Post by DaviesX on 2012-04-21
Don't you thing this is a satire...
It comes out such a short code eventually
```

#include <iostream>
using namespace std;

void StrMask ( int number );

int main()
{
    StrMask ( 7410747 );
    return 0;
}

void StrMask ( int number )
{
    int temp;

    if ( number != 0 )
    {
        temp = number%10;
        StrMask ( (number - temp)/10 );
    }
    else
    {
        return ;
    }

    if ( temp >= 0 )
    {
        if ( temp != 7 )
            cout << (char)('0' + temp);
        else
            cout << '*';
    }
}

```

---

### Post by mosesaro on 2012-04-21
While I was waiting i was actually trying to implement an array that reverse the string at the end.

---

### Post by mosesaro on 2012-04-21
what does (char) do

---

### Post by DaviesX on 2012-04-21
Force to change the right operand to type 'char'

---

### Post by mosesaro on 2012-04-21
so it prints from the right?

---

### Post by DaviesX on 2012-04-21
Yeah, when backtracking

---

### Post by DaviesX on 2012-04-21
Sorry for my being delay
Here is the version for negative number :)

```

#include <iostream>
using namespace std;

void StrMask ( int number );

int main()
{
    StrMask ( -7410747 );
    return 0;
}

void StrMask ( int number )
{
    int temp;

    if ( number > 0 )
    {
        temp = number%10;
        StrMask ( (number - temp)/10 );
    }
    else if ( number < 0 )
    {
        cout << '-';
        StrMask ( -number );
    }
    else
    {
        return ;
    }

    if ( temp != 7 )
        cout << (char)('0' + temp);
    else
        cout << '*';
}

```

---

### Post by mosesaro on 2012-04-21
Thank you for your help very much. I actually could do the next part now

---

### Post by mosesaro on 2012-04-21
Can you just clarify a bit more what char does I am having trouble understanding it.

---

### Post by DaviesX on 2012-04-21
You don't have to use (char), just if you want the function to generate a real string. You can actually do like this
```

#include <iostream>
using namespace std;

void StrMask ( int number );

int main()
{
    StrMask ( -7410747 );
    return 0;
}

void StrMask ( int number )
{
    int temp = -1;

    if ( number > 0 )
    {
        temp = number%10;
        StrMask ( (number - temp)/10 );
    }
    else if ( number < 0 )
    {
        cout << '-';
        StrMask ( -number );
    }
    else
    {
        return ;
    }

    if ( temp >= 0 )
    {
        if ( temp != 7 )
        {
            cout << temp;
        }
        else
        {
            cout << '*';
        }
    }
}

```

I'm just learning c language, so I can't help making a bunch of bug...

---

### Post by mosesaro on 2012-04-22
thank you once again

---

### Post by DaviesX on 2012-04-22
> **mosesaro said:**
> thank you once again

Because you get more beans from it, lol ;)

---

### Post by Vaphell on 2012-04-22
> **mosesaro said:**
> Yes I need help with my homework so whats the big deal I have been at this problem for the whole day and I am also contributing I'm not just asking him to do everything. I could show you other code that i wrote I'm just having problems with this one thing.

and this is what exactly you should do. The deal is that doing someone else's homework is forbidden here, that is the forum policy.
Post your attempt, ask for hints, clarifications, pointing out the flaws. Nobody knows what you tried, nobody knows what your train of thought was and that's all that matters in the learning process. You got a fully working program on a silver platter.

You will never learn if you will get working solutions with no effort. Yes, you can read the code and think that you more or less understand what happens in it, but rest assured - you will be unable to whip up anything resembling a working program even if given very similar assignment. 'Understanding' and being able to effortlessly recreate steps taken are two entirely different things. I know, i've been there and i got to really understand programming few years later after my classes.
Knowledge is best absorbed when it's your sweat flowing and your forehead bashing the table out of frustration, not someone else's.

---

