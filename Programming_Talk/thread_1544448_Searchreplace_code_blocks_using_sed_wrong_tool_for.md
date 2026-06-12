---
title: "Search/replace code blocks using sed: wrong tool for the job?"
date: 2010-08-02
forum: Programming Talk
---

### Post by Phasmus on 2010-08-02
So here's the deal, I have a skeleton source file that needs to be customized for specific purposes/systems using a shell script.  The variable parts of the file are tagged like this:
@DO_SOMETHING_SYSTEM-SPECIFIC@
Sed finds that easily and can replace it with any simple string equally easily.  The problem is I need to replace tags like that with blocks of code, including spaces, newlines, special characters, the works.  

Escaping everything for sed's benefit would be tedious, unreadable and unmaintainable (and escaping spaces doesn't seem to work anyway).  This would be trivial using python or java, but I need to use the lowest common denominator (bash, sed, etc) for implementation.  Does anyone know how to do a simple replacement of one literal string with another in the shell?

---

### Post by DaithiF on 2010-08-02
Hi,
I agree that something like python would be a better tool for the job.  
But if it has to be shell, you could possibly get there using sed's 'r' command to read text from a file for the replacement content.

So it could work something like:
1. for each search expression put the replacement content into its own separate file
2. have a file which maps from the search expressions to the filename with replacement contents, e.g.:

```
@DO_SOMETHING_SYSTEM-SPECIFIC@  replace-file1
@DO_SOMETHING_ELSE@  replace-file2

```

then a script like:
```
while read pattern filename
do
   sed "/$pattern/{r $filename
   ;d}" sourcefile
done < file_with_replacemappings
```

(add -i param to sed to make in-place updates to the file if this approach is at all useful)

also, this assumes that the search/replace strings are whole lines, if they can be partial lines then it gets a little more complicated.

---

### Post by alphaniner on 2010-08-02
I use sed in a script that creates a web page.  The only thing I really have to escape is double quotes.  I don't know if this will be of any help, but here's an example:

```
sed -e "s|${N}|<!--\"${A3}\"--><div class=\"img\"><div>${THUMB}</div><div class=\"desc\"><div class=\"name\"><a href=\"${A1}\">${A3}</a></div><div class=\"links0\"><
div class=\"links1\">${M}</div></div><div class=\"info\">${D} --- ${C}</div></div></div>\n&|" ${TTemp} >${PTemp0}
```

---

### Post by ghostdog74 on 2010-08-02
> **Phasmus said:**
> So here's the deal, I have a skeleton source file that needs to be customized for specific purposes/systems using a shell script.  The variable parts of the file are tagged like this:
@DO_SOMETHING_SYSTEM-SPECIFIC@
Sed finds that easily and can replace it with any simple string equally easily.  The problem is I need to replace tags like that with blocks of code, including spaces, newlines, special characters, the works.  

Escaping everything for sed's benefit would be tedious, unreadable and unmaintainable (and escaping spaces doesn't seem to work anyway).  This would be trivial using python or java, but I need to use the lowest common denominator (bash, sed, etc) for implementation.  Does anyone know how to do a simple replacement of one literal string with another in the shell?

show an example of the source, show what you want to change from that example, then show your desired output. An example speaks more than a thousand words you write.

---

### Post by Phasmus on 2010-08-03
Thanks for the input so far folks.  The file-read idea is cool, but I have a lot of little snippets I'm substituting and part of the goal is to simplify this code base (yeah, again, I know sed is less than ideal) so that might not be the way to go.  Here's a pretty basic example of what I'm trying to do.

In my hypothetical skeleton file, comp.skel, I have a line line this ():

	  -MM | -V | --version | -dumpversion @VERSDUMPEXT@)

In the script that turns the skeleton into a script of its own I define this variable:

VERSDUMPEXT="| -M | -print-prog-name=ld | -print-search-dirs"

Ideally I could do:

cat comp.skel | sed -e 's,@VERSDUMPEXT@,'$VERSDUMPEXT',' > comp.sh

and get a comp.sh where the line has become:

-MM | -V | --version | -dumpversion | -M | -print-prog-name=ld | -print-search-dirs)

If it were just one line and I didn't care who could read it the escaping and tweaking for sed would be fine, but I want a general solution that's easy to maintain.  I don't need proper regex matching here, just a string-literal search and replace so it's irritating to have no clean solution.  

One area where I may need to rethink is use of variables to contain my substitution text.  I really like this for readability and ease of use (if I want to generate a new script I can just copy and edit my block of variables).  But there are some issues with escaping inside variables.  For example:

$ export COMPILERTYPE="Fortran 77"
$ echo $COMPILERTYPE
Fortran 77
$ export COMPILERTYPE="Fortran\ \77"
$ echo $COMPILERTYPE
Fortran\ ?
$ export COMPILERTYPE="Fortran\\ \\77"
$ echo $COMPILERTYPE
Fortran\ ?

This is probably a dash specific problem, but of course it'd be nice if this system would work on Ubuntu as well...

---

### Post by ljrmorgan on 2010-08-03
Couldn't you use the g option in sed - that will do a global replace - something like:
cat comp.skel | sed "s/@VERSDUMPEXT@/'$VERSDUMPEXT'/g"
that'll replace all instances.

Sorry if I'm missing the point... (probably am)

---

### Post by ljrmorgan on 2010-08-03
> **ljrmorgan said:**
> Couldn't you use the g option in sed - that will do a global replace - something like:
cat comp.skel | sed "s/@VERSDUMPEXT@/'$VERSDUMPEXT'/g"
that'll replace all instances.

Sorry if I'm missing the point... (probably am)

Or you could run
```
sed -e "s/@VERSDUMPEXT@/'$VERSDUMPEXT'/g" comp.skel > comp.sh
```

or stick all your substitutions into a file called subs.sed, and run
```
sed -f subs.sed comp.skel > comp.sh
```

---

### Post by Jacobian on 2010-08-03
I wonder if you would be better off writing a short script?

For example, you could perform a literal text search in Python. This would give you a great deal of flexibility.

Here is a code sample to get you started:
```
#!/usr/bin/env python

# Libraries
import os
import re

if __name__ == "__main__":

	f = open('filename', 'r')
	text = f.read()
	f.close()
```

At this point, you can do a search and replace on the text string.

Here are some functions which may be useful:
[string.find]("http://docs.python.org/library/string.html#string.find")
[re]("http://docs.python.org/library/re.html")

---

