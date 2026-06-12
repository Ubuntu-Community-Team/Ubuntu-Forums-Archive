---
title: "C preprocessor and C continuation character \"
date: 2011-06-23
forum: Programming Talk
---

### Post by mr_mop on 2011-06-23
This is a query to find out if this change is intentional, or if this is an unlikely bug.

If you were to have the file, foo.dat:

```

Hello \
World
```

and then run it through the C preprocessor, I see a difference between the output on Lucid and Natty.

On Lucid, running the command:
```
cc -E -x c foo.dat
```
the output is:
```

# 1 "foo.dat"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "foo.dat"
Hello World
```
However, on Natty, the output is:
```

# 1 "foo.dat"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "foo.dat"
Hello
World
```

I'd like to know:
1) Is this an intentional change or is it a bug?
2) Can I fix it with a new command option?

Thanks in advance.

MM

---

### Post by Arndt on 2011-06-23
> **mr_mop said:**
> This is a query to find out if this change is intentional, or if this is an unlikely bug.

If you were to have the file, foo.dat:

```

Hello \
World
```

and then run it through the C preprocessor, I see a difference between the output on Lucid and Natty.

On Lucid, running the command:
```
cc -E -x c foo.dat
```
the output is:
```

# 1 "foo.dat"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "foo.dat"
Hello World
```
However, on Natty, the output is:
```

# 1 "foo.dat"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "foo.dat"
Hello
World
```

I'd like to know:
1) Is this an intentional change or is it a bug?
2) Can I fix it with a new command option?

Thanks in advance.

MM

Does this apply to macros too? What happens to input like this:

```
#define FOO a \
 b

FOO

```

---

### Post by mr_mop on 2011-06-23
> **Arndt said:**
> Does this apply to macros too? What happens to input like this:

```
#define FOO a \
 b

FOO

```

No, that works fine.

```

#define FOO a \
 b
hello \
 world

FOO

```

will output

```

# 1 "foo.dat"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "foo.dat"

hello
 world

a b

```

---

### Post by johnl on 2011-06-23
Try passing **-traditional-cpp** (see [here](http://gcc.gnu.org/onlinedocs/cpp/Traditional-Mode.html)).  This seems to work for me, but you may need to dig through the document i linked to figure out why.  I suspect it is because in valid C code whitespace including newlines is irrelevant, so there is no reason to transform:
```

FOO \
 BAR;

-into- 

FOO BAR;

```

Hope this helps.

**Edit:** found this quote:

> 
The C preprocessor is intended to be used only with C, C++, and Objective-C source code. In the past, it has been abused as a general text processor. It will choke on input which does not obey C's lexical rules. For example, apostrophes will be interpreted as the beginning of character constants, and cause errors. Also, you cannot rely on it preserving characteristics of the input which are not significant to C-family languages. If a Makefile is preprocessed, all the hard tabs will be removed, and the Makefile will not work.

Having said that, you can often get away with using cpp on things which are not C. Other Algol-ish programming languages are often safe (Pascal, Ada, etc.) So is assembly, with caution. -traditional-cpp mode preserves more white space, and is otherwise more permissive. Many of the problems can be avoided by writing C or C++ style comments instead of native language comments, and keeping macros simple. 


It sounds like using the preprocessor on something other than a valid C source is not well supported, although -traditional-cpp can help.

---

### Post by mr_mop on 2011-06-23
I'll give it a try.  So likely this is a fix to a bug and not the introduction of a new one. :)  Good to figure out.

Will report back with what I find.

---

### Post by mr_mop on 2011-06-28
Well the -traditional-cpp flag didn't help.  It made other unexpected changes to the files.

I've done away with the \ in the file, and now it just works.

Thanks for the help!

MM

---

