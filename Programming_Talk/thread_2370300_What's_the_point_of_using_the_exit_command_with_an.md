---
title: "What's the point of using the exit command with an integer?"
date: 2017-09-01
forum: Programming Talk
---

### Post by John_Patrick_Mason on 2017-09-01
I'm having trouble understanding a chapter in the book *The Linux Command** Line* by William E. Shotts, a popular book for those seeking to learn about the Linux command line. The book can be found [here]("https://sourceforge.net/projects/linuxcommand/files/TLCL/16.07/TLCL-16.07.pdf/download").  The section I'm having trouble with can be found on page 388 of the  PDF. Frankly, I don't get either the first paragraph or the second  paragraph. The book says that adding the exit command with the integer  "1" to the following script:

```

#!/bin/bash

# test-file: Evaluate the status of a file

FILE=~/.bashrc

if [ -e "$FILE" ]; then
        if [ -f "$FILE" ]; then
                echo "$FILE is a regular file."
        fi
        if [ -d "$FILE" ]; then
                echo "$FILE is a directory."
        fi
        if [ -r "$FILE" ]; then
                echo "$FILE is readable."
        fi
        if [ -w "$FILE" ]; then
                echo "$FILE is writable."
        fi
        if [ -x "$FILE" ]; then
                echo "$FILE is executable/searchable."
        fi
else
        echo "$FILE does not exist"
        exit 1
fi

exit

```

will  allow the script to indicate failure if $FILE expands to the name of a  nonexistent file. I tried changing the value of FILE to /bin/usr (a  nonexistent file) with the "exit 1" command left intact and then omitted  the same command to compare both results to each other, and I still end  up, both times, with the string "/bin/usr does not exist".
I guess  the fact that it printed "/bin/usr does not exist" both times is an  indication of failure, but then what's the point of including the exit  command with an integer? How does using the exit command with 1 show  that the script failed? I don't get what's the point of including the  exit 1 command if I get the same results in both cases?

Second,  what does the book mean by operators? In mathematics, I was always  taught that the operators were the + (plus) - (minus) / (divided by) and  * (times) symbols. Is that what they are referring to?

---

### Post by &amp;KyT$0P# on 2017-09-01
The exit status is used to indicate whether your program succeeded (0) or failed (any positive number, usually 1).  It is largely your responsibility, as the programmer, to decide when to exit with a non-zero status, and if so what that exit status will be.

Let's say your program is called [FONT=Courier New]yourprogram.sh[/FONT] and resides in the current directory.  You can get the exit status by running your program like so -
```
./yourprogram.sh;echo "$?"
```

As for why it's useful to give non-zero exit status on failure?  The following commands are very basic examples to demonstrate -
```
./yourprogram.sh && echo 'My program Succeeded!'
./yourprogram.sh || echo 'My program failed :('
```

Try them with your example program, both with and without the [FONT=Courier New]exit 1[/FONT] line, and see the difference.

Does this help?

---

### Post by Rocket2DMn on 2017-09-02
Perhaps it should be noted that the error message you see is more useful to human users, whereas the integer code is more useful for other software to determine if something succeeded or failed.  Error message are not consistent, are often mixed with normal messages, and can even be translated into different languages depending on the user's system preferences.  This makes them difficult for software to parse.  Error codes are just numbers, and can be kept consistent across software versions and systems, so other software could conceivably make decisions based on the specific return values, not just a binary decision of success or failure.

