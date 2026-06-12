---
title: "gcc behaviour standard or chance?"
date: 2008-10-29
forum: Programming Talk
---

### Post by Sydius on 2008-10-29
When I run the following code, it seems that the data represented by "abcdefg" is only given one address in memory, even though it goes out of scope with each iteration of the loop (right?).  If my understanding is correct, a string literal is only made once in memory, no matter how many times it is used.  Is this standard-compliant or chance behavior?

[PHP]
#include <iostream>

int main(void)
{
    for (int i = 0; i < 7; i++) {
        const char *c = &"abcdefg"[i];
        std::cout << "Value: " << *c << " Address: " << (unsigned int)c << std::endl;
    }
}
[/PHP]

---

### Post by snova on 2008-10-29
I don't know if it's part of the standard, but GCC has to store it *somewhere*. (It's probably in the .data section.) Your variable may go out of scope, but the string is still at the same location.

---

### Post by Tony Flury on 2008-10-29
Since the string only appears once in the code, the compiler will only allocate it memory once, anything else would not be a sensible thing for the compiler to do.

Would be interested to see what it did if the same string literal appeared more than once in the same module - would it recognise that and optimise them into one string - to be honest i would hope so, but it might not.

---

### Post by Sydius on 2008-10-29
> **Tony Flury said:**
> Since the string only appears once in the code, the compiler will only allocate it memory once, anything else would not be a sensible thing for the compiler to do.

Would be interested to see what it did if the same string literal appeared more than once in the same module - would it recognise that and optimise them into one string - to be honest i would hope so, but it might not.

It does (in my version of GCC).  But is that dependable behavior? Or chance/optimization?

---

### Post by hod139 on 2008-10-29
From the C++ standard (2.13.4)"
> 
  1 A string literal is a sequence of characters (as defined in 2.13.2) surrounded by double quotes, optionally beginning with the letter L, as in "..." or L"...". A string literal that does not begin with L is an ordinary string literal, also referred to as a narrow string literal. An ordinary string literal has type &#8220;array of n const char&#8221; and static storage duration (3.7), where n is the size of the string as defined below, and is initialized with the given characters. A string literal that begins with L, such as L"asdf", is a wide string literal. A wide string literal has type &#8220;array of n const wchar_t&#8221; and has static storage duration, where n is the size of the string as defined below, and is initialized with the given characters. 

2 Whether all string literals are distinct (that is, are stored in nonoverlapping objects) is implementation-defined. The effect of attempting to modify a string literal is undefined.
This is standard behavior

---

### Post by Sydius on 2008-10-29
> Whether all string literals are distinct (that is, are stored in nonoverlapping objects) is implementation-defined. 

I read that as meaning that it is up to GCC whether or not the string literal is stored in one location or not?

I'm still left wondering if that string literal is a single string literal or if the fact that it goes out of scope means it is many.

---

### Post by Tony Flury on 2008-10-29
In your case since the actual string only appears once in your source code, then the compiler will almost certainly only store it once. It would be a brain dead compiler (and gcc isn't brain dead), to allocate it multiple times - for a start it would have to work out how many times it would go round the loop, to work out how many copies to allocate.

if the same string appears twice in the same source code file, then the standard says it is upto the compiler to decide if it allocates two strings in memory or one.

Bear in mind what goes out of scope each time round your loop is the pointer variable - that will point to part of the string literal but it is not the same as the string literal.

The other thing i would say is never never rely on an assumption of where the compiler may or may not store anything.

---

### Post by hod139 on 2008-10-29
> **Sydius said:**
> I read that as meaning that it is up to GCC whether or not the string literal is stored in one location or not?
You read this right, the compiler can choose to reuse a string literal or to statically allocate a new one.

Edit: Tony Flury beat me to it

---

### Post by snova on 2008-10-29
As far as I know, GCC only stores identical strings once.

---

### Post by Sydius on 2008-10-29
I'm more interested in the theory behind this.  Would every standard-compliant compiler have to treat that string literal as a single string literal, or it is just an obvious optimization?  What if the loop is unrolled by the compiler (does the standard docs talk about this?)?

---

### Post by snova on 2008-10-29
I'm pretty sure it's implementation defined, but I don't exactly have a copy of the standard...

As for optimization, that's definitely up to the compiler.

---

### Post by hod139 on 2008-10-29
Here is all of section 2.13.4 (the section on string literals) from the 2003 ISO C++ standard:
> 
2.13.4 String literals [lex.string]
string-literal:
          "s-char-sequence_opt"
          L"s-char-sequence_opt"
s-char-sequence:
          s-char
          s-char-sequence s-char
s-char:
          any member of the source character set except
                   the double-quote ", backslash \, or new-line character
     escape-sequence
     universal-character-name

1 A string literal is a sequence of characters (as defined in 2.13.2) surrounded by double quotes, optionally beginning with the letter L, as in "..." or L"...". A string literal that does not begin with L is an ordinary string literal, also referred to as a narrow string literal. An ordinary string literal has type &#8220;array of n const char&#8221; and static storage duration (3.7), where n is the size of the string as defined below, and is initialized with the given characters. A string literal that begins with L, such as L"asdf", is a wide string literal. A wide string literal has type &#8220;array of n const wchar_t&#8221; and has static storage duration, where n is the size of the string as defined below, and is initialized with the given characters.

2 Whether all string literals are distinct (that is, are stored in nonoverlapping objects) is implementation-defined. The effect of attempting to modify a string literal is undefined.

3 In translation phase 6 (2.1), adjacent narrow string literals are concatenated and adjacent wide string literals are concatenated. If a narrow string literal token is adjacent to a wide string literal token, the behavior is undefined. Characters in concatenated strings are kept distinct. [Example: "\xA" "B" contains the two characters &#8217;\xA&#8217; and &#8217;B&#8217; after concatenation (and not the single hexadecimal character &#8217;\xAB&#8217;). ]

4 After any necessary concatenation, in translation phase 7 (2.1), &#8217;\0&#8217; is appended to every string literal so that programs that scan a string can find its end.

5 Escape sequences and universal-character-names in string literals have the same meaning as in character literals (2.13.2), except that the single quote &#8217; is representable either by itself or by the escape sequence \&#8217;, and the double quote " shall be preceded by a \. In a narrow string literal, a universal-character-name may map to more than one char element due to multibyte encoding. The size of a wide string literal is the total
number of escape sequences, universal-character-names, and other characters, plus one for the terminating L&#8217;\0&#8217;. The size of a narrow string literal is the total number of escape sequences and other characters, plus at least one for the multibyte encoding of each universal-character-name, plus one for the terminating &#8217;\0&#8217;.
Points 1 and 2 are the only ones the concern your question, and from point 2 you can see that it is up to the compiler implementors on how to handle duplicate string literals.

---

### Post by Npl on 2008-10-29
> **Sydius said:**
> I'm more interested in the theory behind this.  Would every standard-compliant compiler have to treat that string literal as a single string literal, or it is just an obvious optimization?  What if the loop is unrolled by the compiler (does the standard docs talk about this?)?You dont define the Stringliteral in each iteration, but a pointer to it. With other words, the string itself is a global object and your code is equivalent to:
```
const char* g_string = "abcdefg";
char* ptr = &((g_string)[i]); // Which is further equal to:
// char* ptr = g_string + i;
```

If you want to instantiate a new string each time you need to write```
const char[] g_string = "abcdefg"; // creates a new copy each iteration
```

---

### Post by dribeas on 2008-10-30
Npl beat me by> **Sydius said:**
> I'm more interested in the theory behind this.  Would every standard-compliant compiler have to treat that string literal as a single string literal, or it is just an obvious optimization?  What if the loop is unrolled by the compiler (does the standard docs talk about this?)?

As pointed before, it is the const char* variable that goes out of scope (exemplified below). Now, string literals do not belong to any given scope, they are constant data not variables.

```

// Sample code: pointer goes out of scope, pointee does not:
char hello[6];
hello[0] = 'H'; hello[1] = 'e'; hello[2] = 'l';
hello[3] = 'l'; hello[4] = 'o'; hello[5] = 0;

for ( int i = 0; i != 10; ++i )
{
   const char *q = hello;
}

```

How many instances of hello are there? What is the scope of q? What is the scope of hello?

I hope this clears the fact that even if q goes in and out of scope, every time the processor starts the loop the 'possibly different' q points to the same memory location: hello.

As a side note, if instead of watching the address of the string you print the address of q, it might well be the case that every time the loop enters q is allocated in the same address (as it is free at that time).

Other people have pointed this out, but I cannot but insist: you should not depend on the address of a literal in your code. When comparing strings (literals or not) you must compare contents, not addresses.

---

