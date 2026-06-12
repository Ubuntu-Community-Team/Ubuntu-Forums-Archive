---
title: "Why does this perl substitution fail?"
date: 2007-08-14
forum: Programming Talk
---

### Post by jimmymus on 2007-08-14
All I want to do is replace ./ with / in all the strings I run through the program

Here is the relevant code

$expression = "./";
$expression2 = "/";

the string going in is
./b/file3

the operator is
s/$expression/$expression2/g

and it gives me 

//file3

now if I put in
./file4

I get out 
/file4

so it at least partly works. I don't understand why the first one is failing.

---

### Post by Sp4cedOut on 2007-08-14
because when perl substitutes the variables in, it looks like:

s/.////g

when using "/", you have to escape character it:

$expression1 = ".\/";
$expression2 = "\/";

---

### Post by jimmymus on 2007-08-14
Damn, that sounded good but it doesn't work.

I'm still getting the exact same problem. =/

---

### Post by Sp4cedOut on 2007-08-15
s/.\//\//

that's the regular expression you're looking for.  Check the perl file I posted, the RE will work if you substitute the variables in too.

---

### Post by jimmymus on 2007-08-15
Ok that works!

I don't understand what just happened though. My variable approach and your variable approach were the exact same. 

Obviously they weren't though. It must have been something insanely simple that I kept overlooking. I wonder why...

Oh well

Thanks so much! This is a great forum

---

### Post by slavik on 2007-08-15
umm, I suggest escaping the dot, too

s|\./|/|g (no reason to escape slash here as I used | instead)

---

### Post by Sp4cedOut on 2007-08-15
oh yeah, I forgot about the dot.  You need to escape that too.

in regex

. = any character
\. = dot

---

### Post by Modred on 2007-08-15
All of that escaping is messy.  Just change the delimiter in the substitution expression.

```
s+$expression+$expression2+g
```

If you aren't using / as your delimiter between expressions, then you don't need to escape it.  You will probably still need to escape the dot, considering that it is a special character in a regular expression.

As an example, I just ran this test code:

```
$text = "Hello World/People";
$text =~ s+/+-+;
print $text;
```
The output was:
Hello World-People

As you can see, no escaping the slash.  Looks much cleaner, plus fewer things to type and possibly mess up.

Note that you don't have to use +.  You can really use almost any non letter character.

EDIT: I just now saw that slavik already said this, but I overlooked it without realizing it, so assuming others will do the same, there shouldn't be any harm in repeating.

---

### Post by slavik on 2007-08-15
in russian there is a saying "repetition is mother of learning" :)

---

