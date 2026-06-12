---
title: "strlen and arrays in C"
date: 2008-11-02
forum: Programming Talk
---

### Post by swappo1 on 2008-11-02
Hello,

I have an array of characters that I am printing using pointers and everything works okay.  When I change the array to integer type, I get an error.
[PHP]#include <stdio.h>
#include <string.h>

int main(void)
{
	char x[11]= {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
	int i=0;
	
	while(i<strlen(x))		
		{
		printf("%d\n", *(x+i));
		i++;
		}
	printf("\n");
	return(0);
}[/PHP]
If I change char x[11]... to int x[11]... I get the following error.
> pointer_incrementing2.c:10: warning: passing argument 1 of ‘strlen’ from incompatible pointer type

I am assuming strlen() only works with characters.  Is there a function that will work for integers?  I am not sure how to get this to work with an integer array.  Thanks

---

### Post by ad_267 on 2008-11-02
strlen only works for strings. From the strlen definition:
> Syntax:
#include <string.h>
size_t strlen( char *str );

Description:
The strlen() function returns the length of str (determined by the number of characters before null termination). 

No there isn't a way to get the length of an integer array. You need to keep track of that yourself. You've hardcoded 11 into that example already, and if you are using dynamic allocation you should know how big the array is.

---

### Post by swappo1 on 2008-11-02
> No there isn't a way to get the length of an integer array. You need to keep track of that yourself. You've hardcoded 11 into that example already, and if you are using dynamic allocation you should know how big the array is.
Okay, thanks.  I'll look into dynamic allocation.  This was something I put together while learning how to use pointers.  I just thought there might be a simple way to track the number of elements like strlen().

---

### Post by mdurham on 2008-11-03
This might do it?

```

int main(void)
{
    char x[]= {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};	// add as many numbers as you like to x[]
    int i;
    
    for(i = 0; i < sizeof(x) / sizeof(x[0]); ++i)       
        {
        printf("%d\n", x[i]);
        }
    printf("\n");
    return(0);
}
```

---

### Post by dribeas on 2008-11-03
> **mdurham said:**
> This might do it?

```

int main(void)
{
    char x[]= {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};	// add as many numbers as you like to x[]
    int i;
    
    for(i = 0; i < sizeof(x) / sizeof(x[0]); ++i)       
        {
        printf("%d\n", x[i]);
        }
    printf("\n");
    return(0);
}
```

In most cases you want to keep the size around. While your code does exactly what you want, if you use x as a parameter to another function (receiving a char[]) the function cannot use that mechanism to retrieve the real size of the array. Also it won't work for dynamically allocated memory. In both cases, sizeof() will return the size of the pointer (divided by the size of the element), not the size of the pointed data.

---

### Post by cl333r on 2008-11-03
> **swappo1 said:**
> Hello,

I have an array of characters that I am printing using pointers and everything works okay.  When I change the array to integer type, I get an error.
[PHP]#include <stdio.h>
#include <string.h>

int main(void)
{
	char x[11]= {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
	int i=0;
	
	while(i<strlen(x))		
		{
		printf("%d\n", *(x+i));
		i++;
		}
	printf("\n");
	return(0);
}[/PHP]
If I change char x[11]... to int x[11]... I get the following error.

I am assuming strlen() only works with characters.  Is there a function that will work for integers?  I am not sure how to get this to work with an integer array.  Thanks

What's more interesting is that strlen doesn't work fine with non-english characters, such as Russian or Japanese. i.e. "&#1057;&#1090;&#1088;&#1072;&#1085;&#1072;" has 6 characters but strlen reports 12, which will result in weird behavior when trying to port it to some other language.

---

### Post by Nemooo on 2008-11-03
Another thing to remember when using loops, is that you don't want your condition calculated each time unless it's necessary. In your example your calculating strlen() each loop:

[php]for(i = 0; i < strlen(x); i++){
    /* Do something */
}[/php]

There's no reason to calculate strlen() each time. Instead use a var to hold the value:

[php]size_t len_str = strlen(x);

for(i = 0; i < len_str(x); i++){
    /* Do something */
}[/php]

---

### Post by dribeas on 2008-11-03
> **cl333r said:**
> What's more interesting is that strlen doesn't work fine with non-english characters, such as Russian or Japanese. i.e. "&#1057;&#1090;&#1088;&#1072;&#1085;&#1072;" has 6 characters but strlen reports 12, which will result in weird behavior when trying to port it to some other language.

strlen calculates the number of one-byte characters before the \0. If you are using multibyte characters then it will report twice the size (each real char is represented by two bytes). If you are using a C99 compliant compiler you can use wcslen, equivalent to strlen for wide character strings.

---

### Post by cl333r on 2008-11-03
> **dribeas said:**
> strlen calculates the number of one-byte characters before the \0. If you are using multibyte characters then it will report twice the size (each real char is represented by two bytes). If you are using a C99 compliant compiler you can use wcslen, equivalent to strlen for wide character strings.

Exactly, which is why I posted about strlen not working fine with non-english characters to warn the guy.
I wish utf8 preexisted C, we wouldn't have the issues we have today, which are not obvious to people who don't (often) deal with foreign languages.
I'm learning C, and I love it, but coming from Java I'm amazed how far one has to go to achieve simple things that by 2008 should be for granted. Part of them are supported by C99 but unfortunately not by gcc yet. In this regard I agree with Linus (Torvalds) who once said that gcc is facing too little or no competition from other open source compilers (Is there any viable open source alternative? I doubt).

---

### Post by nvteighen on 2008-11-03
> **cl333r said:**
> Exactly, which is why I posted about strlen not working fine with non-english characters to warn the guy.
I wish utf8 preexisted C, we wouldn't have the issues we have today, which are not obvious to people who don't (often) deal with foreign languages.
I'm learning C, and I love it, but coming from Java I'm amazed how far one has to go to achieve simple things that by 2008 should be for granted. Part of them are supported by C99 but unfortunately not by gcc yet. In this regard I agree with Linus (Torvalds) who once said that gcc is facing too little or no competition from other open source compilers (Is there any viable open source alternative? I doubt).
You have a valid complain, but you're missing what's C's point.

Yeah, it would be nice to be able to do simple things in C in a more simple way ;), but the issue is that we **need** a low-level language like C is to be able to have something like Java or other high-level languages. If we move C to a higher-level, then, how do we implement C?

Yes, someone will argue there is C++, but again, it suffers the same issues as C and if you want dynamic strings, you have to use the STL, which is not built-in the language, but just a standard library.

---

### Post by dribeas on 2008-11-03
> **nvteighen said:**
> Yes, someone will argue there is C++, but again, it suffers the same issues as C and if you want dynamic strings, you have to use the STL, which is not built-in the language, but just a standard library.

I wonder what the definition of built-in is for a language. It is part of the standard, just as much as Java API (that defines String) is part of its own standard, or .NET libs. 

The fact is that the standard body has (and still is) trying to avoid adding unneeded features to the language, and everything that can be added as a standard library is done in that way. On the other hand, small changes to the language are added as to facilitate the implementation of those libs.

---

### Post by nvteighen on 2008-11-03
> **dribeas said:**
> I wonder what the definition of built-in is for a language. It is part of the standard, just as much as Java API (that defines String) is part of its own standard, or .NET libs. 

The fact is that the standard body has (and still is) trying to avoid adding unneeded features to the language, and everything that can be added as a standard library is done in that way. On the other hand, small changes to the language are added as to facilitate the implementation of those libs.
Good question. Built-in, for me, means whatever it's not included in an external library. So, in C, e.g. printf() is not built-in, because you need to link to the Std. Lib. to get it work. But, the way strings work in C is part of the built-in array support.

---

### Post by dribeas on 2008-11-03
> **nvteighen said:**
> Good question. Built-in, for me, means whatever it's not included in an external library. So, in C, e.g. printf() is not built-in, because you need to link to the Std. Lib. to get it work. But, the way strings work in C is part of the built-in array support.

Interesting definition, but I don't quite agree. To me the difference is whether it is part of the standard and all compilers/interpreters must support it.

Where is the limit? Linking against a lib? Including the header? Importing a module? Is the math library part of C? Is it C++? You know Java, is java.util.Vector part of Java?

---

### Post by nvteighen on 2008-11-04
> **dribeas said:**
> Interesting definition, but I don't quite agree. To me the difference is whether it is part of the standard and all compilers/interpreters must support it.

Where is the limit? Linking against a lib? Including the header? Importing a module? Is the math library part of C? Is it C++? You know Java, is java.util.Vector part of Java?
I don't know Java, so I can't tell you :)

