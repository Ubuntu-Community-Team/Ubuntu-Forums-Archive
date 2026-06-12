---
title: "Error compiling simple code."
date: 2009-10-03
forum: Programming Talk
---

### Post by jessiebrownjr on 2009-10-03
This is basic C im attempting to learn.This is the code that Anjuta IDE pops out onto the screen when you make a new file as a template.
```
#include <stdio.h>
    int main()
        {
            printf(''Goodbye, cruel world!\n'');
            return(0);
         }

```Now that seems like it should compile right? I hit build, and get a slew of errors.
```
main.c:4:20: error: empty character constant
main.c: In function &#8216;main&#8217;:
main.c:4: error: expected &#8216;)&#8217; before &#8216;Goodbye&#8217;
main.c:4: error: stray &#8216;\&#8217; in program
main.c:4:45: error: empty character constant
main.c:4: warning: null argument where non-null required (argument 1)
make: *** [main.o] Error 1
```I'm lost how I'm supposed to even start learning to program when even the basic code like this the compiler itself gave me to as a template isn't compiling.. what could possibly be wrong?

On another compiler when I tried to run a code that would be assumed to be proper, it would error out as well.

Please help if you can think of anything, this is very frustrating.

---

### Post by MadCow108 on 2009-10-03
you have two ' (single apostrophes) resulting in '' instead of a " (double apostrophe or however this calls in English)
looks similar but its not :)
syntax highlighting should also show you that
replace the '' by " and see the difference

---

### Post by wmcbrine on 2009-10-03
You've got a pair of single quote marks at each end of the string. It needs to be *one, double* quote mark character at each end.

---

### Post by Can+~ on 2009-10-03
C reserves single quotes for character types, and double quotes for strings.

"Hello World" = 'H' 'e' 'l' 'l' 'o' ' ' 'W' 'o' 'r' 'l' 'd' 0

---

### Post by jessiebrownjr on 2009-10-03
I repalced it with the double quotes and it worked.... Now WTF did the "anjuta ide" come with a bad default program? silly. Thanks guys

---

### Post by phrostbyte on 2009-10-03
You can also do 

return 0;

for future reference, the parenthesis are pretty pointless

Typically you return a value from main() other then zero when there is an fatal error

if (error) return -1;

for instance.

---

### Post by jessiebrownjr on 2009-10-03
> **phrostbyte said:**
> You can also do 

return 0;

for future reference, the parenthesis are pretty pointless

Typically you return a value from main() other then zero when there is an fatal error

if (error) return -1;

for instance.

i'm sure this is great advice thats ahead of my time :-)

Now I have a new question..  I compiled the program finally and the only way I was able to go into a terminal and run it, was if I moved it to like my root dir with gksudu nautilus... now can I add my user desktop to where I can run my newbie compiled files from a local dir/desktop if I choose to?

Thanks for quick replies!

---

### Post by MadCow108 on 2009-10-03
you probably tried to run it like that:
myprogram.o
this then searches for a file named myprogram.o in your $PATH environment variable (you can see that with echo $PATH) and  probably didn't find it.

If the program lies in a path which is not in $PATH then you give a relative or absolute path to the program:
./myprogram.o
(. means current directory)

alternatively you can add the path where it lies in to the $PATH variable by typing this:
export PATH=$PATH:/some/dir
add this to your .bashrc to have this change permanently in the terminal

also note that when you want to start a terminal program by double clicking it it will close immediately after it finishes, so you won't see anything in most cases

---

