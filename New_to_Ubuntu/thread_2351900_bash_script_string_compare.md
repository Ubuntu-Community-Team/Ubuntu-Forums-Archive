---
title: "bash script string compare"
date: 2017-02-07
forum: New to Ubuntu
---

### Post by macnux on 2017-02-07
Hello
I'm new to Linux bash scripting
I was reading a tutorial about string comparison in bash scripts
I understand most of BUT one thing stops me.
the comparison of greater than syntax is very weird actually I don't understand it totally !!
I want a reasonable answer. 
Why did he not put quotations on the text that contains spaces which are val2 while he puts the quotations on the if statements?
it actually works but not quite understandable !!!


```
#!/bin/bash
val1=text
val2=another text
if [ $val1 \> "$val2" ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
```

and this is the tutorial I get that snippet

[https://likegeeks.com/bash-script-easy-guide/](https://likegeeks.com/bash-script-easy-guide/)

I hope you help me get something I can understand
thanks in advance.

---

### Post by &amp;KyT$0P# on 2017-02-07
> **macnux said:**
> Why did he not put quotations on the text that contains spaces which are val2 
Er, actually, he should have. :)

As it is, that line is running a program named "text", with the environment variable "val2" set to "another".

---

### Post by macnux on 2017-02-07
im sorry my mistake
the code is like this

```
#!/bin/bash
val1=text
val2="another text"
if [ $val1 \> "$val2" ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
```

my question is the code gives error when i write it like this

```
#!/bin/bash
val1=text
val2="another text"
if [ $val1 \> $val2 ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
```

i just remove the quotations from the $val2 on the if statement
error says 

./myscript: line 4: [: too many arguments

---

### Post by geeksmith on 2017-02-07
val2 has a space in it, which causes the compare to fail unless you wrap it in quotes. The '>' operator is binary: it accepts two (and only two) arguments, one on each side of it, and returns either true or false. val2 looks like two arguments on the right side of the '>' operator because of the space. You have to put it in quotes to make the shell accept it as a single argument instead of two.

It's always good form to surround your variables with quotes in shell programming, with a few exceptions. I suggest using [http://www.shellcheck.net/](http://www.shellcheck.net/) for a sanity check on scripts. If you try to conform to their suggestions, your scripts will be very clean and easier to maintain. You'll also learn a lot by trying to understand the errors it highlights in your scripts.

---

### Post by macnux on 2017-02-07
do you mean for any text contains space I have to quote it on all instances !!
bash scripting will be ridiculous if it is like that
I thought I quote its first instance only

---

### Post by sisco311 on 2017-02-07
Please check out: [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)

[ is a command. It works the same way the test command works, but its last argument must be ]. See:
```
help [
help test
```

In your first example the first argument is **text**, the second is **>**, the third is **another text** and the last one is **]**

If you don't quote $val2, then the third argument becomes **another** and the fourth argument **text**. The [ command expects either an operator or **]** as its fourth argument.

Hope this makes sense. :)

See also the man page:
```
man bash | less "+/^ +test expr"
```

EDIT: geeksmith beat me to it. Forum glitch :)

@macnux yes you should use quotes: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by geeksmith on 2017-02-07
Quotes are your friend in shell scripting world. Yes, you must use them on all variables containing spaces (in most use cases). Like I said, you should be quoting ALL variables in most use cases, not just those with spaces. For istance, you might change a variable definition from one without a space to one containing a space, or you might be reading input that may or may not contain spaces.

Believe me, requiring quotes around variables with spaces and special characters is the VERY LEAST ridiculous/annoying thing about shell scripting.

---

### Post by geeksmith on 2017-02-07
Nice links, sisco311! Adding them to my pile of shell scripting resources :cool:

---

### Post by macnux on 2017-02-08
Thanks for your detailed reply @sisco311
Does that mean I have to quote every instance of any string that contains spaces all over the script?

---

### Post by sisco311 on 2017-02-08
As a rule of thumb, yes, if in doubt, you should double quote every expansion.

---

### Post by macnux on 2017-02-09
Thanks a lot

---

### Post by SeijiSensei on 2017-02-09
Also note that there is an important difference in bash between single and double quotes.  Strings inside single quotes are treated literally, while strings inside double quotes are interpreted with environment variables replaced by their values. 
```

var="some variable"
echo 'here is $var'
echo "here is $var"

```
will return "here is $var" for the first echo and "here is some variable" for the second.

You need to enclose strings with spaces in them in quotes because bash uses the space as a delimiter.

---

### Post by macnux on 2017-02-10
thanks a lot for your reply
it helped me

---

