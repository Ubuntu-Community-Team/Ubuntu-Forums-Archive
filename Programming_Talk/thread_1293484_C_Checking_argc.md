---
title: "C Checking argc"
date: 2009-10-17
forum: Programming Talk
---

### Post by matmatmat on 2009-10-17
How do you check against an argument in C? Eg:
```

if (argv[1] == "e"){

```
doesn't work

---

### Post by Bachstelze on 2009-10-17
[http://publications.gbdirect.co.uk/c_book/chapter9/string_handling.html](http://publications.gbdirect.co.uk/c_book/chapter9/string_handling.html)

You can't use == between two strings in C because strings are pointers.

---

### Post by BenAshton24 on 2009-10-17
Anyway, are you actually getting argv when you initialise your program?

eg.
```
#include <iostream>

int main(int argc, char *argv[])
{
	std::string bob = argv[1];
	if (bob == "e"){
		std::cout << "hi";
	}
}
```

EDIT: Sorry, I forgot you were talking about C, my mind is in C++ mode at the moment :P

---

### Post by matmatmat on 2009-10-17
Shouldn't this work:
```

if (strcmp(argv[1],"e")){

```
?

---

### Post by howlingmadhowie on 2009-10-17
> **matmatmat said:**
> How do you check against an argument in C? Eg:
```

if (argv[1] == "e"){

```
doesn't work

in C you can use the strings.h library:

```

#include <strings.h>
#include <stdio.h>

int main(int argc, char **argv) {

  if(strcmp(argv[1], "test")==0) {
    printf("success!\n");
  } else {
    printf("failure!\n");
  }

  return 0;
}

```

which results in the following:

```

me[7]% gcc -o stringtest stringtest.c
me[8]% ./stringtest test
success!
me[9]c% ./stringtest foo
failure!
me[10]c% 

```

---

### Post by howlingmadhowie on 2009-10-17
> **matmatmat said:**
> Shouldn't this work:
```

if (strcmp(argv[1],"e")){

```
?

almost. strcmp returns 0 if the first argument is the same as the second.  but 0 is regarded as false in an if condition, so you have to test for this:

```

if (strcmp(arg1, arg2)==0) {  
/* this will be executed when arg1 and arg2 are the same */
}

```

---

### Post by matmatmat on 2009-10-17
Thanks

---

### Post by nvteighen on 2009-10-17
> **howlingmadhowie said:**
> in C you can use the strings.h library:


Strictly speaking, it's **string.h** (singular!) which provides the usual str* functions... **strings.h** (plural!) instead provides just two functions: **strncasecmp** and **strcasecmp**... Of course, strings.h includes string.h and that's why your snippet works ;)

I myself prefer to use the exact header... I'm a bit obsessive with that :P

---

### Post by MadCow108 on 2009-10-17
if you want to compare a single char you can use ==
but you have to use single quotes and dereference argv[x]:
```

if (*argv[1] == 'e')

```
but this only works with single letters!!! for more you have to use str*cmp functions

single quotes mark chars and double quote are char arrays

---

### Post by dwhitney67 on 2009-10-17
Just to add spice to this thread, if it is *nix-style command line args that need to be checked by the application, consider using getopt() or one of it's related functions.

See the man-page:
```

man 3 getopt

```

---

### Post by matmatmat on 2009-10-17
I've looked at getop before, but my app is a bit simple for that!

---

