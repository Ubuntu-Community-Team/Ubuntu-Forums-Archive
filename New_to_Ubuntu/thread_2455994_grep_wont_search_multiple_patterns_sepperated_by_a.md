---
title: "grep wont search multiple patterns sepperated by a newline"
date: 2021-01-01
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2021-01-01
Hello all,

This ones been annoying me for a while. grep is supposed to accept a list of patterns to search for with each separated by a newline, so I've tried the following syntax(s)...```
grep [PATTERN1\nPATTERN2\nPATTERN3] [INPUTFILE.TXT]
grep ["PATTERN1\nPATTERN2\nPATTERN3"] [INPUTFILE.TXT]
grep ["PATTERN1"\n"PATTERN2"\n"PATTERN3"] [INPUTFILE.TXT]
```...plus various other syntax(s) but none of them seem to work, I can only search for multiple strings using the '-E' option, as in...```
grep -E "PATTERN1|PATTERN2" [INPUTFILE.TXT]
```...can anyone guide me here?

---

### Post by Holger_Gehrke on 2021-01-01
That only works for "grep -F", which will search for fixed strings (so the 'patterns' are **not** regular expressions). Example:
```

ls -l|grep -F 'lrwx
public
Bilder'

```
which - if executed in my $HOME - would list one symbolic link, my public_html directory and my pictures directory.

You can also use the option '-f file_full_of_patterns' where file _full_of_patterns is a text file with multiple patterns one per line.

Holger

---

### Post by The Cog on 2021-01-01
The top answer here might be of help: [https://stackoverflow.com/questions/3717772/regex-grep-for-multi-line-search-needed](https://stackoverflow.com/questions/3717772/regex-grep-for-multi-line-search-needed)
In brief, use grep -zo to convert newlines to nulls and only output the found string.

---

### Post by jcdenton1995 on 2021-01-01
hmmm very annoying, my grep doesn't seem to respond to this!```
perrywinklesnoop@perrywinklesnoop-System-Product-Name:~$ ls|grep -F 'owl\n
> alpha\n
> grep'
grepfile

perrywinklesnoop@perrywinklesnoop-System-Product-Name:~$ ls|grep -E 'owl|alpha|grep'
alphazulu
grepfile
theowlandthepussycat
perrywinklesnoop@perrywinklesnoop-System-Product-Name:~$
```

As you can see, when I use 'grep -F' followed by a newline separated list, it will only return matches for the final item in the list, whereas when I use 'grep -E' it will return matches for all...

---

### Post by jcdenton1995 on 2021-01-01
Thanks, I've just given it a go but still grep will only print the strings which match the final line. I just find it really weird because the info pages literally state this is a feature of grep...> grep [OPTION...] [PATTERNS] [FILE...]

There can be zero or more OPTION arguments, and zero or more FILE
arguments.  The PATTERNS argument contains one or more patterns
separated by newlines, and is omitted when patterns are given via the
‘-e PATTERNS’ or ‘-f FILE’ options.  Typically PATTERNS should be quoted
when ‘grep’ is used in a shell command.

Since newline is also a
separator for the list of patterns, there is no way to match newline
characters in a text.

---

### Post by The Cog on 2021-01-01
Grep normally works on single lines. You will never find a \n with grep because it splits the input into lines before searching. Unless you use -z to convert \n to null.

---

### Post by jcdenton1995 on 2021-01-01
sorry there's a misunderstanding, I'm not trying to find newlines in the input data, but rather trying to specify a list of patterns to be searched for with each pattern in the list separated by a new line, which is what the grep documentation seems to suggest is the done thing.

---

### Post by Holger_Gehrke on 2021-01-01
I had previously just looked at the man page (which doesn't mention this way of specifying multiple patterns except for use in fixed string mode, though it mentions giving multiple -e PATTERN options). You're right, the info documentation mentions this. So I tried
```

ls -l|grep -E '^lrwx.*
\.db$
w{3}-data'

```
and got the expected results 
```

