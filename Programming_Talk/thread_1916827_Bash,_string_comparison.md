---
title: "Bash, string comparison"
date: 2012-01-28
forum: Programming Talk
---

### Post by SoFl W on 2012-01-28
My end goal is to read some weather information from a text or xml file, extract the temperature and write it on an image file using convert.  I am trying to take it one step at a time learn a little and improve on my bash scrip.  Convert works fine calling it from a script and creating an image with a variable's text on it.

Now I want to read from a text file and this is where I am running into problems.  Every tutorial on the Internet gives similar examples that fail.  My text file is simple
sample.txt contains:
```
Line one
Line 2
Line Three
Line four
Line 5
Line SIX
```

```
#!/bin/bash
while read LINE
do 
if [ $LINE = *four* ]
then
    echo "contains four"
fi
done < "sample.txt"

```
Produces "[: 11: Line: unexpected operator" five times, if I use the ";" after the [ or not.
Using double brackets produces "readit.sh: 8: [[: not found" repeat five times if I use the ";" after the bracket or not.

I have tried several different versions of string comparison all which fail, even when I copy the exact example from a website.

What is the proper way to compare a sting in bash? (or to extract a specific line from a text file)  


I am using 10.4.3 and have bash version 4.1.5(1)-release (x86_64-pc-linux-gnu)

---

### Post by SeijiSensei on 2012-01-28
> if [ $LINE = *four* ]

I'd use 

```
if [ "$(echo $LINE | grep 'four')" != "" ]
```

The expression "echo $LINE | grep 'four'" will match any line with the text "four" in it.  If you want to be more stringent, you can use a more complex regular expression.  For instance "grep 'four$'" would only match the text "four" it if came at the end of the line.

The $() operator returns the results of the command.  In this case it will return the entire contents of any line containing the string 'four'.  That result is tested against the empty string using the not-equal operator.  So a line with the text "four" will make the LHS of the comparison not empty, and thus the entire logical expression will be true.

---

### Post by Vaphell on 2012-01-29
double brackets work just fine here
```
while read LINE
do 
  echo $LINE $( if [[ $LINE = *four* ]]; then echo "contains four";  fi )
done < "sample.txt"
```
output:
```
$ ./if.sh 
Line one
Line 2
Line Three
Line four contains four
Line 5
Line SIX
```

single brackets will fail because they don't prevent word splitting (words in $LINE get delimited at whitespaces and will appear as separate arguments) while [[ does.

also consider not using all-caps for variable names, you risk overwriting some environment variable by accident (envvars are all-caps by convention)

---

### Post by SoFl W on 2012-01-29
I found the reason for my problem.  I have been calling my programs with "sh (program_name).sh" which produces the errors.  I saw Vaphell's example and used ./(program_name).sh and it worked fine.

I have no idea when I started using "sh (program_name).sh" but I saw it used somewhere and continued with it.     For some reason it works with some scripts and obviously not others.
"bash (program_name).sh " also works fine.    I am going to work on this some more and if it works I will mark the thread solved.

---

### Post by nothingspecial on 2012-01-29
You sure you didn't make a typo

```
nothingspecial@magik:~$ while read LINE
> do 
>   echo $LINE $( if [[ $LINE = *four* ]]; then echo "contains four";  fi )
> done < "sample.txt"
Line one
Line 2
Line Three
Line four contains four
Line 5
Line SIX

```

---

### Post by SoFl W on 2012-01-29
Thank you everyone for your help.  The code worked but the way I called the code didn't.  That was frustrating  to copy examples and the examples not working.  My script is slowly coming around and working close enough to the way I would like.  Again thank you for your help, it helped me see my error.
From what I can see calling 'sh' but using "#!/bin/bash'[FONT=monospace] in my script didn't make the interpretor happy.  I am reading up on the differences between bash and sh but I still don't quite see the major differences or advantages of one over the other.

Thanks

[/FONT]

---

### Post by Vaphell on 2012-01-29
sh is symlink to dash.
hashbang line would invoke bash, but you have overriden it by calling sh explicitly. Bash has more features but is considered fat by some. It's perfect for user sessions where all kinds of stuff happen but there are uses for leaner flavors of shell so system can run scripts without the bloat when possible.

---

### Post by sisco311 on 2012-01-30
> **SeijiSensei said:**
> I'd use 

```
if [ "$(echo $LINE | grep 'four')" != "" ]
```

The expression "echo $LINE | grep 'four'" will match any line with the text "four" in it.  If you want to be more stringent, you can use a more complex regular expression.  For instance "grep 'four$'" would only match the text "four" it if came at the end of the line.

The $() operator returns the results of the command.  In this case it will return the entire contents of any line containing the string 'four'.  That result is tested against the empty string using the not-equal operator.  So a line with the text "four" will make the LHS of the comparison not empty, and thus the entire logical expression will be true.

There is no need for the test (`[') command. The syntax of the if statement is:
```
if COMMANDS; then
    COMMANDS
fi
```

POSIX:
```

while read -r line; do
    if printf '%s' "$line" | grep "REGEX" > /dev/null 2>&1; then
        printf '%s\n' "whatever"
    fi
done < file

```

In BASH, instead of echo or printf you can use a here string:
```
if grep "REGEX" <<< "$LINE"; then ...
```

But, as suggested by Vaphell, in BASH, you can use the compound test command `[[':
```
if [[ $line =~ "ERE" ]]; then ...
```
where ERE is an extended regular expression. 

See:
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)
and BashFAQ 031.

---

### Post by SoFl W on 2012-02-01
Thank you for this additional information.  Once I started calling the script correctly it started working.  I was able to write the code and get it working.  It may not be perfect, I am sure it could be improved but I was able to get done what I wanted to get done and improve my knowledge.  As I continue to improve my knowledge I will write more efficient code.  For now the script works the way I want.

---

