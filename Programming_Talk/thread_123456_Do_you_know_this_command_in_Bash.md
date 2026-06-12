---
title: "Do you know this command in Bash?"
date: 2006-01-30
forum: Programming Talk
---

### Post by tseliot on 2006-01-30
Hi, I'm a newbie in bash (and in programming in general) and I would like to know how I can replace some words with other ones in a text file without opening it with an editor.

For example I would like to change every "ciao" word in "text.txt" with an "hello" word and then either save the modified file or redirect the output to another file.

Is there a command (in bash) which does this?

Thanks in advance.

Alberto

---

### Post by alamba on 2006-01-30
Yes there is, I believe you can do this using pipes. Its pretty trivial. Unfortunately I'm not good at this. Try google for bash pipes if u're in a hurry or I'm sure someone would be able to give you the exact command here.

Akshay

---

### Post by toojays on 2006-01-30
There is no command built into bash to do this. However, the sed program was designed to do what you want.

To redirect the output to another file, you would run "sed -e 's/ciao/hello/g' input.txt >output.txt"

To save the modified file, you would use a special GNU extension: "sed -ie 's/ciao/hello/g' input.txt"

You can read the complete sed documentation [online](http://www.gnu.org/software/sed/manual/sed.html), or in Emacs' info mode, or by running "info sed".

---

### Post by tseliot on 2006-01-30
[QUOTE=toojays]There is no command built into bash to do this. However, the sed program was designed to do what you want.[/QUOTE]
...And the books I bought don't mention how to do this.

[QUOTE=toojays]To redirect the output to another file, you would run "sed -e 's/ciao/hello/g' input.txt >output.txt"

To save the modified file, you would use a special GNU extension: "sed -ie 's/ciao/hello/g' input.txt"

You can read the complete sed documentation [online](http://www.gnu.org/software/sed/manual/sed.html), or in Emacs' info mode, or by running "info sed".[/QUOTE]
Thanks I'll try it

EDIT: it WORKS GREAT! Thanks again now I can develop my little project!

---

### Post by jerome bettis on 2006-01-30
you can also use awk for this type of stuff.  i prefer awk over sed cause it has C like syntax and sed is kinda bizarre.  awk is pretty sweet check it out

cat input.txt | awk ' { gsub("oldtext", "nextext"); print $_ } ' > output.txt

---

### Post by slavik on 2006-01-30
or you can write perl :)

perl is sed, awk, shell, C all put in one. :)

it can also do db and stuff ... and a simple perl web server is like 10 lines of code ... take THAT apache and smoke it. :P

---

### Post by sas on 2006-02-02
In perl it'd be: 
perl -pi -e 's/ciao/hello/g' text.txt

---

### Post by Lord Illidan on 2006-02-02
[quote=tseliot]...And the books I bought don't mention how to do this.


Thanks I'll try it

EDIT: it WORKS GREAT! Thanks again now I can develop my little project![/quote]

What books have you got then?  Am wondering what to buy myself..

---

### Post by kvorion on 2006-02-02
[QUOTE=tseliot]For example I would like to change every "ciao" word in "text.txt" with an "hello" word and then either save the modified file or redirect the output to another file.

Alberto[/QUOTE]

I think
```
 perl -e `s/ciao/hello/g` > text.txt
``` should work.

We are using Perl regular expressions here. 

perl -e is simply to run the command on ur shell.
s/foo/bar/g;
replaces any occurrence of the exact character sequence foo in the "current string" by the character sequence bar; for example, foolish bigfoot would become barlish bigbart

---

### Post by tseliot on 2006-02-04
Thanks for the answers!

4 Lord Illidan: I'm using this book (I bought it on Amazon) "A Practical Guide to Linux  Commands, Editors, and Shell Programming" - Mark Sobell

The other book of mine is: "Running Linux" Oreilly

BTW I haven't read them all.

---

### Post by professor_chaos on 2006-02-04
for bash scripting i find this a useful resource.
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

