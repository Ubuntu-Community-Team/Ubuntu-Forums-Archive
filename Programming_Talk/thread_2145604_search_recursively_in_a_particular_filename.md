---
title: "search recursively in a particular filename"
date: 2013-05-15
forum: Programming Talk
---

### Post by IAMTubby on 2013-05-15
Hello,
_Situation :_ I want to search for the word, 'confedit' in all makefiles in my system using grep.

_I have tried :_
I know of grep -r
I tried doing grep -r 'confedit' ./*Makefile 2>/dev/null
but it doesn't return anything.

The makefiles could be named as Makefile or makefile.
So please give me a file pattern which checks both.

Please advise,
Thanks.

---

### Post by papibe on 2013-05-15
Hi IAMTubby.

As far as I know, if you omit the filename, it would search recursively. Unfortunately, it would look for all files.

This may work:
```
find -type f -iname "makefile" -exec grep -H "confedit" '{}' \;
```
where:
[LIST]
[*]-type will filter only files
[*]    -iname will match the filename "makefile" (case insensitive).
  [*]  -exec will execute a grep for each file found,
[*]-H in grep will print the filename with the match line.
[/LIST]
Let us know how it goes.
Regards.

---

### Post by prodigy_ on 2013-05-15
^ This won't output filenames where matching lines are found. Need to add **-print**.

---

### Post by papibe on 2013-05-15
> **prodigy_ said:**
> ^ This won't output filenames where matching lines are found. Need to add **-print**.
Good catch! :)

The grep's option -H would do that even better (filename in same line as matched line).

Regards.

---

### Post by IAMTubby on 2013-05-16
> **papibe said:**
> find -type f -iname "makefile" -exec grep -H "confedit" '{}' \;

Thanks a lot papibe, it worked :)

I have 2 questions though:
1. I don't have to add the -print option,correct ? (I think it worked for me by adding -H alone, but since you said "good catch", I'm a bit confused)
2. Can you tell me what **'{}' \;** means towards the end of the command ?

Thanks.

---

### Post by papibe on 2013-05-16
> **IAMTubby said:**
> 1. I don't have to add the -print option,correct ?
You don't have to.
> **IAMTubby said:**
> 2. Can you tell me what **'{}' \;** means towards the end of the command ?
In the context of the -exec option the string '{}' represents the file that has been match. '\;' is the syntax to mark the end of the exec command.

Does that help?
Regards.

---

### Post by IAMTubby on 2013-05-16
> **papibe said:**
> 
In the context of the -exec option the string '{}' represents the file that has been match. '\;' is the syntax to mark the end of the exec command.

Thanks a lot papibe, it's clear now. :)

---

### Post by ofnuts on 2013-05-17
Also:
```

shopt -s globstar
grep -l "confedit" **/makefile

```

(with the "globstar" option "**" expands recursively to all the directories in the tree).

---

### Post by IAMTubby on 2013-05-21
> **papibe said:**
> 
find -type f -iname "makefile" -exec grep -H "confedit" '{}' \;

papibe, I'm sorry to reopen this thread again.
Ever since, you told me of the above command, I have been using it extensively with great success.

But I would like to know how you can give a pattern to search within the makefile.
To find all makefiles containing a reference to anything ending with **.lo**, I tried doing **find -type f -iname "makefile" -exec grep -H "*.lo" '{}' \;** but couldn't get the desired result.

Surprisingly, the pattern works when I'm only using find, as in, to find all files ending with **.lo**, this works 
**find ./ -name '*.lo' 2>/dev/null** works and lists everything ending with **.lo**

---

### Post by ofnuts on 2013-05-21
Replace the '*' by   backslash
```

[B]find -type f -iname "makefile" -exec grep -H "\.lo" '{}' \;

```

[/B]"*.lo" looks for the string "*.lo", not for any string that ends with ".lo".

---

### Post by papibe on 2013-05-21
> **ofnuts said:**
> 
```
**find -type f -iname "makefile" -exec grep -H "\.lo" '{}' \;**
```
+1

---

### Post by IAMTubby on 2013-05-21
> **ofnuts said:**
> Replace the '*' by   backslash
```

