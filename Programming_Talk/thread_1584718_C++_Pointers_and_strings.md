---
title: "C++: Pointers and strings"
date: 2010-09-29
forum: Programming Talk
---

### Post by TeoBigusGeekus on 2010-09-29
A couple of noobie questions about pointers and strings.

[SIZE="4"](1)[/SIZE]
I've read that it's a bad idea to dereference an uninitialised pointer as it would lead to a segmentation fault.
```
int* c;
*c=10;
```
The pointer, having not been initialised, points to a random place in memory, in which I place a value that could lead to catastrophic results.
My question is why this code
```
char* str;
str="hello everybody";
```
or
```
const char* str;
str="hello everybody";
```
doesn't lead to a segmentation fault as well. Isn't this the same case as before? A pointer, which points randomly somewhere in memory, that gets a value after it's declared.


[SIZE="4"](2)[/SIZE]
The code
```
char* str="hello everybody";
```
leads to the following warning from the compiler:
```
deprecated conversion from string constant to ‘char*’
```
I've read that string literals are treated as constants, so the correct code would be:
```
const char* str="hello everybody";
```
Somewhere on the internet, it was mentioned that this is C++'s way of not letting you change a string.
But why does this only happen with pointers?
The following code
```
char str[20]="hello everybody";
```
or
```
string str="hello everybody";
```
is perfectly accepted and I'm allowed to change the value of str later in the code.
Why does c++ "protect" pointer-strings and not array strings?

I apologise if my questions seem foolish - I'm trying to learn c++ from books and the internet.

---

### Post by schauerlich on 2010-09-29
A string can act as a char*, so you're just initializing the pointer, not dereferencing it.

```

char str[20] = "string" 

```

creates an array *on the stack* initialized with "string", whereas

```
char str* = "string"
```