But, what's Java (or whatever language)? The system of semantics and syntax? This undoubtly which allows java.util.Vector to exist and be part of a Java program.

I admit the limit is not clear; actually, I'm currently working on this topic for a little research on artificial languages (kind an assignment, but not that small either... maybe a "long paper"?). It's not only appliable to programming languages, but also artificial ones in general... What's Esperanto? It's vocabulary or the "16 Rules" of the *Fundamento de la Internacia Lingvo*? Yes, the rules give the vocabulary the chance to exist... but you can't have just empty rules without anything to use them...

Curiously, natural languages seem to not have that issue... you can't think of having English rules in pure form separate from its vocabulary. Both sides modify eachother...

But anyway, these are intuitions and may be, of course, discussable.

---

### Post by dribeas on 2008-11-04
> **nvteighen said:**
> I don't know Java, so I can't tell you :)


Oh, I thought I had read you in another post talking about Java. Anyway, it was a trick question, but I can take it back to C++, even if it must be the yet-to-be-approved standard.

The question on java.util.Vector (that is part of the library) can be mapped to the concept of Range. Concepts are a new addition to the language, they allow you to define requirements on data types to be handled by a template. Now, Range is one of those set of requirements, and it will be provided in STL.

The problem with dividing STL appart from the language is that the line can be impossible to delimit. There is this new 'for each' language feature:

```

// example based in one from [wikipedia]("http://en.wikipedia.org/wiki/C%2B%2B0x")
std::vector< int > v; // + fill in vector
for ( int& x : v )
{
   x *= 2;
}

```

Now, clearly that for defines a new language construct, new syntactic rules. But it is based on (uses and requires) a concept that is part of the STL. Both cannot be split apart from the other, where's the division?

In Java this is past, and not future. The for each construct is similar in syntax to the above code, and it is based in the Collection<> generics interface, that is part of the API. That was the tricky part of the question, or it would have been for a Java programmer anyway.

---

### Post by nvteighen on 2008-11-05
> **dribeas said:**
> Oh, I thought I had read you in another post talking about Java. Anyway, it was a trick question, but I can take it back to C++, even if it must be the yet-to-be-approved standard.

The question on java.util.Vector (that is part of the library) can be mapped to the concept of Range. Concepts are a new addition to the language, they allow you to define requirements on data types to be handled by a template. Now, Range is one of those set of requirements, and it will be provided in STL.

The problem with dividing STL appart from the language is that the line can be impossible to delimit. There is this new 'for each' language feature:

```

// example based in one from [wikipedia]("http://en.wikipedia.org/wiki/C%2B%2B0x")
std::vector< int > v; // + fill in vector
for ( int& x : v )
{
   x *= 2;
}

```

Now, clearly that for defines a new language construct, new syntactic rules. But it is based on (uses and requires) a concept that is part of the STL. Both cannot be split apart from the other, where's the division?

In Java this is past, and not future. The for each construct is similar in syntax to the above code, and it is based in the Collection<> generics interface, that is part of the API. That was the tricky part of the question, or it would have been for a Java programmer anyway.
Ok, I see. 

That's a nice example... Well, yes: it's defining a new syntax and also a new meaning for 'for'. I guess that's implemented by some macro, as, if I'm not wrong (and if I am, please correct me) the STL is a library you link to and it's not "built-in" the compiler. If that's correct, we face the problem of macros, which have lead me to real headaches... curiously, Lisp macros are the easiest to deal with linguistically: you can treat them as chomskian transformations because they preserve syntax and are written in exactly the same language used for code. C or C++ macros, instead, are in a different language... a kind of meta-language but distinct to the language it refers to... (Meta-English is English itself, but "Meta-C" is not C)

So, the issue is whether we consider macros to be part of their language or not. If yes, then the STL example would be just a transformation of a deep structure (in Chomskian terms) and therefore, it's not even a new feature in the language nor new syntax, but the same syntax "hidden".