[B]find -type f -iname "makefile" -exec grep -H "\.lo" '{}' \;
[/B]
```"*.lo" looks for the string "*.lo", not for any string that ends with ".lo".

> **papibe said:**
> +1

Thanks a lot ofnuts, papibe :)
But just so that I can  try out a few things by myself, I have a question.
1.Please check this link [http://www.cyberciti.biz/faq/howto-find-a-file-under-unix/](http://www.cyberciti.biz/faq/howto-find-a-file-under-unix/) which has this command, **[COLOR=#111111][FONT=Consolas]$ find . -type f -name '*.pl'[/FONT][/COLOR]** Why is it that * works for pattern matching here? 
2.So we are using **/** for pattern matching in the answer you gave above ?

---

### Post by prodigy_ on 2013-05-21
> **IAMTubby said:**
> Why is it that * works for pattern matching here?
**-name** uses shell (bash) pathname expansion while **-regex** uses regular expressions.

Bash pathname expansion is similar to Windows wildcards expansion but has its quirks. I'd suggest you to read [Bash Manual](http://www.gnu.org/software/bash/manual/bashref.html). It's a lot of text but without it you're using a tool you know little about.

Regular expressions are way more complex and far more powerful. Consult grap manpage (**man grep** command) and check [Perl Manual](http://perldoc.perl.org/perlre.html).

---

### Post by papibe on 2013-05-22
If the expressions were not quoted, all of them would fall under the same rule: bash expressions.

However, each program has its own rules on how to expand expressions. The way to protect the expression (specially if it has asterisks) is to quote them so they are not expand by bash, and can be used by each respective program.

In the case of the command 'find' both the -iname and -name options use very simple pattern matching. However, it has other options that allow it to use POSIX expressions (like grep). For example:
```
find -regextype posix-egrep -regex  '.*/[Mm]akefile'
```
Does that help?
Regards.

Caveat: note that -name works over the single file name, whereas -regex matches over the whole path.

---

### Post by ofnuts on 2013-05-22
> **papibe said:**
> If the expressions were not quoted, all of them would fall under the same rule: bash expressions.

Mostly they would be subject to shell filename expansion in the current directory... so the search ends up being not what you think.
If you current directory has one single foo.c in the current directory, and you want to search for other .c files in subdirectories:
```

find -name *.c

```
is really seen by the find command as:
```

find -name foo.c

```
since the unquoted '*.c' is expanded before find is called. So find will only return foo.c files in the subdirectories. Of course, without any .c in your current directory, the '*.c' remains '*.c' even without quotes (assuming shopt 'nullglob' is not set) so the command works, and with several *.c files, find will complain about the syntax.
 
> **papibe said:**
> In the case of the command 'find' both the -iname and -name options use very simple pattern matching. However, it has other options that allow it to use POSIX expressions (like grep). For example:
```
find -regextype posix-egrep -regex  '.*/[Mm]akefile'
```

Not really a good example this bash supports this type of expressions directly, and so does find in -name expressions :)

---

### Post by IAMTubby on 2013-05-22
> **papibe said:**
> 
Does that help?

> **prodigy_ said:**
> **-name** uses shell (bash) pathname expansion while **-regex** uses regular expressions.

> **ofnuts said:**
> Mostly they would be subject to shell filename expansion in the current directory... so the search ends up being not what you think.

Please be a bit patient with me, if I don't get it even after one more explanation, I shall go and spend a few hours reading it.

I tried the following command to search for the word 'greptest' in all files except c files recursively from the current directory.
**find ./ -type f ! -name '*\.c' -print0 | xargs -0 -l grep 'greptest'**
But I'm getting the same output even with
**find ./ -type f ! -name '*.c' -print0 | xargs -0 -l grep 'greptest'**

Because of this, I'm not able to understand the meaning of **slash(/)** to represent a file ending with .c(same as my question in my previous post)

I'm sorry to ask the question again, but I'm still finding it a bit difficult even after writing a few commands.

Thanks.

---

### Post by IAMTubby on 2013-05-22
i was able to figure it out, please wait for a few minutes for me to post my answer/understanding and then you may reply

---

### Post by IAMTubby on 2013-05-22
Sorry for multiple spams by me, but this is my understanding.My question was why **slash(/) is used**

_What I understand is that_, 
*** ? .** etc are special characters.
If you want the following meanings, then you need not mention any slash etc. ie, "*c" would mean anything ending with c, like ''spec''
```

 (dot)will match *any single character*, equivalent to ? (question mark) in standard wildcard expressions. Thus, "m.a" matches "mpa" and "mea" but not "ma" or "mppa".
