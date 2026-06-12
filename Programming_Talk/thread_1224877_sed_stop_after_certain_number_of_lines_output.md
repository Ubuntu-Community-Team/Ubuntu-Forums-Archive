---
title: "sed: stop after certain number of lines output?"
date: 2009-07-27
forum: Programming Talk
---

### Post by paperplate9 on 2009-07-27
Any way to get sed to stop after a certain number of lines have been output? For example, if I have a 100-line file, if I want it to only match the first 20 line-matches in the file, how can I do this in sed?

I know I can use awk but have the impression that sed will be faster. I'm parsing log files which may grow to 100MB or even more. Any suggestions?

Seems like a simple solution but for the life of me, I can't figure it out.

PS: I'm on Solaris.

---

### Post by ghostdog74 on 2009-07-28
use nawk on solaris

```

nawk 'NR<=20{ #do something}' file

```

---

### Post by stroyan on 2009-07-28
That is an interesting challenge.
Sed is not really good at counting things.
But it can match a pattern that includes a count.
Here is a solution that uses the hold buffer to keep track of matches.
When the number of matches gets high enough the hold buffer matches the pattern.
When the substitution succeeds the script quits.
This example prints the first five file names that contain an "e".
```
$ MAX=5; ls | sed -rn -e "
/e/{
# Print a match
p
# Add an m to the hold buffer
x
s/^/m/
# clear the test result
t test
: test
s/m{$MAX}/done/
x
T more
Q
: more
}
"
```

Hmm...  It looks like solaris never picked up the -r option for extended regular expressions.  Perhaps it can handle this form-
```
$ MAX=5; ls | sed -n -e "
/e/{
# Print a match
p
# Add an m to the hold buffer
x
s/^/m/
# clear the test result
t test
: test
s/m\{$MAX\}/done/
x
T more
Q
: more
}
"
```

Note that the count for this regular expression is limited to 255.

---

### Post by paperplate9 on 2009-07-29
Thanks ghostdog & stroyan for the replies. However, I'm aware of how to do it with awk (but NR only works only for the input line number) and was hoping that sed would work.

stroyan, your solution works as expected. I'm glad you mention the 255 limit...I would've overlooked it and had to spend time debugging. Since I can generate the actual sed script at runtime, I can alter it a bit and use consecutive \{255\} and \{${leftover}\} combinations to fulfill my "max". Thanks.

---

### Post by ghostdog74 on 2009-07-29
> **paperplate9 said:**
> Thanks ghostdog & stroyan for the replies. However, I'm aware of how to do it with awk (but NR only works only for the input line number) and was hoping that sed would work.

stroyan, your solution works as expected. I'm glad you mention the 255 limit...I would've overlooked it and had to spend time debugging. Since I can generate the actual sed script at runtime, I can alter it a bit and use consecutive \{255\} and \{${leftover}\} combinations to fulfill my "max". Thanks.

well, seems like i misunderstood your requirement. 
```

awk '/mystring/{c++;print}c==20{print ;exit} file

```
the above awk increment counter c if "mystring" is found. then if counter reach 20, exits the process. Is that what you want?

---

### Post by Arndt on 2009-07-29
> **paperplate9 said:**
> Any way to get sed to stop after a certain number of lines have been output? For example, if I have a 100-line file, if I want it to only match the first 20 line-matches in the file, how can I do this in sed?

I know I can use awk but have the impression that sed will be faster. I'm parsing log files which may grow to 100MB or even more. Any suggestions?

Seems like a simple solution but for the life of me, I can't figure it out.

PS: I'm on Solaris.

You can pipe the output from 'sed' through "head -20".

---

### Post by paperplate9 on 2009-07-29
> **ghostdog74 said:**
> well, seems like i misunderstood your requirement. 
```

awk '/mystring/{c++;print}c==20{print ;exit} file

```the above awk increment counter c if "mystring" is found. then if counter reach 20, exits the process. Is that what you want?

Yes, that will get me the correct output with awk, and what is what I plan to use if if I have problems with sed. Sorry I wasn't clear.

> **Arndt said:**
> You can pipe the output from 'sed' through "head -20".

The problem with using 'head' is I feel that if I'm parsing a huge file and only want 'n' matches, that sed will continue to read through the file even after the number of matches has been satisfied which wastes time & CPU resources. The match strings are trivial (only searches for a certain word, nothing fancy), and a lot of output could be generated which inefficiently gets discarded by 'head'.

---

### Post by paperplate9 on 2009-07-30
> **paperplate9 said:**
> The problem with using 'head' is I feel that if I'm parsing a huge file and only want 'n' matches, that sed will continue to read through the file even after the number of matches has been satisfied which wastes time & CPU resources. The match strings are trivial (only searches for a certain word, nothing fancy), and a lot of output could be generated which inefficiently gets discarded by 'head'.

Hmm...it seems I was wrong...I guess once `head` has fulfilled the number of lines of output, it closes stdin which then closes stdout of sed, which forces sed to close.

Simple script I did to test if 'sed' will keep going after head -number is fulfilled:

```

#!/bin/bash

typeset globi=0
onexit()
{
    echo "exiting$$ at i=${globi}" >> tmp_status
}

doit()
{
    echo "me=$$" > tmp_status
    trap onexit EXIT;
    for i in {1..5000};
    do
        globi=$i
        echo $globi
    done | head -$1
}


doit ${1:-20}
```Basically this printed out that the function "doit" was done after $i lines and the program exited....

I guess the question now is, which is more efficient:
 -> one process: sed script stops itself
 -> two processes: sed keeps processing, but piped to head to stop

I'm gonna run some 'time' trials with huge files but if anyone has any input, please chime in!

---

### Post by stroyan on 2009-07-30
> **paperplate9 said:**
> 
I guess the question now is, which is more efficient:
 -> one process: sed script stops itself
 -> two processes: sed keeps processing, but piped to head to stop

I'm gonna run some 'time' trials with huge files but if anyone has any input, please chime in!

The performance of two cases will depend on just how much of the data file has to be read after reaching the desired output count.
If sed can avoid reading through a gigabyte of non-matching trailing text then stopping as soon as possible is an obvious win.

One important factor in the performance of sed or grep is not so obvious.  If you are in a locale with a variable size character encoding such as en_US.UTF-8 then pattern search code has to work much harder.  If you know that the data file uses only simple fixed size characters then you can get much better performance by setting "LANG=C" in the environment before a command that will do pattern searching.  I don't know what your default locale would be on solaris.  It is worth a look.

---

### Post by xX@v@Xx on 2012-03-23
It maybe late but can help someone... 
not so difficult.... ;-)
here it is:
sed '1,20 {your sed process};20q' file1

#ex:
```
 sed -n '1,20 {=;p};20q' file1
```let me know....

Here we have to be careful between displayed and processed
try this:
```
 sed  -n '1,20p;22q'  file1
```

the sed process will quit at line 22 with no longer process 
I guess is what you wanted to do... 
The line 21 will be processed but not displayed...

---

