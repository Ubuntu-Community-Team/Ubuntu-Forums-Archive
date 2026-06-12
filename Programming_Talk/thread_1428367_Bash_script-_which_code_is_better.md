---
title: "Bash script- which code is better?"
date: 2010-03-12
forum: Programming Talk
---

### Post by blur xc on 2010-03-12
If I have a script that might create a temporary text file, and when it's done displays the contents of the text file, if it exists.  Which code would be better?

```
if [ -f file.txt ]; then
   cat file.txt
fi
```or
```
cat file.txt 2> /dev/null
```I think the if statement makes prettier code, but passing the error to /dev/null if file.txt doesn't exist works too.

Thoughts?

Thanks,
BM

---

### Post by howlingmadhowie on 2010-03-12
i'd go for the first example because it's clearer what it means. i doubt it would be much slower than the second code either.

---

### Post by kaibob on 2010-03-12
I would use the following:

```
[ -f file ] && cat file
```

If the above can't be used, I would go with the if command.

---

### Post by d3v1150m471c on 2010-03-12
```

if [ -f file ]; then
   cat file
else
echo "file does not exist"
fi

```
or
```

[ -f file] && cat file || echo "file does not exist"

```

---

### Post by blur xc on 2010-03-12
Well, I thought I'd do a benchmark the the results are more than surprising-

I wrote this script:
```
#!/bin/bash

for (( i = 1; i < 500; i++ )); do
    # cat missingfiles.txt 2> /dev/null
    if [ -f missingfile.txt ]; then
        cat missingfile.txt
    fi
done
```

and by commenting out / uncommenting the different lines of code I was able to see which is better and the 2> /dev/null is about 6000% slower to execute.  In reality, running the command just once would yield an imperceptible difference, but it is good to see anyway-

the /dev/null bit:
```
time ./test1.sh

real    0m3.203s
user    0m0.956s
sys    0m2.128s
```

and the if statement:
```
time ./test1.sh

real    0m0.050s
user    0m0.012s
sys    0m0.012s
```

Thanks-
BM

---

### Post by howlingmadhowie on 2010-03-13
> **blur xc said:**
> Well, I thought I'd do a benchmark the the results are more than surprising-

I wrote this script:
```
#!/bin/bash

for (( i = 1; i < 500; i++ )); do
    # cat missingfiles.txt 2> /dev/null
    if [ -f missingfile.txt ]; then
        cat missingfile.txt
    fi
done
```

and by commenting out / uncommenting the different lines of code I was able to see which is better and the 2> /dev/null is about 6000% slower to execute.  In reality, running the command just once would yield an imperceptible difference, but it is good to see anyway-

the /dev/null bit:
```
time ./test1.sh

real    0m3.203s
user    0m0.956s
sys    0m2.128s
```

and the if statement:
```
time ./test1.sh

real    0m0.050s
user    0m0.012s
sys    0m0.012s
```

Thanks-
BM

gosh, that is actually rather interesting. i wouldn't have expected such a huge difference.

thinking about it, this could be because cat starts a new process with all the overhead this entails, while [ test ] is a shell built-in.

---

### Post by falconindy on 2010-03-13
If you're specifying Bash in the shebang, you really should be using Bash syntax, which is even faster since [[ is a keyword. Had to up the test size by a factor of 20 to get a meaningful difference in my results:

```
# Using untested cat
real	0m5.272s
user	0m1.801s
sys	0m3.034s

# Using [ -f missingfiles.txt ]
real	0m0.130s
user	0m0.121s
sys	0m0.008s

# Using [[  -f missingfiles.txt ]]
real	0m0.090s
user	0m0.081s
sys	0m0.008s
```

Also interesting is changing the for loop declaration to Bash syntax:
```
for i in {1..10000} do;
    if [[ -f missingfiles.txt ]]; then
        cat missingfiles.txt
    fi
done
```
```
real	0m0.052s
user	0m0.045s
sys	0m0.007s
```

---

