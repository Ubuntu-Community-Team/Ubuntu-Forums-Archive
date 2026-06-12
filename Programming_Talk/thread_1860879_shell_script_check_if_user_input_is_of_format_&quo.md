---
title: "shell script: check if user input is of format &quot;int int int int&quot;"
date: 2011-10-15
forum: Programming Talk
---

### Post by CryptKeeper777 on 2011-10-15
I want the user to type in four numbers with spaces in between ("int int int int"). How do I check if the input fulfills this format?

I've successfully checked for the validity of a (y/n) input using
```

if [[ $input == "y" ]]; then
    echo "hell yeah!"
elif [[ $input == "n" ]]; then
    echo "damn..."
else
    "you're stupid! try again."
fi

```
so I'm familiar with the principle, but checking if it's "int int int int" is a bit more complicated than just checking it matches a particular string...

---

### Post by Vaphell on 2011-10-15
```
$ x="    0       1 2222 333     "
$ if echo $x | egrep -q '^[0-9]+ [0-9]+ [0-9]+ [0-9]+$'; then echo OK; else echo FAIL; fi
**OK**
$ a=$( echo $x ); rgx='^[0-9]+ [0-9]+ [0-9]+ [0-9]+$'; if [[ "$a" =~ $rgx ]]; then echo OK; else echo FAIL; fi
**OK**

$ x="0 0 0 0 0"
$ if echo $x | egrep -q '^[0-9]+ [0-9]+ [0-9]+ [0-9]+$'; then echo OK; else echo FAIL; fi  
**FAIL**
$ a=$( echo $x ); rgx='^[0-9]+ [0-9]+ [0-9]+ [0-9]+$'; if [[ "$a" =~ $rgx ]]; then echo OK; else echo FAIL; fi
**FAIL**

```

there are 2 oneliners - one using grep, and one using bash =~
i assumed that any amount of whitespaces is legit, as long as there are 4 ints.

---

### Post by CryptKeeper777 on 2011-10-15
Thanks a lot for your fast reply. That's what I was looking for. I've also tried out if it matters how many spaces there are between the numbers: It doesn't matter. (the script calls the command pdfcrop and gives the values entered by the user to --margins)

I like the first of the two commands better, BTW. Could you please say some words on how the command works, especially the middle part which checks if there are four integers? It looks a bit cryptic to me...

---

### Post by Vaphell on 2011-10-15
both lines do pretty much the same thing - they check if x matches the pattern/regular expression. Google regular expressions and familiarize yourself with them, they prove very useful in anything even remotely related to text strings.

^[0-9]+ [0-9]+ [0-9]+ [0-9]+$
^ = start of line
$ = end of line
[0-9] = any char from 0-9 range (digit)
+ = 1 or more of preceding symbol (in this case 1 or more digit)
  
egrep = grep -e
grep is a tool that looks for occurences of expressions in files (eg. grep 'something' file1 file2) but you can also pass data to it via pipe (eg echo $x | grep ...  -> output of echo becomes input of grep) 
grep --help to get quick help with available options, google for tutorials to get the idea how grep is used.
i used -q (quiet) - didn't need grep to print the matching sequence, i only cared if it found it.

=~ is a bash operator that tests argument against the regex

---

### Post by CryptKeeper777 on 2011-10-15
Thanks for the detailed explanation. It was mainly the regular expression ^[0-9]+ ... $ that I didn't know. 

Could the expression easily be expanded to also accept floats, not just integers? It's not really necessary in the context of pdfcrop because increments of 5 are enough for my purpose, so there's no need for floating point numbers, but I'm curious.

---

### Post by Vaphell on 2011-10-15
floats as in there can be a dot in the middle? :-)
easy
[0-9] -> [0-9]+([.][0-9]+)?
one-or-more digit followed by 0-or-1 (dot,one-or-more digit)
? = 0 or 1
* = 0 or more
+ = 1 or more

if you want shorter expression try ```
^([0-9]+([.][0-9]+)?([ ]|$)){4}$
```
{4} means exactly 4 of (float followed by space or end_of_line)

---

