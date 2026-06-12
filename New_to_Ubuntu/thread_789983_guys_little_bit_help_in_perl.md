---
title: "guys little bit help in perl"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by viswanathan on 2008-05-11
well guys i know this is not the appropriate place to post this topic but had a little doubt why do we declare **my $______**_ for a variable why cant we just declare **$_________ **  and i more doubt how do the c compiler differentiate between preprocessor directive form comments coz both of them start with # :lolflag:

---

### Post by sdennie on 2008-05-11
1) I believe that declaring stuff "my" when using "use strict" is to limit the scope of variable.  If you don't declare "use strict" at the top of the program, you can makeup variable names on the fly but, it's not a good habit to get into.

2) Perl programs don't use the C compiler so there is no mistaking a comment for a preprocessor directive.

---

### Post by viswanathan on 2008-05-11
dude what about c compiler during c programing how does it differentiate that was my question

---

### Post by sdennie on 2008-05-11
For comments, C uses /* */ and C++ uses // or C style comments.  Although perl and C look similar in many ways, they don't use the same notation for comments.  So, yes, in C, "#blah" will be passed to the preprocessor whereas in perl "#blah" will be considered a comment.

---

### Post by niteshifter on 2008-05-11
Hi,

You're correct - not the right place. Will probably be moved....

In Perl "my $variable" and "$variable" will resolve like this: $variable is in the global namespace, "my $variable" is in a specific module's namespace. This is to prevent names collision. You can use $variable in short scripts, but with modules and objects using "my" is to your advantage, unless you enjoy long, frustrating debug sessions.

Last time I looked comments in C (traditional) are bracketed between /* and */ markers, more modern C/C++ can use //, none use the # for comments, that's a shell thing.

---

### Post by viswanathan on 2008-05-11
thanx dude got little bit confused its really confusing  to learn two language at a time

---

### Post by viswanathan on 2008-05-11
guys 1 more doubt how does the compile differentiate she bang with comments ???????/

---

### Post by sdennie on 2008-05-11
Essentially, the interpreter doesn't differentiate it from a comment:

[http://en.wikipedia.org/wiki/Shebang_%28Unix%29](http://en.wikipedia.org/wiki/Shebang_%28Unix%29)

---

### Post by viswanathan on 2008-05-11
thnx dude u r really genius

---

