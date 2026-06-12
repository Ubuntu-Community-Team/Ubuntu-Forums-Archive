---
title: "C++ twisted logic"
date: 2010-09-14
forum: Programming Talk
---

### Post by kacper on 2010-09-14
I have this little code that doesn't work as it should. Perhaps it's just a logical error on my part. Any help would be appreciated.

```

cin >> yesno;

	// Shouldn't but does work
	if (yesno != 'y' && yesno != 'Y') { return 0; }

	// Should but doesn't work
	if (yesno != 'y' || yesno != 'Y') { return 0; }
```

---

### Post by James78 on 2010-09-14
Have you tried it this way?
```
cin >> yesno;

    // Shouldn't but does work
    if ((yesno != 'y') && (yesno != 'Y')) { return 0; }

    // Unknown if it works
    if ((yesno != ('y' || 'Y')) { return 0; }

    // Should but doesn't work
    if ((yesno != 'y') || (yesno != 'Y')) { return 0; }
```
P.S. Yes, the annoying logic error problem.. It gets confusing VERY fast. Had it happen to me many times, in many languages. :/

---

### Post by bouncingwilf on 2010-09-14
The first case should  always return false unless yesno  = y or Y ;
the second case will always return false because whatever character is input then conditions are met.


You may be better explicitly testing for y/Y

---

### Post by Some Penguin on 2010-09-14
Really?  Have you simply considered what those statements do if, say, "yesno" is 'b' or 'y'?


And since 'y' != 'Y', isn't the result of the second version obvious?  It can't be BOTH 'y' and 'Y', so one of those != has to be true...

---

### Post by bouncingwilf on 2010-09-14
I think setting up logic that tries to say (If something relatively complicated is  true) then  return false is potentially very confusing.


bouncingwilf

---

### Post by TheGreatmelfan on 2010-09-14
try using toupper?

char yesno;

cin>>yesno;

yesno = toupper(yesno);

if(yesno != 'Y')
return 0;

should work

---

### Post by TheGreatmelfan on 2010-09-14
forgot to mention when using toupper
use 
#include<cctype>

---

### Post by ssam on 2010-09-14
be careful with negations and logic
```

    NOT (P OR Q) = (NOT P) AND (NOT Q)
    NOT (P AND Q) = (NOT P) OR (NOT Q)

```
[http://en.wikipedia.org/wiki/De_Morgan%27s_laws](http://en.wikipedia.org/wiki/De_Morgan%27s_laws)

---

### Post by Rany Albeg on 2010-09-14
```
if (yesno == 'y' || yesno == 'Y')
{
        // user said YES.
}
else
{
        // user did not say YES.
}
```

---

### Post by nvteighen on 2010-09-14
Uf... Since when are strings compared that way? std::cin returns a string, not a character, so you can't use ==. Either you use strcmp() (but that's actually C) or you use std::string::compare, which is the C++ method (using std::string, of course).

```

#include <iostream>
#include <string>

int main(void)
{
    std::string yesno; // DON'T use char * in C++!
    std::cin >> yesno;

    // std::string::compare returns 0 on equality
    if((yesno.compare("y") == 0) || (yesno.compare("Y") == 0))
        std::cout << "Yup!" << std::endl;
    else
        std::cout << "Nope!" << std::endl;

    return 0;
}

```

---

### Post by worksofcraft on 2010-09-14
Well, I think the problem is mostly that you are expressing the logic in a confusing way. Also don't be afraid to put in brackets that are redundant if they make the code more clear. Perhaps re-write it as follows... 

```

bool get_yesno() {
	char yesno;
	cin >> yesno;
	return (toupper(yesno) == 'Y');
}

```

Keep in mind that you might want to modify it one day to check if an N was entered when it isn't a Y and if not to prompt the user again asking for either a Y or an N response. Then also one day you might have to translate it to a foreign language that uses extended characters and who don't even have a Y or N on their keyboard :shock:

---

### Post by nvteighen on 2010-09-15
> **worksofcraft said:**
> Well, I think the problem is mostly that you are expressing the logic in a confusing way. Also don't be afraid to put in brackets that are redundant if they make the code more clear. Perhaps re-write it as follows... 

```

bool get_yesno() {
	char yesno;
	cin >> yesno;
	return (toupper(yesno) == 'Y');
}

```

Oh. std::cin works with chars too? I didn't know that... well, I'm not quite a C++ programmer either :P

---

### Post by manzdagratiano on 2010-09-15
> **nvteighen said:**
> Uf... Since when are strings compared that way? std::cin returns a string, not a character, so you can't use ==. Either you use strcmp() (but that's actually C) or you use std::string::compare, which is the C++ method (using std::string, of course).


char characters can always be compared using the "==" or "!=" operator.

The way the code is set up, the first line will return 0 if and only if neither 'y' nor 'Y' was entered by the user; it is equivalent to the NOR condition, which is the `neither nor ' case. The second line will always return 0 - even if 'y' or 'Y' or anything else at all was entered by the user, since one of the two conditions, or both, will always be true. It is equivalent to the NAND condition, which is not a 'neither nor' case. Hence the code does work as it should, and the first line is indeed the correct one - but that also depends on what you were asking for, which you never specified in your post.

---

### Post by kacper on 2010-09-21
> **manzdagratiano said:**
> char characters can always be compared using the "==" or "!=" operator.

The way the code is set up, the first line will return 0 if and only if neither 'y' nor 'Y' was entered by the user; it is equivalent to the NOR condition, which is the `neither nor ' case. The second line will always return 0 - even if 'y' or 'Y' or anything else at all was entered by the user, since one of the two conditions, or both, will always be true. It is equivalent to the NAND condition, which is not a 'neither nor' case. Hence the code does work as it should, and the first line is indeed the correct one - but that also depends on what you were asking for, which you never specified in your post.

Looking at ```
if (yesno != 'y' && yesno != 'Y') { return 0; }
``` to me yesno can't be y and Y at the same time.

---

### Post by dwhitney67 on 2010-09-21
> **kacper said:**
> Looking at ```
if (yesno != 'y' && yesno != 'Y') { return 0; }
``` to me yesno can't be y and Y at the same time.

That's correct.  'yesno' will only ever hold one value; whether this be 'y', 'Y', or some other character depends on what is inputted by the operator running the application.

Btw, the AND table for two values, A and B, where Y is the result is:
```

A * B     Y
------------
F   F  |  F
F   T  |  F
T   F  |  F
T   T  |  T

```

Note that in C or C++ (and with many other similar languages), when the first expression of an AND statement is evaluated to FALSE, the second expression is not evaluated (the reason is that it is moot).  A FALSE value ANDed with any other value is always FALSE.

The OR table for two values, A and B, where Y is the result is:
```

A + B     Y
------------
F   F  |  F
F   T  |  T
T   F  |  T
T   T  |  T

```
Here, when two expressions are ORed together, if either expression evaluates to TRUE, then the result is TRUE.  Thus if the first expression evaluates to TRUE, there is no need to evaluate the second expression.  If the first expression is evaluated to be FALSE, then the second expression is evaluated; depending on its value, the overall result may be TRUE or FALSE.

If you have the time, Google for information on "Discrete Mathematics" to give you better insight in logic expressions; or just take a basic h/w class.  :-)

---

### Post by James78 on 2010-09-24
> **dwhitney67 said:**
> Note that in C or C++ (and with many other similar languages),** when the first expression of an AND statement is evaluated to FALSE, the second expression is not evaluated (the reason is that it is moot).**  A FALSE value ANDed with any other value is always FALSE.
That's a very good little piece of information there. Thanks for putting together that post. ;)

---