But, if we consider the macro-language to be a different one to the programming language, then it would mean that macro-languages are able to create new languages and the STL could be considered a built-in part of something we could call "C++/STL" (like "C/GLib", where there's a radical shift on semantics that renders C into a OOP language, for example).

It's an interesting discussion. And again, still too confuse to give an exact conclusion. Also, there seems to be really little and bad bibliography and research on artificial (and therefore, programming) languages in general. A pity, actually.

---

### Post by dribeas on 2008-11-06
> **nvteighen said:**
> That's a nice example... Well, yes: it's defining a new syntax and also a new meaning for 'for'. I guess that's implemented by some macro, as, if I'm not wrong (and if I am, please correct me) the STL is a library you link to and it's not "built-in" the compiler. If that's correct, we face the problem of macros, which have lead me to real headaches...

STL is not built-in the compiler, but the compiler can depend on it existing. Neither this functionality nor template that most people see as glorified macro system are really implemented with macros. Incidentally, STL is a header only library, meaning that you don't have to link your executable with it, the templates ( STL, the T is for template ) are compiled together with user code.

Macros are known to be a source of trouble and the language tries to get away from them while keeping backwards compatibility. There are, anyways, some things that cannot be implemented without a macro system. I am thinking on the boost preprocessor libraries, for example, that generate compilable code for the user.

As most of your discussion is based on templates and the STL being based on macros, I will not discuss it point by point. On the other hand, I will try to make clear that templates are nothing like macros and cannot be implemented just with macros.

Template specializations

Whether [complete]("http://en.wikipedia.org/wiki/Template_specialization#Template_specialization") or [partial]("http://en.wikipedia.org/wiki/Partial_template_specialization") template specializations allow the user to define different implementation details. The easier example, whether a good one or not, is std::vector<T> template. It has a generic implementation used for any data type, and an specific specialization for bool where instead of storing data in a heap allocated array of T it compacts the bools so that each value takes just one bit.

SFINAE

[SFINAE]("http://en.wikipedia.org/wiki/SFINAE") means that if the compiler instantiates a template and it fails it is not a compilation error. Only after all possible template instantiations have failed the compiler will give up and a compilation error will be triggered.

The combination of both functionalities (none of which can be implemented on top of a macro system) allows the STL, or any other template library to have different implementations depending on the type used as argument. As an example, std::advance (move an iterator a number of positions) will execute in constant time for random access iterators ( iterator + constant is implemented for those) while it takes linear time for bidirectional iterators (only increment/decrement operators are defined).

Other differences

Templates play fair with the name and type systems. Templates belong to the namespace where they were defined as any other regular data type. Macros, on the other hand are processed by the precompiler that has no notion of namespaces, and populate all possible namespaces, and worse, even places where types are not allowed.

> **nvteighen said:**
> It's an interesting discussion. And again, still too confuse to give an exact conclusion. Also, there seems to be really little and bad bibliography and research on artificial (and therefore, programming) languages in general. A pity, actually.

That is interesting if you are studying languages. A whole field to study and publish papers :)

It is a pity that some interesting conversations end up in the second to third page of other posts.

---

### Post by nvteighen on 2008-11-06
> **dribeas said:**
> STL is not built-in the compiler, but the compiler can depend on it existing. Neither this functionality nor template that most people see as glorified macro system are really implemented with macros. Incidentally, STL is a header only library, meaning that you don't have to link your executable with it, the templates ( STL, the T is for template ) are compiled together with user code.

Thanks for clariying this to me. I've looked at the header files and yes, no macros. So, according with my definition in the post above, STL would not be part of the language, but just something coded in C++ that's widespread in use.

There we get into an interesting question: Does usage define what's part of the language or not? Vectors in C++ or printf() in C are not "in" the compiler... though there's almost no C code without #include <stdio.h> (refer to Hackles: [http://hackles.org/cgi-bin/archives.pl?request=315](http://hackles.org/cgi-bin/archives.pl?request=315)). And moreover, those are considered standard of their respective languages... Is it the standard which defines what the programming language is? And what about those languages without standard?

> 
Templates play fair with the name and type systems. Templates belong to the namespace where they were defined as any other regular data type. Macros, on the other hand are processed by the precompiler that has no notion of namespaces, and populate all possible namespaces, and worse, even places where types are not allowed.

That's mainly because templates are written in the same language as the code they'll be applied and macros, not. That obviously leads to "safer" code... but that's not only what happens. Templates exist because the compiler allows you to have them and, because templates are C++ code, they will be restricted by C++ syntax and semantic rules. Therefore, you get a meta-language equal to the target-language! Of course, you cannot compare this embryonic meta-language with Lisp's macro system, which is based on the ability of symbolic analysis (the symbol referring to a Lisp object is also a Lisp object itself) and therefore, everything is subceptible of metalinguistic analysis.

> 
It is a pity that some interesting conversations end up in the second to third page of other posts.

Well, this is a Programming Forum... and even if I believe that programmers are good intuitive linguists, I can understand that these discussions aren't the most relevant ones in this place...

---

### Post by mooolen on 2011-12-07
You can use ```
sizeof(x)/sizeof(int)
```
In general
```
sizeof(<array>)/sizeof(<type of array>)
```

---

