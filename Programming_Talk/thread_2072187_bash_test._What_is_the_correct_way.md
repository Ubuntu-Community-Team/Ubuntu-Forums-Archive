---
title: "bash test. What is the correct way"
date: 2012-10-17
forum: Programming Talk
---

### Post by Drenriza on 2012-10-17
Hey guys.

I'am wondering the following. When you in bash make a if then statement, you need to test
some value in the [ $value ]

Lately (when looking some scripts through) i have seen the if then statement used as follows
```

if [ "$(echo $value | grep '\-something')" ]; then

```

And from what i can understand from the above, it's like testing a boolean.
if echo $value |grep '\-something' equal something then do something.

Or am i totally incorrect?

But is this the "correct" way in bash to test for such?

Also another if then statement that have me puzzled is as follows
```

if [ "$(ls $path1/${path}_* 2>/dev/null)" ] && [another if];then

```

Anyone who can tell me how the above function with the ls and 2> /dev/null works.

Is it like saying
if ls $path1/${path2}_* gives an error to /dev/null and another if equal something; then do something   ??

Thanks on advance.
Kind regards.

---

### Post by albandy on 2012-10-17
2>/dev/null means redirect message errors to /dev/null

---

### Post by Drenriza on 2012-10-17
> **albandy said:**
> 2>/dev/null means redirect message errors to /dev/null

Yes but what does it mean in the context of a if statement?

Is the if true if a error message gets redirected? Or what turns the if true and what turns it false?

---

### Post by albandy on 2012-10-17
This means if "ls" returns something, the first part is true.

This can be rewrited this way:

RESULT=$(ls $path1/${path}_* 2>/dev/null)
if [ "$RESULT" ] && [another if] then


So in RESULT will be saved the result of doing ls, and 2>/dev/null does nothing in the script, only redirect the standard error output.

---

### Post by Lars Noodén on 2012-10-17
The exit code of a program or script is a separate thing from its output to stdout or stderr.  So you should be able to test the outcome regardless of whether you redirect output or not.  See $?

---

### Post by Drenriza on 2012-10-17
> **albandy said:**
> This means if "ls" returns something, the first part is true.

This can be rewrited this way:

RESULT=$(ls $path1/${path}_* 2>/dev/null)
if [ "$RESULT" ] && [another if] then


So in RESULT will be saved the result of doing ls, and 2>/dev/null does nothing in the script, only redirect the standard error output.

So it cooks down to being a boolean, true / false.

Two questions.
#1 Is this the correct way of doing so in bash or is their another way? Besides putting ls output into a variable and testing that and executing ls directly in the if.

#2 Will the if result true if their are multiple lines in $RESULT?

EDIT
> **Lars Noodén said:**
> The exit code of a program or script is a separate thing from its output to stdout or stderr.  So you should be able to test the outcome regardless of whether you redirect output or not.  See $?

What does $? mean?

---

### Post by drmrgd on 2012-10-17
Yes, another way to say it is that the '2>/dev/null' just suppresses any output of that command so that you screen isn't full of text that you don't want to see when executing the command.  You're redirecting stderr to /dev/null.

---

### Post by nothingspecial on 2012-10-17
test, if, && etc all explained here

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

### Post by drmrgd on 2012-10-17
It might be more helpful to see what you're trying to accomplish.  I've read before that using 'ls' within a conditional is not the best way.  There are some test operators that may take the place of testing an 'ls' command.  For example:

```
if [ ! -f test/* ]; then
    echo "Sorry, file not found!"
else
    echo "Hey I found some files!"
fi
```

So, if I run that on an empty directory:

```
$ ls -R test/
test/:
$ if [ ! -f test/* ]; then echo "Not Found"; else echo "Hey I found some files"; fi
Not Found

```

And now I'll run it on a directory with a file:
```

$ touch test/file1.txt
$ if [ ! -f test/* ]; then echo "Not Found"; else echo "Hey I found some files"; fi
Hey I found some files

```

See here for some Bash test operators:

[http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html)

---

### Post by Vaphell on 2012-10-17
but it will fail if there are more files. Shell with expand * to the list of files and *[ -f file1 file2 ... ]* is not a valid expression.

```
$ [ -f * ]
bash: [: too many arguments
```

[http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)
> In Bash, you can do this safely and easily with the nullglob and dotglob options (which change the behaviour of globbing), and an array:
```
shopt -s nullglob dotglob
files=(*)
(( ${#files[*]} )) || echo directory is empty
shopt -u nullglob dotglob
```
dir content packed into array, test size

---

### Post by drmrgd on 2012-10-17
Absolutely correct!  Thanks for pointing that out.  I was trying to scribble out a super simple test case of how to use test operators as opposed to 'ls' and didn't really think through more complicated (but probably truer to real life) cases.

---