### Post by cubeist on 2010-03-13
> **falconindy said:**
> If you're specifying Bash in the shebang, you really should be using Bash syntax, which is even faster since [[ is a keyword. Had to up the test size by a factor of 20 to get a meaningful difference in my results:

```
# Using untested cat
real	0m5.272s
user	0m1.801s
sys	0m3.034s

# Using [ -f missingfiles.txt ]
real	0m0.130s
user	0m0.121s
sys	0m0.008s

# Using [[  -f missingfiles.txt ]]
real	0m0.090s
user	0m0.081s
sys	0m0.008s
```

Also interesting is changing the for loop declaration to Bash syntax:
```
for i in {1..10000} do;
    if [[ -f missingfiles.txt ]]; then
        cat missingfiles.txt
    fi
done
```
```
real	0m0.052s
user	0m0.045s
sys	0m0.007s
```

This is really useful!  Can you tell us where you found this syntax reference?  The last Bash book I bought (The bash cookbook by O'reilly) published last year doesn't use this syntax anywhere. Neither do any of my other books... is there a down side to using [[ over [ ?

---

### Post by howlingmadhowie on 2010-03-13
this page looks interesting for bash testing:
[http://www.ibm.com/developerworks/library/l-bash-test.html](http://www.ibm.com/developerworks/library/l-bash-test.html)

the basic differences seem to be:

with [ and ] you have to escape lots of stuff (for example brackets, < and > and *) so you end up writing stuff like:
```

[ian@pinguino ~]$ [ ! \( "a" = "$HOME" -o 3 -lt 4 \) ]; echo $?
1

```
which checks if a==$HOME or 3 is less than 4

with [[ and ]] you don't have to escape stuff so instead you can write:
```

[[ ( -d "$HOME" ) && ( -w "$HOME" ) ]]

```
which is a lot easier on the eyes.

(( and )) are used for arithmetic testing on integer values.

---

### Post by falconindy on 2010-03-13
> **cubeist said:**
> This is really useful!  Can you tell us where you found this syntax reference?  The last Bash book I bought (The bash cookbook by O'reilly) published last year doesn't use this syntax anywhere. Neither do any of my other books... is there a down side to using [[ over [ ?
Not sure where I picked up the {x..y} syntax initially, but it's used all over. The [BashFAQ](http://mywiki.wooledge.org/BashFAQ) is a phenomenal resource that no scripter should go without, lest their Bash-cred be questioned.

The **only** reason not to use double square brackets is portability, since it's only valid in Bash. They're faster and far more flexible as Howie has shown above. You're even allowed to use Bash regex inside [[ ]] comparisons.

---

### Post by blur xc on 2010-03-14
> **falconindy said:**
> If you're specifying Bash in the shebang, you really should be using Bash syntax, which is even faster since [[ is a keyword. Had to up the test size by a factor of 20 to get a meaningful difference in my results:

```
# Using untested cat
real    0m5.272s
user    0m1.801s
sys    0m3.034s

# Using [ -f missingfiles.txt ]
real    0m0.130s
user    0m0.121s
sys    0m0.008s

# Using [[  -f missingfiles.txt ]]
real    0m0.090s
user    0m0.081s
sys    0m0.008s
```Also interesting is changing the for loop declaration to Bash syntax:
```
for i in {1..10000} do;
    if [[ -f missingfiles.txt ]]; then
        cat missingfiles.txt
    fi
done
``````
real    0m0.052s
user    0m0.045s
sys    0m0.007s
```

Cool- thanks for that.  I would have used bash syntax for the for loop, but just didn't know how.  I'm still new at this, and I'm reading Wiley's Linux Command Line and Bash Scripting Bible May 2008 (long title) and I first ran across the C syntax for-loops and just went with it.  

I first read about the {x..y} syntax in the Ubuntu Pocket Guide by Keir Thomas, of all places for stuff like "mkdir photos{1..10}" or "touch file{1..10}.txt".

BM

---