### Post by kacper on 2010-09-27
> Note that in C or C++ (and with many other similar languages), when the first expression of an AND statement is evaluated to FALSE, the second expression is not evaluated (the reason is that it is moot). A FALSE value ANDed with any other value is always FALSE.

Is this statment also true for PHP? If not so that explains all this confusion. :)

---

### Post by nvteighen on 2010-09-27
> **kacper said:**
> Is this statment also true for PHP? If not so that explains all this confusion. :)

This is an interesting topic... how this evaluation rules interact with imperative programming... 

```

; SLIME 2010-07-21
CL-USER> (defparameter a 8)
A
CL-USER> (defparameter b 6)
B
CL-USER> (and (setf a nil) ; Returns NIL = FALSE
              (setf b 7))
NIL
CL-USER> b
6
CL-USER> 

```

So, variable b hasn't changed... because there's something nasty about boolean operations and setf in Common Lisp (they're macros) but in MIT/GNU Scheme... where booleans and set! are all evaluated in order because all are functions (not macros):
```

MIT/GNU Scheme running under GNU/Linux
Type `^C' (control-C) followed by `H' to obtain information about interrupts.

Copyright (C) 2010 Massachusetts Institute of Technology
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Image saved on Wednesday March 10, 2010 at 2:10:10 AM
  Release 9.0.1 || Microcode 15.1 || Runtime 15.7 || SF 4.41 || LIAR/i386 4.118
  Edwin 3.116

1 ]=> (define a 7)

;Value: a

1 ]=> (define b 8)

;Value: b

1 ]=> (and (set! a #f) (set! b 5))

;Value: 8

1 ]=> a

;Value: #f

1 ]=> b

;Value: 5

1 ]=> 

```

So, in MIT/GNU Scheme you have to assume that no matter how the and turns out, all arguments will be evaluated and side-effects will be performed...

I wonder what languages have which behaivor regarding this.

---

### Post by julio_cortez on 2010-09-27
> **nvteighen said:**
> So, in MIT/GNU Scheme you have to assume that no matter how the and turns out, all arguments will be evaluated and side-effects will be performed...I can see a sense under the C++ behaviour: if I had to evaluate "if A happens and also B happens, then do C" in real life, if A doesn't happen I won't care that much about B happening or not.
*But it's different if I'm told "do A and B and see if they're true". In that case, if I'm aware that some side-effect could come from doing B, I'll do it anyway.*

Of course we humans have common sense to behave differently if we're told "watch if A and B happen, if both do then do C" (so we can avoid to care about B, if A is false) or "perform A and B and see if both give the expected result, and if so do C" (so we'll do B anyway even if A is false).
*And programming languages aren't usually sensible enough to do so. It's just code, it can't know whether there will be side-effects or not..*

They're 2 different situations that have little to do with each other in my opinion..

---

### Post by worksofcraft on 2010-09-27
I lurked on the discussion here with great interest and what I want to say now is as follows:

In the Prolog language we can really exploit the boolean expression "short circuit" to make our programs do what we want them to. I was very impressed and delighted to be able to use similar techniques in C/C++

It's quite neat once you get use to thinking that way! Don't think like/dislike.. think how can I use this to my advantage? ;)

p.s. If you ever see any of my code don't be surprised to find lots of "bool" functions that called from rather long if statements that just print an error message when they evaluate as true :shock:

---

### Post by lisati on 2010-09-27
Surely the answer is to be aware of possible side effects, and write your code in such a way that either avoids them or makes use of them as appropriate.

---

### Post by ssam on 2010-09-27
the short circuiting is sometimes used in languages like bash or perl to exit when errors occur.
```

command || exit

```
will exit the script if command fails. for example
```

wget $FOO || exit

```
will quit if the download fails

and the other way around. if you are debugging code you might be repeatedly building and running. you could do
```

gcc -o foo foo.c && ./foo

```
that will compile it, and only run it if the compile was successful.

---