creates an array containing "string" in the *read-only* area of memory (meaning it's hard coded into the binary of your application, and not writeable)

Your last example uses the std::string class, which is a whole 'nother thing entirely.

---

### Post by GeneralZod on 2010-09-29
I'll be quite informal about this; I'm sure people will be able to nitpick what I'm writing here, but it should at least give you at least broadly correct answers :)


> **TeoBigusGeekus said:**
> 
[SIZE="4"](1)[/SIZE]
I've read that it's a bad idea to dereference an uninitialised pointer as it would lead to a segmentation fault.
```
int* c;
*c=10;
```
The pointer, having not been initialised, points to a random place in memory, in which I place a value that could lead to catastrophic results.
My question is why this code
```
char* str;
str="hello everybody";
```
or
```
const char* str;
str="hello everybody";
```
doesn't lead to a segmentation fault as well. Isn't this the same case as before? A pointer, which points randomly somewhere in memory, that gets a value after it's declared.


No, it's a different case to your first example: in your first example, the segmentation fault occurred because you de-referenced an uninitialised pointer and put something into the memory it was pointing to.  In the second, no segmentation fault occurs: you are not de-referencing the pointer, and so you are not putting anything into the memory it points to.  In fact, you are setting str to point to some valid (but likely read-only) memory.

> 
[SIZE="4"](2)[/SIZE]
The code
```
char* str="hello everybody";
```
leads to the following warning from the compiler:
```
deprecated conversion from string constant to &#8216;char*&#8217;
```
I've read that string literals are treated as constants, so the correct code would be:
```
const char* str="hello everybody";
```
Somewhere on the internet, it was mentioned that this is C++'s way of not letting you change a string.
But why does this only happen with pointers?
The following code
```
char str[20]="hello everybody";
```
or
```
string str="hello everybody";
```
is perfectly accepted and I'm allowed to change the value of str later in the code.
Why does c++ "protect" pointer-strings and not array strings?


"hello everybody" is a *string literal* and different systems will store these in different ways - it would be perfectly permissible to store these in areas of memory that simply cannot be written to, for example.  Then

```

char* str="hello everybody";

```

would enable you to do e.g.

```

str[0] = 'a';

```

which would then attempt to overwrite the values in this read-only memory, with potentially crazy results!

In contrast, having this

```
char str[20]="hello everybody";
```

actually creates an array of 20 chars (on the stack, if it is in a function body), and *copies* the string literal "hello everybody" into this array.  Assuming that the array is created somewhere where it is safe to write (and the stack would usually qualify), then

```
str[0] = 'a';
```

would change the contents of the array, which is safe.

Similarly,

```
string str="hello everybody";
```

will create something like a char array somewhere writable (on the heap, most probably) and again just copy the contents of the string literal into this array.

---

### Post by TeoBigusGeekus on 2010-09-29
So, to see if I got this right,
```
const char* str="hello everybody";
```
hardcodes the string literal "hello everybody" to the program's memory (read only, therefore I must use const) and makes str point to it.

---

### Post by schauerlich on 2010-09-29
> **TeoBigusGeekus said:**
> So, to see if I got this right,
hardcodes the string literal "hello everybody" to the program's memory (read only, therefore I must use const) and makes str point to it.

yup.

---

### Post by Sockerdrickan on 2010-09-29
> **TeoBigusGeekus said:**
> So, to see if I got this right,
```
const char* str="hello everybody";
```hardcodes the string literal "hello everybody" to the program's memory (read only, therefore I must use const) and makes str point to it.
Yes

---

### Post by TeoBigusGeekus on 2010-09-29
Thanks everyone for your quick and enlightening answers!!!
I've got tons to learn...:P

---

### Post by SaintDanBert on 2010-09-29
Within the language "specification", when you write
```

      char *stuff;     [color=red]-5 points[/color]
      ...
      stuff = "lah dee dah";

```

The part in quotes already has the data type of **pointer to character**.

Students lose points for failure to initialize.

```

     char *stuff = 0;
     ...

```

This code initializes a pointer to NULL. Most modern compilers have special code for references to NULL-pointers.  A NULL-pointer is still a valid but worthless address within your process space. In contrast, if left without initialization, your pointer variable might contain any set of bits pointing to any place in system memory.  Both will result in a seg-fault error. Your environment (workstation vs. embedded) and compiler+runtime determine the consequences.

If you are troubled with pointer errors, check out Electric Fence
[ http://www.filetransit.com/view.php?id=83348 ]( http://www.filetransit.com/view.php?id=83348 ).

~~~ 0;-Dan

---

### Post by TeoBigusGeekus on 2010-09-29
> **SaintDanBert said:**
> Within the language "specification", when you write
```

      char *stuff;     [color=red]-5 points[/color]
      ...
      stuff = "lah dee dah";

```

The part in quotes already has the data type of **pointer to character**.

Students lose points for failure to initialize.

```

     char *stuff = 0;
     ...

```

This code initializes a pointer to NULL. Most modern compilers have special code for references to NULL-pointers.  A NULL-pointer is still a valid but worthless address within your process space. In contrast, if left without initialization, your pointer variable might contain any set of bits pointing to any place in system memory.  Both will result in a seg-fault error. Your environment (workstation vs. embedded) and compiler+runtime determine the consequences.

If you are troubled with pointer errors, check out Electric Fence
[ http://www.filetransit.com/view.php?id=83348 ]( http://www.filetransit.com/view.php?id=83348 ).

~~~ 0;-Dan

Thanks for the link Dan. Although I'm very far from creating massive code that needs outside help to spot mistakes, Electric Fence will come handy in the future.

---

### Post by worksofcraft on 2010-09-30
I'm glad I spotted this... I used to think I understood it... but now just trying to work with unicode strings I find...
```

static const gunichar Digits[] = L"0123456789";
// gives compile time error:
cs_num2.cpp:38: error: array must be initialized with a brace-enclosed initializer

```
bleh... really does look like C++ implementation of "wide strings" is even more useless than I thought :( I've gotta write it as:
```

static const gunichar Digits[] = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9' };

```

---

### Post by dwhitney67 on 2010-09-30
> **worksofcraft said:**
> I'm glad I spotted this... I used to think I understood it... but now just trying to work with unicode strings I find...
```

static const gunichar Digits[] = L"0123456789";
// gives compile time error:
cs_num2.cpp:38: error: array must be initialized with a brace-enclosed initializer

```
bleh... really does look like C++ implementation of "wide strings" is even more useless than I thought :( I've gotta write it as:
```

static const gunichar Digits[] = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9' };

```

WTH is a "gunichar"??

This works:
```

#include <cwchar>

int main()
{
   const wchar_t digits[] = L"0123456789";

   //...
}

```

---

### Post by worksofcraft on 2010-09-30
> **dwhitney67 said:**
> WTH is a "gunichar"??

This works:
```

#include <cwchar>

int main()
{
   const wchar_t digits[] = L"0123456789";

   //...
}

```

Sigh - so it does :shock:

However, following advice you gave me once before I'm actually trying to **NOT reinvent the wheel** this time and use proper software library [Glib Reference Manual for Unicode Manipulation]("http://library.gnome.org/devel/glib/unstable/glib-Unicode-Manipulation.html"). That works on: [I]typedef guint32 gunichar;
A type which can hold any UTF-32 or UCS-4 character code, also known as a Unicode code point.[/I]

---

