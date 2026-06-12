---
title: "Bad fd number"
date: 2010-04-23
forum: Programming Talk
---

### Post by panos80 on 2010-04-23
Hi All,

I'm having a problem when trying certain Perl scripts. More specifically, when the Perl script tries to run a 'system' function that contains the redirection (?) symbol '>&' I get the following error message: 

```

sh: Syntax error: Bad fd number

```

I'm using bash so I don't really understand why would I get an error message from sh...

If I modify the system function so that it doesn't contain the '>&' symbol (and any subsequent files, of course) then the command executes but the files that were supposed to be generated are not and the script crashes anyway!

Any ideas?

---

### Post by ju2wheels on 2010-04-29
I assume you want to redirect stdout and stderr to the same file, in which case ">&" is incorrect syntax as it says because what you really would want is "&>" such as in this example:

```

perl someperscript.pl &> alloutput.txt

```

---

### Post by slavik on 2010-04-29
> **ju2wheels said:**
> I assume you want to redirect stdout and stderr to the same file, in which case ">&" is incorrect syntax as it says because what you really would want is "&>" such as in this example:

```

perl someperscript.pl &> alloutput.txt

```
well, if you do >& you need to add a number ...

for example '>&2' would redirect stdout to stderr.

---

