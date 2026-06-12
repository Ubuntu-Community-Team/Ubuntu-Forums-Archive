---
title: "Bash regular expressions strangeness"
date: 2007-05-29
forum: Programming Talk
---

### Post by Goliath! on 2007-05-29
A long time ago in a galaxy far, far away I used to be pretty good with shell scripting.  However, I'm seeing some strange behavior in bash on Feisty that I don't understand.  Can some one explain it to me?  Or is this some kind of bug?

I have a directory with lots of various files in it.  I want to move a subset of these files to another directory.  The files I want to move are all named YYYY-MM-DDab.tar.gz, where the YYYY-MM-DD is a date and ab stands for two alpha characters.

Here's what I tried in a test directory with a subset of my files.

```
     1  me@pc:~/AAA_My_Stuff/regexp$ ls | sort
     2  2007-05-27asdf
     3  2007-05-27asdf.tar.gz
     4  2007-05-27ff
     5  2007-05-27ff.tar.gz
     6  2007asdf
     7  2007asdf.tar.gz
     8  2asdf
     9  2asdf.tar.gz
    10  asdf
    11  asdf.tar.gz
    12
    13  me@pc:~/AAA_My_Stuff/regexp$ ls [0-9]\{4,4\}*.tar.gz
    14  ls: [0-9]{4,4}*.tar.gz: No such file or directory
    15
    16  me@pc:~/AAA_My_Stuff/regexp$ ls '[0-9]\{4,4\}*.tar.gz'
    17  ls: [0-9]\{4,4\}*.tar.gz: No such file or directory
    18
    19  me@pc:~/AAA_My_Stuff/regexp$ ls [0-9]{4,4}*.tar.gz
    20  ls: [0-9]4*.tar.gz: No such file or directory
    21  ls: [0-9]4*.tar.gz: No such file or directory
    22
    23  me@pc:~/AAA_My_Stuff/regexp$ ls '[0-9]{4,4}*.tar.gz'
    24  ls: [0-9]{4,4}*.tar.gz: No such file or directory
    25
    26  me@pc:~/AAA_My_Stuff/regexp$ ls [0-9]{0,4}*.tar.gz
    27  ls: [0-9]4*.tar.gz: No such file or directory
    28  2007-05-27asdf.tar.gz  2007-05-27ff.tar.gz  2007asdf.tar.gz
    29
    30  me@pc:~/AAA_My_Stuff/regexp$ ls '[0-9]{0,4}*.tar.gz'
    31  ls: [0-9]{0,4}*.tar.gz: No such file or directory
    32
    33  me@pc:~/AAA_My_Stuff/regexp$ ls [0-9]\{0,4\}*.tar.gz
    34  ls: [0-9]{0,4}*.tar.gz: No such file or directory
    35
    36  me@pc:~/AAA_My_Stuff/regexp$ ls '[0-9]\{0,4\}*.tar.gz'
    37  ls: [0-9]\{0,4\}*.tar.gz: No such file or directory
```

Lines 1-11 are just to show you what's in my test directory.