For example, in many languages like C, we use a special integer called "errno" to indicate status - see [http://pubs.opengroup.org/onlinepubs/009695399/basedefs/errno.h.html](http://pubs.opengroup.org/onlinepubs/009695399/basedefs/errno.h.html)

---

### Post by John_Patrick_Mason on 2017-09-02
First, I'd like to thank both of you for responding. After reading both   answers I did some experimentation of my own. The first thing I did was   modify the script to look like this:

```

#!/bin/bash

# test-file: Evaluate the status of a file

FILE=/bin/usr

if [ -e "$FILE" ]; then
    if [ -f "$FILE" ]; then
        echo "$FILE is a regular file."
    fi
    if [ -d "$FILE" ]; then
        echo "$FILE is a directory."
    fi
    if [ -r "$FILE" ]; then
        echo "$FILE is readable."
    fi
    if [ -w "$FILE" ]; then
        echo "$FILE is writable."
    fi
    if [ -x "$FILE" ]; then
        echo "$FILE is executable/searchable."
    fi
fi

exit

```

I then ran the program with:

```

test_program

```

after making sure to place the program in the ~/bin directory (to reduce typing). I then typed:

```

echo $?

```

which gave me an exit status of 0. I then proceeded to modify the script again with:

```

#!/bin/bash

# test-file: Evaluate the status of a file

FILE=/bin/usr

if [ -e "$FILE" ]; then
    if [ -f "$FILE" ]; then
        echo "$FILE is a regular file."
    fi
    if [ -d "$FILE" ]; then
        echo "$FILE is a directory."
    fi
    if [ -r "$FILE" ]; then
        echo "$FILE is readable."
    fi
    if [ -w "$FILE" ]; then
        echo "$FILE is writable."
    fi
    if [ -x "$FILE" ]; then
        echo "$FILE is executable/searchable."
    fi
else
    exit 1
fi

exit

```

ran the program again and then typed:

```

echo $?

```

which gave me an exit status of 1. Now, correct me if I'm wrong, but  this is how I understand the whole purpose of using the exit command  with an integer in the first place: In the first script above, if I omit  the exit 1 command  and proceed to execute the script and then type echo $?, there is no  way for sure to tell whether the script executed "successfully" even  though the  echo $? command gave an exit status of 0. Whereas if I modify the script  to add the exit 1 command, run my script again and then re-type echo $?   again, which gives me a value of 1, and since the integer matches the  assigned exit status value in my second script, I can ascertain that the  portion of the script above the "else" command failed to run. Does that  explanation make sense?

---

### Post by &amp;KyT$0P# on 2017-09-03
> **John_Patrick_Mason said:**
> Now, correct me if I'm wrong, but  this is how I understand the whole purpose of using the exit command  with an integer in the first place: In the first script above, if I omit  the exit 1 command  and proceed to execute the script and then type echo $?, there is no  way for sure to tell whether the script executed "successfully" even  though the  echo $? command gave an exit status of 0. 
This part is correct.

> Whereas if I modify the script to add the exit 1 command, run my script again and then re-type echo $? again, which gives me a value of 1, and since the integer matches the assigned exit status value in my second script, I can ascertain that the portion of the script above the "else" command failed to run. 
You have the right idea but not quite precise.  Your second script explicitly declares that if [FONT=Courier New]$FILE[/FONT] does not exist, it is an error.  You have chosen an exit status of 1 for that error.  And your script does not use an exit status of 1 for any other reason.

So when you run your script again and then re-type [FONT=Courier New]echo $?[/FONT] again, and get a value of 1, since the integer matches the assigned exit status value in your second script, you can ascertain that your script failed because it encountered a non-existant [FONT=Courier New]$FILE[/FONT].

---

### Post by John_Patrick_Mason on 2017-09-03
If I could just rephrase the first part of my statement to be even more  precise; just because echo $? outputs an exit value of 0, doesn't mean  the file assigned to FILE existed in the first place, is that correct?

Also,  if we were to go back to my original question of what's the point of  using the exit 1 command in the very first script. Looking at the script  again, the line echo "$FILE does not exist" seems kinda redundant, since I  could have just as well omitted the line and typed echo $? to get the exit  value, and be done with it, am I right?

---

### Post by &amp;KyT$0P# on 2017-09-03
> **John_Patrick_Mason said:**
> If I could just rephrase the first part of my statement to be even more  precise; just because echo $? outputs an exit value of 0, doesn't mean  the file assigned to FILE existed in the first place, is that correct?
For the script **without** [FONT=Courier New]exit 1[/FONT], that is correct.

> Also, if we were to go back to my original question of what's the point of using the exit 1 command in the very first script. Looking at the script again, the line echo "$FILE does not exist" seems kinda redundant, since I could have just as well omitted the line and typed echo $? to get the exit value, and be done with it, am I right?
Well, you can, but giving a human-readable error message is good practice.

* To illustrate one example why, suppose you chain your script with several others that don't give human-readable error messages.
```
test_program && test_program2 && test_program3 && echo 'Success!!!';echo "$?"
```
Unless the scripts have no overlap at all in error exit statuses, it might take a while to figure out which script is breaking the chain.  If the scripts give good human-readable error messages too, you'll know *at a glance* which script failed and why.

On a related note, I sometimes prefix error messages with the name of the script, e.g. -
```
echo "test_program: Error: $FILE does not exist"
```

---

### Post by John_Patrick_Mason on 2017-09-03
OK, now what's the deal with the operators? I was taught that the operators were + - / *. This from the book:

"First, notice how the parameter $FILE is quoted within the expressions. This is not required, but it is a defense against the parameter being empty. If the parameter expansion of $FILE were to result in an empty value, it would cause an error (the operators would be interpreted as non-null strings rather than operators). Using the quotes around the parameter ensures that the operator is always followed by a string, even if the string is empty."

I still don't get why quotes are necessary.

---

### Post by &amp;KyT$0P# on 2017-09-03
> **John_Patrick_Mason said:**
> OK, now what's the deal with the operators? I was taught that the operators were + - / *. 
They are using the term 'operator' to refer to the various tests you're performing, such as
```
[ -e "$FILE" ]
```
In that example, the operator is [FONT=Courier New]-e[/FONT]

> **John_Patrick_Mason said:**
> I still don't get why quotes are necessary.
That's because that's not the best way to introduce the concept of quotes.  Let me try to do better.

You know how you separate commands arguments with spaces, like so?
```
less -R somefile.txt
```

Ok, now what if instead of [FONT=Courier New]somefile.txt[/FONT], the file we wanted to view was named [FONT=Courier New]Foo Foo Foo.txt[/FONT]?  If you try to 'just use' that filename, this is what happens -
```
$ less -R Foo Foo Foo.txt
Foo: No such file or directory
Foo.txt: No such file or directory

```
Yeah yeah, we know those don't exist, not helpful.  So how do we tell the shell to treat the filename as a single argument?

Well, there are several ways to solve this, but the simplest one is this -
```
less -R "Foo Foo Foo.txt"
```

Woo-Hoo, It Works! :D

So, to sum up what's said so far, use quotes when you want to limit what the shell parses.  I believe that double-quotes, as we are using here, limit parsing to stuff involving the $ symbol, commands enclosed in backticks, and some backslash escape sequences.  (I may have left something out, please correct me if so.)


Now, going back to the explanation you quoted -
> "First, notice how the parameter $FILE is quoted within the expressions. This is not required, but it is a defense against the parameter being empty. If the parameter expansion of $FILE were to result in an empty value, it would cause an error (the operators would be interpreted as non-null strings rather than operators). Using the quotes around the parameter ensures that the operator is always followed by a string, even if the string is empty."
Variables in shell scripts are not like other languages.  Their values just kinda get plopped straight in the code.

Example -
```
$ Foo="Bananas   Monkey"
$ cat $Foo
cat: Bananas: No such file or directory
cat: Monkey: No such file or directory
```
This expanded to [FONT=Courier New]cat Bananas Monkey[/FONT], which failed because I don't have files named Bananas or Monkey in that directory.

And again, with quotes -
```
$ cat "$Foo"
cat: 'Bananas   Monkey': No such file or directory

```
This time it expanded to
```
cat "Bananas   Monkey"
```
... which failed because I don't have a file with that name either.

Now what if Foo has no value?
```
$ Foo=
$ cat $Foo
```
The shell interprets this as simply [FONT=Courier New]cat[/FONT], which will hang.  (If you actually ran this, use Ctrl-C to get your shell back.)

Let's try it again, but with quotes -
```
$ cat "$Foo"
cat: '': No such file or directory
```
Notice that it expanded to [FONT=Courier New]cat ""[/FONT].  See the difference?  The shell treats the quotes' contents as a single unit, so it sees it as an argument to pass to [FONT=Courier New]cat[/FONT], albeit an empty argument.



Armed with that, read this text again -
> "First, notice how the parameter $FILE is quoted within the expressions. This is not required, but it is a defense against the parameter being empty. If the parameter expansion of $FILE were to result in an empty value, it would cause an error (the operators would be interpreted as non-null strings rather than operators). Using the quotes around the parameter ensures that the operator is always followed by a string, even if the string is empty."

Hope this clears that one up for you. :)

