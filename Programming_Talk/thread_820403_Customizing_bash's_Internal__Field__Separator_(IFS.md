---
title: "Customizing bash's Internal  Field  Separator (IFS)"
date: 2008-06-06
forum: Programming Talk
---

### Post by Lars Noodén on 2008-06-06
I'm running into some weirdness trying to explicitly set the special variable in bash, the Internal  Field  Separator to be a space, a new line and a tab.  This is in GNU bash, version 3.2.39(1)-release (x86_64-pc-linux-gnu)

I would like to be able to explicitly set the Internal Field Separator to be a space, a new line and a tab.  I would expect the backslash sequences to be interpreted, but they seem not to be. Despite many HOWTOs, Tutorials, and guides only setup 'one' below successfully assigns all three.  

  # one
  export IFS=`/bin/echo -ne " \t\n"`
  echo "$IFS" | cat -vte

These others below fail, usually by making the letters 't' and 'n' into field separators.  That is not the behavior I expect, I would expect the backslash sequences to be interpreted properly:

  # two
  export IFS=" \t\n"
  echo "$IFS" | cat -vte

  # three
  export IFS=$" \t\n"
  echo "$IFS" | cat -vte

  # four
  export IFS=$' \t\n'
  echo "$IFS" | cat -vte

Here is the problem in a different form:

  $ FOO=$'a\n a';echo $FOO
  a a
  $ FOO=$"a\n a";echo $FOO
  a\n a
  $ FOO="a\n a";echo $FOO
  a\n a
  $ FOO='a\n a';echo $FOO
  a\n a

---

### Post by geirha on 2008-06-06
Seems to be working for me.
```

$ IFS=$' \t\n' FOO=$'a b\tc\nd-e'; echo $FOO
a b c d-e
$ IFS=' ' FOO=$'a b\tc\nd-e'; echo $FOO
a b	c
d-e
$ IFS=$'\t' FOO=$'a b\tc\nd-e'; echo $FOO
a b c
d-e
$ IFS=b FOO=$'a b\tc\nd-e'; echo $FOO
a  	c
d-e

```

---

### Post by colo on 2008-06-06
Also note that bash's default IFS already consists of " \t\n".

---

### Post by Lars Noodén on 2008-06-06
@geirha: on which platform and for which version of bash is it working for you?  

I am finding that it does not work on 

GNU bash, version 3.2.39(1)-release (x86_64-pc-linux-gnu)

2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

$ lsb_release -rcd
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy

---

### Post by Lars Noodén on 2008-06-06
> **colo said:**
> Also note that bash's default IFS already consists of " \t\n".

Yes.  However, for scripts, I wish to explicitly set the IFS, but without having to backtick output from echo.

---

### Post by geirha on 2008-06-06
> **Lars Noodén said:**
> @geirha: on which platform and for which version of bash is it working for you?  

I am finding that it does not work on 

GNU bash, version 3.2.39(1)-release (x86_64-pc-linux-gnu)

2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

$ lsb_release -rcd
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy

GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)

2.6.24-18-386 #1 Wed May 28 19:30:01 UTC 2008 i686 GNU/Linux

Ubuntu 8.04

---

### Post by Lars Noodén on 2008-06-06
> **geirha said:**
> GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)

2.6.24-18-386 #1 Wed May 28 19:30:01 UTC 2008 i686 GNU/Linux

Ubuntu 8.04

Hmm. I'm finding that it does work for a different architecture:

$ uname -a ;lsb_release -rc
Linux oin 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
Release:        7.10
Codename:       gutsy
maintenance@oin:~$ uname -a ;lsb_release -rc;bash --version
Linux oin 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
Release:        7.10
Codename:       gutsy
GNU bash, version 3.2.25(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.

---

### Post by Lars Noodén on 2008-06-06
Thanks for helping to walk through the problem.

The failure to interpret backslash escapes happens when starting the shell script with just sh
#!/bin/sh

/bin/sh is really dash, not bash
   [https://launchpad.net/ubuntu/+spec/dash-as-bin-sh](https://launchpad.net/ubuntu/+spec/dash-as-bin-sh)
 
So, changing the first line to the following gets rid of the problem:
#!/bin/bash


I guess that not interpreting backslash escapes is supposed to be normal behavior for dash?

---

### Post by ghostdog74 on 2008-06-06
for hassle free delimiter parsing, use awk.

---

### Post by HalPomeranz on 2008-06-06
Btw, this syntax works:

```

#!/bin/bash

IFS=$' \t\n'

```

---

### Post by Lars Noodén on 2008-06-11
@Hal:

Yes.  Thanks.  I found that the default #!/bin/sh actually goes to dash, not bash as I had thought.  So I had been accidentally testing in bash and scripting in dash.

dash is about 99KB and bash is about 796KB so I will try dash for both and adjust the syntax accordingly.

FWIW, ksh weighs in at 1.2 MB.

---

### Post by texaganian on 2010-08-17
> **HalPomeranz said:**
> Btw, this syntax works:

```

#!/bin/bash

IFS=$' \t\n'

```

What is that $' syntax and what does it do? I see it used for setting IFS but I've never seen it explain _anywhere_.

---

### Post by DaithiF on 2010-08-18
from **man bash**:
>        Words of the form $'string' are treated specially.  The word expands to
       string, with backslash-escaped characters replaced as specified by  the
       ANSI  C  standard.  Backslash escape sequences, if present, are decoded
       as follows:
              \a     alert (bell)
              \b     backspace
              \e     an escape character
              \f     form feed
              \n     new line
              \r     carriage return
              \t     horizontal tab
              \v     vertical tab
              \\     backslash
              \'     single quote
              \nnn   the eight-bit character whose value is  the  octal  value
                     nnn (one to three digits)
              \xHH   the  eight-bit  character  whose value is the hexadecimal
                     value HH (one or two hex digits)
              \cx    a control-x character


---

### Post by caine0001 on 2012-09-22
When I set IFS='\n' it just erases all the lowercase letter n's from the text. If I use an uppercase N then it separates 2 lines at the newline spot and starts a second line. Why do I have to use an uppercase N and everyone else can use the lowercase?

---

### Post by Vaphell on 2012-09-23
my take on the issue is: if you have to manipulate IFS, most likely you are doing it wrong. Care to explain what do you need it for exactly?

besides it's not '\n', but $'\n'

---

