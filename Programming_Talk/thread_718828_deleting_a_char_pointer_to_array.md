---
title: "deleting a char pointer to array"
date: 2008-03-08
forum: Programming Talk
---

### Post by StOoZ on 2008-03-08
I get the following error while the 'delete' command is being processed:
"Segmentation fault (core dumped)"

the code:
> int main()
{
    char *uname = new char[50];
    uname = "hello";
    
    delete []uname;
    return 0;
}


any idea?
10x

---

### Post by mike_g on 2008-03-08
Strange. It doesent segfault here? (Vista & DevC++). 

Since you are coding in C++ you could try using C++ style strings. Maybe this will work for you:
```
#include <iostream>
using namespace std;

int main()
{
    string str;
    str="hello";
    cout << str << endl;
}
```
Edit: also theres an implicit return 0 in C++, so you don't need it.

---

### Post by PaulFr on 2008-03-08
```
char *uname = new char[50];
    uname = "hello";   **<--- uname points to a constant string and not to allocated memory**
    delete []uname;  **<--- you are trying to delete a constant string**
``` Perhaps you intended ```
strcpy(uname, "hello");
```

---

### Post by LaRoza on 2008-03-08
> **mike_g said:**
> 
Edit: also theres an implicit return 0 in C++, so you don't need it.

One should explicitly return it.

---

### Post by libwilliam on 2008-03-08
```
uname = "hello";
```

uname is a pointer. when this statement happens it is changing what uname is pointing at. In this case it is changing it to a const string literal. So delete doesn't know what is going on because it isn't pointing to the same memory.

Possible fixes are use array notation.

```
char uname[] = "hello";
```

this sets uname to be 'h' 'e' 'l' 'l' 'o' '0\'

Or if you want to use new, you could do this...

```
strncpy(uname, "hello", 5);
```

This actually copies "hello" into the memory location that uname already points to, so there is no problem.

Or you could use the string class like mike_g said.

---

### Post by smartbei on 2008-03-08
What you should keep in mind is that uname is not an array, it is a pointer. While they behave in a similar manner, not all of the rules that apply to one apply to the other. For example, you cannot increment an array:
```

char array[20];
array++; // << 'array' is not an lvalue

```

and you cannot delete/free it - it is allocated on the stack and not on the heap.

---

### Post by mike_g on 2008-03-08
[quote="LaRoza"]One should explicitly return it.[/quote]
Yeah, I got that wrong before here talking about C.

Apparently an implicit return 0 is part of the C++ and C99 standard.

Heres a reference:
[http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376)

Not that it really makes all that much of a difference.

---

### Post by LaRoza on 2008-03-08
> **mike_g said:**
> Yeah, I got that wrong before here talking about C.

Apparently an implicit return 0 is part of the C++ and C99 standard.

Heres a reference:
[http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376)

Not that it really makes all that much of a difference.

Thanks, that is a good article on it.

I do believe one shouldn't expect the compiler to do that, and explictly return what you want to be returned.

---

### Post by Jessehk on 2008-03-08
> **LaRoza said:**
> Thanks, that is a good article on it.

I do believe one shouldn't expect the compiler to do that, and explictly return what you want to be returned.

and *I* believe that is true when writing C89, not C++98. :)

---

### Post by Can+~ on 2008-03-08
> **mike_g said:**
> Yeah, I got that wrong before here talking about C.

Apparently an implicit return 0 is part of the C++ and C99 standard.

Heres a reference:
[http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376)

Not that it really makes all that much of a difference.

> >>> import this
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
**Explicit is better than implicit.**
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!

I know this is python, but I thought it would fit the subject.

---

### Post by LaRoza on 2008-03-08
> **Jessehk said:**
> and *I* believe that is true when writing C89, not C++98. :)

I think one should explicitly state what one wants, and not rely on such things. It is valid, as you say, but I wouldn't do it.

Can+~ got exactly what I was thinking about...

---

### Post by hod139 on 2008-03-08
> **StOoZ said:**
> I get the following error while the 'delete' command is being processed:<snip>

This question seems to be showing up with more frequency.  Here is a discussion on it we had not too long ago: [http://ubuntuforums.org/showthread.php?t=696643](http://ubuntuforums.org/showthread.php?t=696643)

---

