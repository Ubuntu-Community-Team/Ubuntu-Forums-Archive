---
title: "using awk to print function  name"
date: 2008-12-21
forum: Programming Talk
---

### Post by samantha grace on 2008-12-21
hi,

I have a requirement where given a variable and a source file say...variable x and file1.c, i need to find the name of the function in which the variable was declared.

i was wondering if this is possible using awk. I already know the name of the variable to be searched...and i guess using grep i can also find the line number, how do i then proceed to find the name of the function in which the variable was declared:confused:.

any ideas are welcome. FYI..the file is a C source code file.

thanks,
Sam

---

### Post by ghostdog74 on 2008-12-21
i can't understand your problem. Show it using an example file, and describe clearly how you want it to look like in the end.

---

### Post by samantha grace on 2008-12-21
hi,
thanks for your reply. Assume that i have a variable called x (this is the input of the script) and i need to find the names of all the functions containing x.Take the following code as an example:

  ```
 
   1.int main(void);
   2.void foo(void);
   3.void bar(void);
   4.
   5.int main(void)
   6.{
   7.int x;
   8.return 0;
   9.}
  10.
  11.void foo(void)
  12.{
  13.int x;
  14.}
  15.
  16.void bar(void)
  17.{
  18.int x;
  19.}
```


so i guess the output should be:


 in 5. main(void) x occurs in line 7 as int x;

in 11.foo(void) x occurs in line 13 as int x

and in 16.bar(void) x occurs in line 18 as int x

Something similar but not exactly as above. To print the name of the functions containing x is crucial.

thanks,
Sam

---

### Post by monkeyking on 2008-12-21
Without being able to help you...

I can understand what you want, and why you want to do it.

At some point I had a very large sourcecode,
that I just needed to clean up.
Remove unused functions and so.

But the lexical analyser in gcc is not so developed.
So theres no builtin command to check for unused functions only variables. Functions are not first class objects in c++, so theres no need to implement a functionality like this in the compiler.


But a debugger at the lexical level in gcc would solve most of these problems.

good luck

---

### Post by samantha grace on 2008-12-21
hi,

ok..i ma not concerned only with variables that are not initialized but any variable used in the program.

How about ctags..or etags..i looked into their docs..but could not figure out how to get the solution using the tag file format.

thanks,
Sam

---

### Post by samantha grace on 2008-12-22
hello,

i guess you were referring to programs such as ctags.i was able to test ctags and found out that it is capable of listing all local/global variables and function names from a source file.But then again i wonder how we can use ctags to determine which variable belongs to which function.

thanks,
Sam

---

