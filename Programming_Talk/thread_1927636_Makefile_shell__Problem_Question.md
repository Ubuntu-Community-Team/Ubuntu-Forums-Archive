---
title: "Makefile shell  Problem Question"
date: 2012-02-18
forum: Programming Talk
---

### Post by celem on 2012-02-18
I have a makefile in which I am trying to automate a variable assignment with some shell script. This particular script line works fine from the shell command line but produces a null result when invoked from within the Makefile. Any ideas?

```

in shell:

$ x=`for f in $(grep \#include softserialtest.ino); do if [ "$f" = \#include ]; then continue; fi; ff=$(echo "$f"|sed "s:.*#include.*<::"|tr -d "<\">"); echo -n "$(basename "$(find "/home/ecomer/arduino/arduino-1.0/libraries/" -name "${ff}")" .h) "; done`
ecomer@pennyroyal:~/arduino/arduino-1.0/sketchbook/softserialtest$ echo $x
SoftwareSerial
$

but in Makefile:

ARDUINO_LIBS2 := $(SHELL `for f in $(grep \#include softserialtest.ino); do if [ "$f" = \#include ]; then continue; fi; ff=$(echo "$f"|sed "s:.*#include.*<::"|tr -d "<\">"); echo -n "$(basename "$(find "/home/ecomer/arduino/arduino-1.0/libraries/" -name "${ff}")" .h) "; done` )
...
# Next target is for debugging. For example, Entering make print-AVRDUDE_CONF
# yields: AVRDUDE_CONF = [/yourpath/hardware/tools/avrdude.conf]
print-%:
	@echo $* = [$($*)]

$ make print-ARDUINO_LIBS2
ARDUINO_LIBS2 = []
$ 

Leaving out the grave accents around the bash script also yields NULL

```

---

### Post by r-senior on 2012-02-18
First thing I'd try is making sure make is using the same shell as your command line. I'm going to guess that make is defaulting to /bin/sh which is a symbolic link to /bin/dash on Debian-based distros. But your command prompt is probably /bin/bash.

You can specify Bash as the shell for make with the following in your makefile:

```
SHELL = /bin/bash
```

---

### Post by celem on 2012-02-18
It is. My first lines in the Makefile are:
#WARNING: This makefile is bash shell dependant!
SHELL := /bin/bash
.SHELLFLAGS := -c

---

### Post by StephenF on 2012-02-18
$f will expand from the Makefile variable rather than be fed literally to the subshell.
Example Makefile.
```

f = "hello"

all:
        @f="goodbye" ; echo "$f $$f"

```

---

### Post by celem on 2012-02-18
Thanks for the reply but I don't see the relevance. When run from bash, my problem statement outputs the string "SoftwareSerial" which, I felt, should have been assigned to ARDUINO_LIBS2. I just did another simple test in the makefile:

DEMO = $(shell echo "hello world" )

which results in:
$ make print-DEMO
DEMO = [hello world]

How is $(shell echo "hello world" ) assigning its output to the makefile variable "DEMO" any different from my problem example? They both output test when run from bash?

> **StephenF said:**
> $f will expand from the Makefile variable rather than be fed literally to the subshell.
Example Makefile.
```

f = "hello"

all:
        @f="goodbye" ; echo "$f $$f"

```

---

### Post by celem on 2012-02-18
In examining my most recent post, I realized that my "demo" test used shell rather than SHELL. I switched it to SHELL and I got no output from it either.

Previously, shell would not work, complaining of syntax errors so I had to define:
SHELL := /bin/bash

When I used $(SHELL ... or $($SHELL) ... I got no syntax errors but I also got no output. Thus the problem is centered around  shell/SHELL

---

### Post by celem on 2012-02-18
A few examples of the problem, trying SHELL several different ways:

---------------------------
SHELL=/bin/bash
...

ARDUINO_LIBS2 := $(**SHELL** for f in...
...
$ make print-ARDUINO_LIBS2
ARDUINO_LIBS2 = []
$

ARDUINO_LIBS2 := $(**shell** for f in...
...
$ make print-ARDUINO_LIBS2
Makefile:135: *** unterminated call to function `shell': missing `)'.  Stop.
$ 

ARDUINO_LIBS2 := $(**$(SHELL)** for f in...
...
$ make print-ARDUINO_LIBS2
ARDUINO_LIBS2 = []
$ 

$ make print-SHELL
SHELL = [/bin/bash]
$

---

### Post by StephenF on 2012-02-19
> **celem said:**
> How is $(shell echo "hello world" ) assigning its output to the makefile variable "DEMO" any different from my problem example? They both output test when run from bash?
This script will run on any machine not just yours.

```

a="" ; for f in $(find /lib -maxdepth 1 -name "libc*") ; do a="$a $f" ; done ; echo $a

```

Outputs on my machine: 
/lib/libcrack.so.2.8.1 /lib/libcap.so.2.22 /lib/libcrypt-2.13.so /lib/libc.so.6 /lib/libcrack.so.2 /lib/libc-2.13.so /lib/libcidn.so.1 /lib/libcidn-2.13.so /lib/libcom_err.so.2.1 /lib/libcap.so.2 /lib/libcom_err.so.2 /lib/libcrypt.so.1

Broken makefile:
```

LIBLIST := $(shell a="" ; for f in $(find /lib -maxdepth 1 -name "libc*") ; do a="$a $f" ; done ; echo $a)

all:
	@echo $(LIBLIST)

```
Outputs on my machine a blank line.

Working makefile:
```

LIBLIST := $(shell a="" ; for f in $$(find /lib -maxdepth 1 -name "libc*") ; do a="$$a $$f" ; done ; echo $$a)

all:
	@echo $(LIBLIST)

```
You have two layers of expansion. One in the makefile and one in the sub-shell. $f and $a both expand to nothing as makefile variables so you may as well imagine the sub-shell script running as if you had never typed them in.

---

### Post by celem on 2012-02-19
StephenF:

I see that I needed '$$' in the shell script but a parsing error still eludes me.

**This works in a terminal:**
```

for f in $$(grep \#include softserialtest.ino)\
do if [ "$$f" = \#include ]\
   then\
      continue\
   fi\
   ff=$$(echo "$$f"|sed "s:.*#include.*<::"|tr -d "<\">")\
   echo -n "$$(basename "$$(find "/home/ecomer/arduino/arduino-1.0/libraries/" -name "$${ff}")" .h) "\
done

```

But, when placed within a Makefile, it gives the same error that is has all along - "**Makefile:135: *** unterminated call to function `shell': missing `)'.  Stop.**"
```

	ARDUINO_LIBS2 := $(shell for f in $(grep \#include softserialtest.ino); \
do if [ "$$f" = \#include ]; \
   then continue; \
   fi; \
   ff=$(echo "$$f"|sed "s:.*#include.*<::"|tr -d "<\">"); \
   echo -n "$(basename "$(find "/home/ecomer/arduino/arduino-1.0/libraries/" -name "$${ff}")" .h) "; \
done )

```

I assume that make is interpreting one of the parenthesis or quotes in the script, but I can't see which or where.

---

### Post by celem on 2012-02-19
I solved the problem with "unterminated call to function", it was make interpreting the '#' as a comment. Escaping it with a backslash solved that. Now the Makefile runs but returns a null result, even though the same code run from a terminal returns the correct data.

Line from Makefile:
```

	ARDUINO_LIBS2 := $(shell for f in $(grep "\#include" softserialtest.ino); \
	do if [ "$$f" = "\#include" ]; \
	then continue; \
	fi; \
	ff=$(echo "$$f"|sed "s:.\#include.*<::"|tr -d "<\">"); \
	echo -n "$(basename "$(find "/home/user/arduino/arduino-1.0/libraries/" -name "$${ff}")" .h) "; \
	done )

```

---

### Post by celem on 2012-02-19
SOLVED! The following works:

```

	ARDUINO_LIBS2 := $(shell for f in $$(grep "\#include" $(TARGET).$(SUFFIX)); \
	do if [ "$$f" = "\#include" ]; \
	then continue; \
	fi; \
	ff=$$(echo "$$f"|sed "s:.\#include.*<::"|tr -d "<\">"); \
	echo -n "$$(basename "$$(find "/home/user/arduino/arduino-1.0/libraries" -name "$${ff}")" .h) "; \
	done )

```

I needed '$$' in ALL cases!

*The bottom line is that, even within a shell script, make considers a '#' as the start of a comment and it gobbles up the first of each '$' encountered, requireing that, within the shell script, that every '#' be escaped with a backslash and every '$' be doubled with '$$' to feed make's appetite for '$'s.*

**A special Thank You to StephenF for starting me down the right path.**

---

