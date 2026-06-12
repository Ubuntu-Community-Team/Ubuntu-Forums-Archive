---
title: "Help with regexes?"
date: 2007-12-26
forum: Programming Talk
---

### Post by sammydee on 2007-12-26
Hi all

I'm a bit stuck here.

I want to search within my music directory and display all files that do NOT contain a '[' character.

I think I can do it with

```
ls -R | grep -E someregex
```

I've googled for ages but can't find any site that tells me how to only match strings that do NOT contain a certain character.

Any help?

Sam

---

### Post by psusi on 2007-12-26
[^x] matches a character OTHER than x, so what you want is:

[^\[]*

Which will match any sequence of 0 or more characters other than '[' ( which has to be escaped with \ since it has special meaning ).

---

### Post by sammydee on 2007-12-26
Well I tried with:

```
ls -R | grep '[^\[]*'
```

But it didn't work. It still listed a load of files with [ in the filename.

I think I should add that the '[' character could be anywhere in the filename, not necessarily at the beginning.

I think what '[^\[]*' does is to match any string that does not BEGIN with a '['. The '[' could be anywhere in the filename.

Any ideas?

Sam

---

### Post by ghostdog74 on 2007-12-26
if you have GNU ls, which i assume you do, 
you can use the ignore option
```

 # ls -ltr --ignore="*\[*"      

```
or if you want to use grep 
```

ls -ltr |grep -v "\["

```
read up the man page of grep and ls for more info.

---

### Post by psusi on 2007-12-26
That shouldn't work either.  I just realized that with the star, it will match any string that contains 0 or more characters OTHER than '[', even if it does contain a '['. Without the star, it matches anything that contains exactly one character that is not a [, even if it still has a [ in it.  

You need to use the start and end of line anchors to exclude the possibility of any other characters on the line:

^[^\[]*$

That will match any sequence of characters other than '[' that lie between the start and end of the line ( with nothing else ).

---

### Post by ghostdog74 on 2007-12-26
> **sammydee said:**
> 
Any ideas?

yes, read [this]("http://kaspersandberg.com/~redeeman/Mastering.Regular.Expressions.3rd.Edition.chm")

---