-rw-r--r--   1 holgeh holgeh   145408 Sep 16  2017 ereader[COLOR=#ff0000].db[/COLOR]
[COLOR=#ff0000]lrwxrwxrwx   1 holgeh holgeh       38 Nov  8  2019 PlayOnLinux's virtual drives -> /home/holgeh/.PlayOnLinux//wineprefix/[/COLOR]
drwxrwxr-x  19 holgeh [COLOR=#ff0000]www-data[/COLOR]   4096 Jul 10 15:19 public_html

```
The one thing I did differently from you was that I didn't put in '\n'. To grep '\n' doesn't have any special meaning, it would search for a literal 'n'.

Holger

---

### Post by The Cog on 2021-01-01
You are right, I misunderstood. Try this:
```
grep 'PATTERN1
PATTERN2
PATTERN3' INPUTFILE.TXT
```
or this which places newlines into the search string (note the dollar in front to fix up interpreting \n by bash)
```
grep $'PATTERN1\nPATTERN2\nPATTERN3' INPUTFILE.TXT
```

---

### Post by jcdenton1995 on 2021-01-02
> **Holger_Gehrke said:**
> I had previously just looked at the man page (which doesn't mention this way of specifying multiple patterns except for use in fixed string mode, though it mentions giving multiple -e PATTERN options). You're right, the info documentation mentions this. So I tried
```

ls -l|grep -E '^lrwx.*
\.db$
w{3}-data'

```
and got the expected results 
```

-rw-r--r--   1 holgeh holgeh   145408 Sep 16  2017 ereader.db
lrwxrwxrwx   1 holgeh holgeh       38 Nov  8  2019 PlayOnLinux's virtual drives -> /home/holgeh/.PlayOnLinux//wineprefix/
drwxrwxr-x  19 holgeh www-data   4096 Jul 10 15:19 public_html

```
The one thing I did differently from you was that I didn't put in '\n'. To grep '\n' doesn't have any special meaning, it would search for a literal 'n'.

I still can't get this to work but it's probably my syntax. I can't see  any '\' at the end of your first line, mine looks like  this...```
perrywinklesnoop@perrywinklesnoop-System-Product-Name:~$  grep -i 'owl\
> *****-cat' theowlandthepussycat
```

I know something is wrong because I cant tab to complete the name of the input file :sad: also rather amused to see I've been censored! (the asterisks aren't actually part of my syntax)

> **The Cog said:**
> You are right, I misunderstood. Try this:
```
grep 'PATTERN1
PATTERN2
PATTERN3' INPUTFILE.TXT
```
or this which places newlines into the search string (note the dollar in front to fix up interpreting \n by bash)
```
grep $'PATTERN1\nPATTERN2\nPATTERN3' INPUTFILE.TXT
```


This actually works! it was the '$' that I was missing. I thought that wrapping a string in quotes was sufficient to protect the meta-characters in it from being expanded by the shell? why is the '$' necessary? (or does the '$' ensure that '\n' *is expanded by the shell??*)

---

### Post by The Cog on 2021-01-03
> **jcdenton1995 said:**
> I thought that wrapping a string in quotes was sufficient to protect the meta-characters in it from being expanded by the shell? why is the '$' necessary? (or does the '$' ensure that '\n' *is expanded by the shell??*)
Exactly that. "man bash" is really hard to read unless you know what you are looking for. Try "man bash" and search for QUOTING (yes, capitals). There is this sentence:
> Words  of  the  form  $'string'  are  treated  specially.  The word expands to string, with backslash-escaped characters replaced as specified by the ANSI C standard.

---

### Post by Holger_Gehrke on 2021-01-03
From 'man bash', section "QUOTING":
> 
... Words  of the form $'string' are treated specially.  The word expands to string, with backslash-escaped characters replaced as specified by the ANSI C standard. ....

So, yes, the '$' makes the bash expand '\n' to a newline-character. (Don't know how often I've read that page over the years and never noticed this construct ...)

I don't have backslashes before the newlines in my example because those would make grep give me an error:"grep: Angehängter Backslash (»\«)" ('appended backslash'). Without the backslash your example would search for the patterns 'owl' and '*****-cat' in the file 'theowlandthepussycat'. If those aren't in there, you'd get no output.

Holger

---

### Post by TheFu on 2021-01-03
> **jcdenton1995 said:**
>  This actually works! it was the '$' that I was missing. I thought that wrapping a string in quotes was sufficient to protect the meta-characters in it from being expanded by the shell? why is the '$' necessary? (or does the '$' ensure that '\n' *is expanded by the shell??*)

Perhaps I missed it, but this is a bash-specific thing.  Other shells would do it different.  Bash expansion (regex/globbing) is mostly intuitive, until it isn't.

If it were me, I'd use egrep (the same as grep -E) which is for 'enhanced regex grep'. 2 fewer characters to type, 'eg{tab}' does the command completion fast.
```
       -E, --extended-regexp
              Interpret PATTERNS as extended regular  expressions  (EREs,  see
              below).

       -P, --perl-regexp
              Interpret  PATTERNS  as  Perl-compatible   regular   expressions
              (PCREs).   This option is experimental when combined with the -z
              (--null-data) option, and grep  -P  may  warn  of  unimplemented
              features.


```
This basically results in nearly python/perl regex handling, so there are fewer surprises. I know perl, so those regex are sometime needed, -P option, but that is seldom, since whenever a bash script gets over 1 page in length, I switch to perl for all the added capabilities like multi-line regex codes with comments. Perl hasn't been write-only in a very long time.

If multiple regex are needed, consider using multiple -e options, one for each.

---

### Post by jcdenton1995 on 2021-01-03
> **Holger_Gehrke said:**
> From 'man bash', section "QUOTING":

So, yes, the '$' makes the bash expand '\n' to a newline-character. (Don't know how often I've read that page over the years and never noticed this construct ...)

I don't have backslashes before the newlines in my example because those would make grep give me an error:"grep: Angehängter Backslash (»\«)" ('appended backslash'). Without the backslash your example would search for the patterns 'owl' and '*****-cat' in the file 'theowlandthepussycat'. If those aren't in there, you'd get no output.

Holger

Righhht now I've got it, I never realised you can just hit enter after typing the first pattern to move to a newline in the terminal (naturally I assumed this would just attempt to run an incomplete command), so is that specifically a function of grep, that it 'knows' when your giving pattern arguments, if you hit enter it should simply move to a new line?

Anyway we've established that one can search for multiple patterns in the following three ways...```
grep $'[PATTERN1]\n[PATTERN2]\n[PATTERN3]' [INPUTFILE]


grep '[PATTERN1]
[PATTERN2]
[PATTERN3]' [INPUTFILE]


grep -E '[PATTERN1]|[PATTERN2]|[PATTERN3]' [INPUTFILE]
```So that pretty much clears it up, thank you all for your help!

---

### Post by TheFu on 2021-01-03
This should work too:
```
grep -E -e [PATTERN1] -e [PATTERN2] -e [PATTERN3]  [INPUTFILE]
```
or if you want them on separate lines:
```
grep -E -e [PATTERN1] \
-e [PATTERN2] \
-e [PATTERN3]  \
[INPUTFILE]
```

Just ensure there isn't any whitespace after the normal line continuation character \.

---

### Post by Holger_Gehrke on 2021-01-04
> **jcdenton1995 said:**
> Righhht now I've got it, I never realised you can just hit enter after typing the first pattern to move to a newline in the terminal (naturally I assumed this would just attempt to run an incomplete command), so is that specifically a function of grep, that it 'knows' when your giving pattern arguments, if you hit enter it should simply move to a new line?


It's not a function of grep, grep isn't running yet. It's the shell (or probably the readline library that the shell uses for text entry) that recognizes the odd number of quotes as a sign that there's more to come.

Holger

---