---

### Post by Rocket2DMn on 2017-09-05
FYI, if you don't provide an exit code from the script, the exit code will be the exit status of the last command run by the script.  This is NOT necessarily 0.  So for example if my script is
```

echo "Hello world!"

```
The echo command doesn't fail, and $?=0.  If, however, my script is
```

cat /foo/bar

```
then I get $?=1, because 1 is apparently the return code from "cat" when the file does not exist.

As an aside, I highly recommend using [shellcheck]("apt:shellcheck") to analyze your shell scripts.  It can provide very helpful feedback on common scripting issues.  There is also a web tool at [https://www.shellcheck.net/](https://www.shellcheck.net/)
It will catch issues like missing quotes around variables when appropriate.

---

### Post by John_Patrick_Mason on 2017-09-05
It's counterintuitive, because to me

```

Foo=
cat "$Foo"

```

is still cat "NULL", which should hang, except it doesn't.

---

### Post by Rocket2DMn on 2017-09-06
> **John_Patrick_Mason said:**
> It's counterintuitive, because to me

```

Foo=
cat "$Foo"

```

is still cat "NULL", which should hang, except it doesn't.

Because you put $Foo inside quotes, the cat application is actually receiving a parameter - an empty string, since $Foo doesn't evaluate to anything.  It's running```

cat ""

```
which is not the same as just
```

cat

```

This is another reason it is preferable to use quotes - 1) you know that the parameter is actually being passed (even if it's empty), and 2) as you saw, it wouldn't let your script hang, or 3) even worse, getting parameters potentially out of order, which could cause unexpected (or even undesirable) behavior, e.g. something that unintentionally overwrites or otherwise destroys files/data.

---

### Post by John_Patrick_Mason on 2017-09-10
Thanks to both for helping me out. I'm marking this thread as solved.

---

### Post by &amp;KyT$0P# on 2017-09-11
You're welcome.  :KS

---

