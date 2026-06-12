---
title: "CamelCase"
date: 2008-02-17
forum: Programming Talk
---

### Post by Fbot1 on 2008-02-17
WhatDoYouThinkOfTheCamelCaseAsOpposeToUsingUnderscores?

---

### Post by CptPicard on 2008-02-17
Which language? I'm used to camelCase in Java and maybe C++, underscores in C, and variable-names-with-lots-of-hyphens in Lisps.

It's weird that you get used to conventions like that, but so it is.

---

### Post by Engnome on 2008-02-17
Doesn't matter much as long as you are consistent.

Myself I use a mix, camelcase for functions and underscore for variables. Dunno why I do it but it stuck, hard to change now, all my programs use it.

---

### Post by LaRoza on 2008-02-17
I use a mix, almost like CptPicard's scheme (or Lisp?).

---

### Post by Fbot1 on 2008-02-17
> **CptPicard said:**
> Which language?

I guess I should of put a "It depends" option.

---

### Post by LaRoza on 2008-02-17
> **Fbot1 said:**
> I guess I should of put a "It depends" option.

I can change the "Don't Care" to "It Depends" for you.

---

### Post by Lster on 2008-02-17
I use CamelCase for almost all my languages. I used to use underscore_styling but switch about 9 months ago. The main thing is consistency for me!

---

### Post by Geekkit on 2008-02-17
I am a conformist: I use what is accepted for the particular programming language I am using (e.g., CamelCase in Java, and under_scores in C). :)

---

### Post by CptPicard on 2008-02-17
That's the point.. consistency does not mean using non-standard ways of coding in some given particular language so that you can be "consistent" in using the same style everywhere.

---

### Post by cprofitt on 2008-02-17
hmm... I have struggled with the concept for a while.
 
I do not work as part of a team so my conventions really only apply to me.
 
I use _variable for form or application global items.
 
```

private string _uID;
private bool _bNewNote;
private bool _bNewContact;
private classes.mContact _objContact = new Business_Mate.classes.Contact();

```
 
I use camelCasing or sCamelCasing in general instead of underscores... but I do not really have a reason to do so. With a static typed language I tend to use:
 
bCamelCase = bool
iCamelCase = int
sCamelCase = string
 
etc...
 
In the end the notation system you use has to do two things:
 
1.  Help you as your write more in-depth programs to remember what the variable/object names are
2.  Help you and a team understand one another's code

---

### Post by Fbot1 on 2008-02-17
> **LaRoza said:**
> I can change the "Don't Care" to "It Depends" for you.

No thanks, they're two different things.

---

### Post by pmasiar on 2008-02-17
Different languages have different standards.

Java uses CamelCase. Python uses CamelCase for classes, and under_score for variables.

Then, some people bring standards from other languages, and projects keep code convention even if not compatible with language standards. Such is life.

---

### Post by Fbot1 on 2008-02-17
> **pmasiar said:**
> Different languages have different standards.

Java uses CamelCase. Python uses CamelCase for classes, and under_score for variables.

Then, some people bring standards from other languages, and projects keep code convention even if not compatible with language standards. Such is life.

So that's a "Don't care"?

---

### Post by Lster on 2008-02-17
[QUOTE=CptPicard]That's the point.. consistency does not mean using non-standard ways of coding in some given particular language so that you can be "consistent" in using the same style everywhere.[/QUOTE]

Use whatever is best and keep it the same for each project is my view. I see no reason to use a standard is no benefits come from that but I agree that there is no point in using the same styling everywhere to be "consistent".

---

### Post by CptPicard on 2008-02-17
> **Lster said:**
> Use whatever is best and keep it the same for each project is my view.

I would make an exception here in case there are multiple languages in a single project...

---

