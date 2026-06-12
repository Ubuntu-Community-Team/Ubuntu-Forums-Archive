---
title: "[SOLVED] ‘not’ undeclared, WTF!?"
date: 2008-12-02
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-02
Why I get this error?
> 
stuff.c:40: error: ‘not’ undeclared (first use in this function)

[COLOR="Navy"]not[/COLOR] does not exist!? Huh? How can I fix this?

And also, why don't [COLOR="Navy"]and[/COLOR] & [COLOR="Navy"]xor[/COLOR] work either?

I have to use && and ^, why? Can't I use the words? That would make code more readable.

---

### Post by FaresH on 2008-12-02
What language are you using ? 

If its c and c++, not is !

example :

```

isTrue = true;

if( isTrue )
     // What ever
}

```
is similar to 


```

isTrue=false;

if( !(isTrue) ){
    // What ever
}


```

---

### Post by crazyfuturamanoob on 2008-12-02
Always forgot, it's C.

But why Scite highlights NOT, AND & XOR and some other stuff when they don't exist?

---

### Post by nvteighen on 2008-12-02
Well, why don't you try using a macro:
```

#define not !

```

This should work for most cases, I guess.

---

### Post by gvoima on 2008-12-02
> **crazyfuturamanoob said:**
> Always forgot, it's C.

But why Scite highlights NOT, AND & XOR and some other stuff when they don't exist?

If you have C syntax highlighting enabled, it should not highlight not, and or xor?

---

### Post by crazyfuturamanoob on 2008-12-02
> **gvoima said:**
> If you have C syntax highlighting enabled, it should not highlight not, and or xor?

Scite highlights these things, but they aren't declared automatically:
[list]
[*]not
[*]xor
[*]and
[*]or
[*]false
[*]true
[/list]
And probably some others too but I'm not sure if I remembered everything.

---

### Post by Paul Miller on 2008-12-02
I'd like to suggest that you use ! rather than the word "not," when writing C code.  Sure, you can do 
```

#define not !

```
but that's bad practice, and it's going to end up making the code *less* readable to anyone with even a passing familiarity with C.  So, just don't do it.

As for why Scite wants to highlight those things, I don't have a clue.

---

### Post by jespdj on 2008-12-02
> **crazyfuturamanoob said:**
> Scite highlights these things, but they aren't declared automatically:
not, xor, and, or: These are not keywords in C nor are they standard functions or macros. Just because Scite highlights these things, doesn't mean they exist.

I don't use Scite, but is it maybe highlighting for a different programming language than C? Look if Scite is set correctly.

---

### Post by mike_g on 2008-12-02
It may be because not and xor are reserved words in C++:
[http://cs.stmarys.ca/~porter/csc/ref/cpp_keywords.html](http://cs.stmarys.ca/~porter/csc/ref/cpp_keywords.html)
So, if you want your code to be usable by C++ progs you might want to avoid using these words as identifiers.

---

### Post by jimi_hendrix on 2008-12-02
my little 2 cents...

just a reminder for the future in C bool is not a type...you have to include bool.h and yes you must use && and ||...

---

### Post by crazyfuturamanoob on 2008-12-03
> **jespdj said:**
> not, xor, and, or: These are not keywords in C nor are they standard functions or macros. Just because Scite highlights these things, doesn't mean they exist.

I don't use Scite, but is it maybe highlighting for a different programming language than C? Look if Scite is set correctly.

My scite highlight option is "C/C++". And as other ppl have mentioned, maybe those words are reserved in C++?

---

