---
title: "Makefile help"
date: 2009-01-07
forum: Packaging and Compiling Programs
---

### Post by reldon on 2009-01-07
I am attempting to understand how a part of a makefile works.  Can anybody explain what this section of code in my makefile does??  I understand from reading that it basically does substitution but can't find any exact info.  Like why the semicolons?  Are the forward slashes just line contiuation characters?  Also, what is the reason for the double pipe symbols before the remove (rm -f $@) command??

According to one text I guess the search group is:  \($*\)\.o[ :]*
And the replace section would be:  \1.o $@ : 
But why the forward slashes, colons, ampersands, and asterisks????

This is the exact text from the makefile...

%.d: %.c
	set -e; $(CC) -I. -M $(CPPFLAGS) $< \
	| sed 's/\($*\)\.o[ :]*/\1.o $@ : /g' > $@; \
	[ -s $@ ] || rm -f $@
ifneq ($(MAKECMDGOALS),clean)
include $(SRCS:.c=.d)
endif

Any help would be greatly appreciated...  !!

---

### Post by KIAaze on 2009-01-09
This is pretty complex, so excuse me if I don't explain everything.
It is actually more of a bash + sed problem, than a Makefile problem.

_**1) Double pipes:**_
The double pipes are an "OR" statement similare to the double & "AND" statement.

They can be used in shellscripts like this:
```
#a=1 and b=2
if [ $a -eq 1 ] && [ $b -eq 2 ]
then
echo "FOO"
fi
#a=1 or b=2
if [ $a -eq 1 ] || [ $b -eq 2 ]
then
echo "FOO"
fi

```

Or on the command-line:
```
ls && echo "SUCCESS"
ls /nonexistentdir || echo "FAILURE"
make && zenity --info --text="Compilation successful" ||  zenity --info --text="Compilation failed"

```

_**2)Are the forward slashes just line continuation characters?**_
Just to be clear on the terms used:
forward slash="/"
backslash="\"

[LIST]
[*]Ending a line with "\" means the command continues on the next line. So "\" is a line continuation character.

[*]"\" is also more generally an "escape character". So it disables the new line characters, but also "(",")" and "." in the sed command.

[*]"\1" is a back-reference used in the sed command.

[*]The "/" used here are specific to the sed. They separate the different arguments.
[/LIST]

_**3)The different commands:**_
%.d: %.c -> target: dependent targets/files

Automatic variables: [http://www.gnu.org/software/make/manual/make.html#Automatic-Variables](http://www.gnu.org/software/make/manual/make.html#Automatic-Variables)
$@ -> target
$< -> first dependency
$* -> The stem in a pattern rule (i.e., whatever the '%' matched)

Semi-colons (";") separate the commands, so we have 4 different parts:

[LIST]
[*]set -e;
=>Exit on first error

[*]$(CC) -I. -M $(CPPFLAGS) $< | sed 's/\($*\)\.o[ :]*/\1.o $@ : /g' > $@;
=>Compile and process the output with sed and then save the sed output in "$@"

[*][ -s $@ ] || rm -f $@
=>If NOT(FILE exists and has a size greater than zero) (i.e: file doesn't exist or has a size of zero), then remove "$@"

[*]ifneq ($(MAKECMDGOALS),clean)
include $(SRCS:.c=.d)
endif
=>This one is new for me, but here's what it seems to be:
> The final line of the Makefile includes all the .d files: The $(SRCS:.c=.d) macro transforms the list of sources in the SRCS variable by changing the extension from .c to .d. The include also tells GNU Make to check to see if the .d files need rebuilding. GNU Make looks to see if there are rules to rebuild included Makefiles (in this case, the .d files), rebuilds them if necessary (following the dependencies specified in the Makefile), then restarts. This "Makefile remaking" feature (see section 3.7 "How Makefiles Are Remade" in the FSF's GNU Make manual; [http://www.gnu.org/software/make/manual/html_mono/make.html#SEC20](http://www.gnu.org/software/make/manual/html_mono/make.html#SEC20)) means that simply typing "make" will rebuild any dependency files that need rebuilding&#8212;but only if the sources have changed. Then, GNU Make will perform the build, taking into account the new dependencies.
Source: [http://www.ddj.com/linux-open-source/184406479](http://www.ddj.com/linux-open-source/184406479)

[/LIST]

Ok, now please stand by while I process the sed command, which is the one you seem to be interested in. :)

More Makefile syntax (makepp is for Perl I think, but the syntax seems similar to GNU make):
[http://makepp.sourceforge.net/1.19/makepp_variables.html](http://makepp.sourceforge.net/1.19/makepp_variables.html)
[http://makepp.sourceforge.net/1.40.1/makepp_statements.html](http://makepp.sourceforge.net/1.40.1/makepp_statements.html)

---

### Post by KIAaze on 2009-01-09
Ok, here is a simplified version of the Makefile with the sed command:
Makefile:
```
%.d : %.c
	sed 's/\($*\)\.o[ :]*/\1.o $@ : /g' $<  > $@;

```
I added "$<" as input file to replace the compilation output piped through in the original version.

hello.c:
```
hello.o: blabla
hello.o : blue
hello.o yes : red

```

Now, if you run:
```
make hello.d
```

You'll get a file named "hello.d".

hello.d:
```
hello.o hello.d : blabla
hello.o hello.d : blue
hello.o hello.d : yes : red

```

The command output shows the substitutions made in the sed command before it is run:
```
sed 's/\(hello\)\.o[ :]*/\1.o hello.d : /g' hello.c  > hello.d;
```

> According to one text I guess the search group is: \($*\)\.o[ :]*
And the replace section would be: \1.o $@ : 

Yes. So I'll assume, you know how the rest of sed works.
It's just that $* is the basename of the .c file and $@ the target name, i.e. the resulting .d file.

---

### Post by reldon on 2009-01-19
Thanks for your help..  

I am slowly beginning to understand some of the complexity of how linux is applied..

---

### Post by reldon on 2009-01-23
please mark as solved..

---