### Post by happysmileman on 2008-02-17
O only really code in C++ (and don't code much anyway) so i always use camelcase, but if I was using a language other than C++ I'd choose based on what most programmers use in that language

---

### Post by red_Marvin on 2008-02-17
I try to keep variable names short enough so I don't need either, if descriptions are needed to avoid confusion, I add comments.
Anything else usually becomes a futile attempt at making a descriptive enough name that is short enough to not get cumbersome to type.

---

### Post by bruce89 on 2008-02-17
Because of GTK+, I like underscores for functions and CamelCase for structures etc.

---

### Post by happysmileman on 2008-02-17
> **bruce89 said:**
> Because of GTK+, I like underscores for functions and CamelCase for structures etc.

Because of QT I enjoy consistency and efficiency :p

[Start QT-GTK flamewar]

---

### Post by DoktorSeven on 2008-02-17
i_love_underscores_since_camel_case_hurts_my_head.

however_if_you_like_camel_case_go_for_it it_wont_hurt_my_feelings_at_all

;)

---

### Post by Wybiral on 2008-02-17
> **CptPicard said:**
> Which language? I'm used to camelCase in Java and maybe C++, underscores in C, and variable-names-with-lots-of-hyphens in Lisps.

It's weird that you get used to conventions like that, but so it is.

Same here, I tend to go with the most common standard for whatever language I'm using.

My C++ code looks like:
```

class SomeClass;

void someFunction() {
    int someVariable = 0;
}

```

My C code looks like:
```

struct some_struct;

void some_function()
{
    int some_variable = 0;
}

```

And my Python code looks like:
```

class SomeClass

def some_function():
    some_variable = 0

```

---

### Post by pmasiar on 2008-02-18
> **Fbot1 said:**
> So that's a "Don't care"?

No, I do care a lot. But there **are** different standards, and I prefer to use them.

---

### Post by lnostdal on 2008-02-18
for almost all "C type languages" (c, c++, java, php, python, etc.) i use:

```

TypesAndClassesAndNamespaces
functionsAndMethods (the initial character is lowercase)
public_or_normal_variables
_private_or_protected_variables (underscore as prefix)
method_or_function_parameter_names_ (underscore as postfix)
CONSTANT

void myFunction()
{
}

class MyType {
  void myMethod()
  {
  }
};

namespace MyNamespace {
}

```


for c/c++ in particular:
```

TEMPLATE_PARAMETER
M_macroFunction
M_macro_value

When doing meta-programming default return-types should have the name 'Result', while return values
should have the name 'value'. Other return-values should have the same naming as
public variables and attributes, while return-types should have the same naming as classes.

```

for lisp i use the common de facto style

---

### Post by cb951303 on 2008-02-18
I use underscore and camelcase in function names such as:

```
void gfx_RenderScene(...)
void snd_StreamWave(...)
```

I first saw it in quake source and it made perfect sense, very clear to understand :)

---

### Post by happysmileman on 2008-02-18
> **cb951303 said:**
> I use underscore and camelcase in function names such as:

```
void gfx_RenderScene(...)
void snd_StreamWave(...)
```

I first saw it in quake source and it made perfect sense, very clear to understand :)

That seems like a very good idea, (putting something like "gfx_", "snd_" in front of function name, then CamelCase) since you know exactly what the function does, (at a glance you know whether it's to do with sound or graphics etc...) But isn't that the purpose of namespaces?

---

### Post by cb951303 on 2008-02-18
> **happysmileman said:**
> That seems like a very good idea, (putting something like "gfx_", "snd_" in front of function name, then CamelCase) since you know exactly what the function does, (at a glance you know whether it's to do with sound or graphics etc...) But isn't that the purpose of namespaces?

indeed :) I should have probably add that I'm using C and quake is written in C :) so no namespaces for me :\

---

### Post by happysmileman on 2008-02-18
> **cb951303 said:**
> indeed :) I should have probably add that I'm using C and quake is written in C :) so no namespaces for me :\

Ah ok, just making sure, I've never coded anything even moderately big, so i've never used namespaces and therefore wasn't really sure whether I was right

---

### Post by Zwack on 2008-02-18
There's a missing option...

I use implicit typing in my Fortran code... :-P

In my case it depends...

If there is a coding standard I follow it, if I'm only doing something simple I keep variable names short...

You're not going to forget what a was in the three lines that it exists in...

If it's C++ I use CamelCase usually
if it's C I use the_underscores usually
in shell scripts I usually use ALLUPPERCASE
and if it's Fortran 77 then I make sure that my integers start with i, j, k, l, m or n.

Z.

---

