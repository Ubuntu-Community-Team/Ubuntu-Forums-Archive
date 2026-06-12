---
title: "need a variant of strcmp"
date: 2013-02-14
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-14
Hello,
I need that strcmp(str1,str2) returns the following values
[b]0  - equal
1 - if char in str1 has a higher value than corresponding in str2
-1 - if char in str1 has a lower value than corresponding in str2
[/b]

Is there something which returns the ascii difference between the 2 corresponding characters where the mismatch occurs ? I am looking for a library function, and not custom code, like
```

int fun()
{
 char* str1 = "hello123";
 char* str2 = "hello9234";

 while(*str1 || *str2)
 {
  if(*str1 > *str2)
   return *str1-*str2;
  else if(*str1 < *str2)
   return *str2-*str1; 
  
  str1++;
  str2++;
 }
 return 0;
}
```

Thanks.

---

### Post by r-senior on 2013-02-15
> **IAMTubby said:**
> Hello,
I need that strcmp(str1,str2) returns the following values
[b]0  - equal
1 - if char in str1 has a higher value than corresponding in str2
-1 - if char in str1 has a lower value than corresponding in str2
[/b]

From the manual page for strcmp:
> The strcmp() and strncmp() functions return an integer less than, equal
       to, or greater than zero if s1 (or the first n bytes thereof) is found,
       respectively, to be less than, to match, or be greater than s2.

If you really need to normalize it to -1, 0, 1, you can do that with a simple division by its abs() value, taking care to avoid dividing by zero.

> Is there something which returns the ascii difference between the 2 corresponding characters where the mismatch occurs ? I am looking for a library function, and not custom code ...
There is nothing in the standard library.

EDIT: I had a look at the implementation of strcmp in GNU glibc and it does in fact return the difference between the characters but I don't believe that can be relied upon:

[http://fossies.org/dox/glibc-2.17/strcmp_8c_source.html](http://fossies.org/dox/glibc-2.17/strcmp_8c_source.html)

> ```

int fun()
{
 char* str1 = "hello123";
 char* str2 = "hello9234";

 while(*str1 || *str2)
 {
  if(*str1 > *str2)
   return *str1-*str2;
  else if(*str1 < *str2)
   return *str2-*str1; 
  
  str1++;
  str2++;
 }
 return 0;
}
```

If you plan on using this, you need to fix it first so that it doesn't compare characters beyond the end of one of the strings when the strings are different lengths.

Good indentation would help you too. One character indents are not enough for most programmers to read your code easily.

---

### Post by ofnuts on 2013-02-15
> **IAMTubby said:**
> Hello,
I need that strcmp(str1,str2) returns the following values
[B]0  - equal
1 - if char in str1 has a higher value than corresponding in str2
-1 - if char in str1 has a lower value than corresponding in str2
[/B]

Is there something which returns the ascii difference between the 2 corresponding characters where the mismatch occurs ? I am looking for a library function, and not custom code, like
```

int fun()
{
 char* str1 = "hello123";
 char* str2 = "hello9234";

 while(*str1 || *str2)
 {
  if(*str1 > *str2)
   return *str1-*str2;
  else if(*str1 < *str2)
   return *str2-*str1; 
  
  str1++;
  str2++;
 }
 return 0;
}
```Thanks.

Maybe that instead of having your code putting requirements on libraries, you could write your code taking in account what the available and popular libraries do?

When you start sharing you code (and that includes posting it here when asking questions), everybody will understand what it does. You will also get familiar with the standard libs and read more easily other people's code.

Consider also that theses standard libraries have been written and are used by people with programming skills and knowledge vastly superior to your current ones, so, on the whole, if your code doesn't fit the libs, the problem may be more with your code than with the libs.

---

### Post by Tony Flury on 2013-02-15
> **ofnuts said:**
> Maybe that instead of having your code putting requirements on libraries, you could write your code taking in account what the available and popular libraries do?

When you start sharing you code (and that includes posting it here when asking questions), everybody will understand what it does. You will also get familiar with the standard libs and read more easily other people's code.

Consider also that theses standard libraries have been written and are used by people with programming skills and knowledge vastly superior to your current ones, so, on the whole, if your code doesn't fit the libs, the problem may be more with your code than with the libs.
+1 

The standard libraries are there for a reason.

---

### Post by Bachstelze on 2013-02-15
> **ofnuts said:**
> if your code doesn't fit the libs,

What does that even mean? The only sense I can make of it is "if your code does something the libraries don't already do", which is of course ludicrous...

---

### Post by MG&amp;TL on 2013-02-15
> **Bachstelze said:**
> What does that even mean? [...] 
 
I think he means that his use-case doesn't fit the standard library use case, which isn't ludicrous but can usually be worked around.

---

### Post by Bachstelze on 2013-02-15
> **MG&TL said:**
> I think he means that his use-case doesn't fit the standard library use case, which isn't ludicrous but can usually be worked around.

I still can't understand what the problem is here. Yes, it is true there is no function in the standard library that does this. No, that does not mean doing it is a sin. Even if it is a purely hypothetical scenario, at least it is one that makes sense, unlike others from the same OP.

---

### Post by IAMTubby on 2013-02-16
> **r-senior said:**
> 
EDIT: I had a look at the implementation of strcmp in GNU glibc and it does in fact return the difference between the characters[/url]

Sir, thanks for the link. I had a look at it. It says strcmp returns "returning less than, equal to or greater than zero". But I tried out multiple examples and all it returns is -1, 0 or +1. Correct me if I'm wrong, but I tried **printf("%d",strcmp("123","923"))** and it prints -1 and not 49-57 == -9. 
Why can't the documentation just say -1,0,1 instead of saying less than, equal to or greater than zero ?

Thanks.

---

### Post by Bachstelze on 2013-02-16
> **IAMTubby said:**
> 
Why can't the documentation just say -1,0,1 instead of saying less than, equal to or greater than zero ?

Because if it did, ill-informed people would write things like [font=monospace]if (strcmp(foo, bar) == -1)[/font], which would fail on systems where strcmp() returns some other value.

---

### Post by trent.josephsen on 2013-02-16
The specification works that way *because *it's a specification and not an implementation. It's designed to be vague enough to allow each implementer to write it in the way that makes the most sense. On some platforms, compare-and-branch may be faster than subtract-and-return-the-result. On others, it may be the other way around. Ambiguity in the spec lets the implementer take advantage of these differences.

What I don't understand is why you care so much. Write your code to use the spec, not the implementation. strcmp is a general tool, and it only returns one value; you can't use it to tell which character is different, so what's the point of knowing by how much it differs? (That is, strcmp("goodbye", "hello") and strcmp("goodbye", "gooey") return the same value no matter which way it's implemented.)

If you have a particular situation in which you need to know something that no standard library function gives you, just write your own. You've got the code, there's no reason not to.

---

### Post by Bachstelze on 2013-02-16
> **trent.josephsen said:**
> (That is, strcmp("goodbye", "hello") and strcmp("goodbye", "gooey") return the same value no matter which way it's implemented.)

I see nothing to that effect anywhere...

---

### Post by IAMTubby on 2013-02-16
> **trent.josephsen said:**
>  Ambiguity in the spec lets the implementer take advantage of these differences.

alright, thanks trent.josephsen.

> 
What I don't understand is why you care so much. Write your code to use the spec, not the implementation. 
shall do that Sir.

---

### Post by IAMTubby on 2013-02-16
> **Bachstelze said:**
> Because if it did, ill-informed people would write things like [font=monospace]if (strcmp(foo, bar) == -1)[/font], which would fail on systems where strcmp() returns some other value.
alright, thanks Bachstelze.

---

### Post by trent.josephsen on 2013-02-16
> **Bachstelze said:**
> I see nothing to that effect anywhere...
Right, sorry, poor wording on my part. That is definitely not a requirement of the C Standard.

---