Line 13 should work (according to my memory and all my old books and the info page).  I should get a list of the files that start with exactly four digits and ending in .tar.gz.  (I'm no longer checking for a whole date, just the year.)  I need to escape the curly brackets with \.  But I get nothing.

But maybe I need to quote the regular expression.  So I try line 16 and get nothing.

But maybe I don't need to escape the curly brackets, so I try line 19 and I get nothing TWICE.  What's going on here?

On line 23 I try to quote it again.  Nope.

On line 26 I try to see if I could get a list with from zero to four digits at the beginning.  This time I get nothing followed by a partially correct answer.  But the file on line 9 should have matched and it's not listed.  WTF????

On lines 30, 33, and 36 I tried some other combinations with no luck.

What am I missing here?  Thanks in advance for anyone willing to help sort me out.

---

### Post by ghostdog74 on 2007-05-29
ls doesn't understand extended regular expression like those you mentioned.
you can pass the ls output to grep/egrep  that understand them..

---

### Post by Goliath! on 2007-05-30
That's what I thought, too.  So I tried it and it still isn't working for me:

```
me@pc:~/AAA_My_Stuff/regexp$ ls | grep [0-9]\{4\}*.tar.gz

me@pc:~/AAA_My_Stuff//regexp$ ls | grep '[0-9]\{4\}*.tar.gz'
2007-05-27asdf.tar.gz
2007-05-27ff.tar.gz
2007asdf.tar.gz
2asdf.tar.gz
asdf.tar.gz
```

The first one should work and I get nothing.  The second one gets the wrong stuff entirely.  I also tried it with egrep and got the same results.

---

### Post by ghostdog74 on 2007-05-30
have you tried this
```

ls -ltr  *[0-9][a-z][a-z].tar.gz

```

---

### Post by cwaldbieser on 2007-05-30
> **Goliath! said:**
> That's what I thought, too.  So I tried it and it still isn't working for me:

```
me@pc:~/AAA_My_Stuff/regexp$ ls | grep [0-9]\{4\}*.tar.gz

me@pc:~/AAA_My_Stuff//regexp$ ls | grep '[0-9]\{4\}*.tar.gz'
2007-05-27asdf.tar.gz
2007-05-27ff.tar.gz
2007asdf.tar.gz
2asdf.tar.gz
asdf.tar.gz
```

The first one should work and I get nothing.  The second one gets the wrong stuff entirely.  I also tried it with egrep and got the same results.

Try
```

$ ls | grep -E '[0-9]{4}*.tar.gz'

```
The -E is to use extended regular expressions.  You don't need to escape the "{" and "}" for grep.  The shell may require them to be escaped if the pattern wasn't in single quotes.

---

### Post by Goliath! on 2007-05-30
ghostdog74, thanks very much for your suggestion of

ls -ltr  *[0-9][a-z][a-z].tar.gz

That works as I would expect, although it's not exactly what I want.  That regexpr just matches file names ending in a digit, a letter, a letter, and .tar.gz.

---

### Post by Goliath! on 2007-05-30
cwaldbieser, thanks for the response!

What I figured out is that in the extended regexpr * matches ZERO or more of the previous expression.  So [0-9]{4}*.tar.gz matches anything ending in .tar.gz, since there can be zero of [0-9]{4}.  Also the period . matches any single character.  So technically I need to escape the periods in .tar.gz and add a period before the *.  In other words:

```

$ ls | grep -E '[0-9]{4}.*\.tar\.gz'

```

This works - thanks!  But now I really want to know why I have to pipe it thru grep.  When does the bash shell evaluate regular expressions and under what circumstances does it assume they are extended regular expressions?

I don't remember things being this difficult years ago when I used Unix on my job.  Maybe then I was using k shell and it treated regexpr differently.


> **cwaldbieser said:**
> Try
```

$ ls | grep -E '[0-9]{4}*.tar.gz'

```
The -E is to use extended regular expressions.  You don't need to escape the "{" and "}" for grep.  The shell may require them to be escaped if the pattern wasn't in single quotes.

---

### Post by Foxmike on 2007-05-30
Well, bash interprets the "ls"'s argument as a filename and is doing "file-name generation" or expansion, which is not the same thing than "regular expression comprehension" as you would like to do.  Grep is doing this.  This is why you have to pipe the output of the "ls" command to grep for it to use his regular expression comprehension capabilities.

I have broke my theets several times on it!:)

Regards. 

-FM

---

### Post by Tesiph on 2007-05-31
Bash only support some basic pattern matching, see the Bash man page on "Pathname Expansion" and "Brace Expansion".

If you want to only use bash, you could use: ```
ls [0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9][a-z][a-z].tar.gz
```
Although using grep (or find with the -regex option) may be a better option

---

### Post by Goliath! on 2007-06-01
Everyone's responses were very helpful.  Thanks!!

---