\ (backslash)is used as an "escape" character, i.e. to protect a subsequent special character. Thus, "\\" searches for a backslash. Note you may need to use quotation marks and backslash(es).
.* (dot and asterisk)is used to match any string, equivalent to * in standard wildcards.
* (asterisk)the proceeding item is to be matched *zero or more* times. ie. n* will match n, nn, nnnn, nnnnnnn but not na or any other character.
^ (caret)means "the beginning of the line". So "^a" means find a line starting with an "a".
$ (dollar sign)means "the end of the line". So "a$" means find a line ending with an "a".
For example, this command searches the file myfile for lines starting with an "s" and ending with an "n", and prints them to the standard output (screen):

```

But, if you want a word to contain a pattern like "*c", then your pattern should be like "\*c"
Similarly, if you want to accommodate the pattern like word ending with the extension ".lo", your pattern should be like "\.lo"

Thanks a lot. Please correct me if I'm wrong.

---

### Post by steeldriver on 2013-05-22
PMJI

That's not really it - the difference is whether you are using a regex based search or a glob based search. For example if we have

```
$ ls
myfile.c

```

```

$ find . -name '*.c'
./myfile.c

```

is a glob-style pattern match, in which * means any characters and . means a literal period; whereas

```
$ find . -regex '.*\.c'
./myfile.c

```

is a regex based search in which . means "any single character" and * means "zero or more instances of the previous regex" and \. means a literal period. If you try

```

$ find . -regex '*.c'

```

it doesn't work because the symbols are interpreted with their regex meanings. However 

```
$ find . -name '*\.c'
./myfile.c

```

does work, because it's OK to escape the period (even though in this case it doesn't need escaping because -name is a non-regex predicate).

Hope this helps

---

### Post by Vaphell on 2013-05-22
```
                         **GLOB**                     **REGEX**
                  ( shell file matching     ( sed, grep, awk, perl, ...
                    **find -name** )              **find -regex** )
--------------------------------------------------------------------------------------
line start                                        ^
line end                                          $
dot                       . (\. works too)        \. or [.]
any char                  ?                       .
any sequence              *                       .*
escaped (literal) X       \X                      \X
'a' or 'b' or 'c'         [abc]                   [abc]
a-z, A-Z                  [a-zA-Z]                [a-zA-Z]
0-9                       [0-9]                   [0-9]
not-XYZ                   [^XYZ]                  [^XYZ]
'abc' or 'def'                                    abc|def 
0-or-more of X                                    X*  
0-or-1 of X                                       X?
1-or-more of X                                    X+
X n times                                         X{n}
X n-m times                                       X{n,m}
```


there are also POSIX char classes like [:space:],[:alpha:],[:digit:] etc. supported by both globs and regexes
[http://www.regular-expressions.info/posixbrackets.html](http://www.regular-expressions.info/posixbrackets.html)
\X in general means escaped X, eg \.='.', \[ = '[' but at least some flavors of regexes also support shorthands for char classes eg
```
\s = whitespace     \S = not-whitespace
\d = digit          \D = not-digit
\w = word-chars     \W = not-word-chars 
```

regex flavors differ in things like meaning  of + vs \+ (some consider + as quantifier and \+ as literal +, other do the opposite), {} vs \{\}, personally i go with ones that have the special meaning as default, i hate seeing loads of \'s
sed -r
grep -E(xtented) or grep -P(erl)
find -regextype posix-extended

---

