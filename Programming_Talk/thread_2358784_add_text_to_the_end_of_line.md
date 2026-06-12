---
title: "add text to the end of line"
date: 2017-04-17
forum: Programming Talk
---

### Post by peter_brickles on 2017-04-17
Seems simple but ive been searching for a good hour of so 

I have a text file and would like to add a string to the end of line  5 ( as an example)

to ake tings hard the line number we have to add the text to is stored in a variable cunningly name $Line_to_append

any ideas on how this could be accomplished gerp, awk sed ???

any help would be gratefully appreciated

---

### Post by TheFu on 2017-04-17
I won't do your homework, but a few ideas ...  

Many different ways to do this. Depends on which language(s)/tools are available.

Shell scripting: 
* split the file after line 5 into 2 files. 
* append to the 1st file whatever you want, then 
* concatenate the files back together.


Perl/Ruby/Python:
* Read the input file and output all the lines until line 5.
* If line == 5, then output the original contents, followed by the new text
* Return to reading the input file and output all the remaining lines.

I'd make the perl/ruby/python script a filter, so the output would be to stdout and could be redirected anywhere I wanted.

You could probably use head, tail, but I don't think gerp will do what you want. ;)  BTW, if you are going to be a programmer/script writer, attention to little details is very important.

There must be 50 other methods to accomplish this homework.

---

### Post by steeldriver on 2017-04-17
Do you understand how to do it in the simpler case (when the line number is not stored in a variable)? That would be a start - don't run before you can walk.

You can easily select lines by number (called *addressing*) in sed : [https://www.gnu.org/software/sed/manual/sed.html#Numeric-Addresses](https://www.gnu.org/software/sed/manual/sed.html#Numeric-Addresses)

You can select lines by their *record number* (NR) in awk

---

### Post by TheFu on 2017-04-17
> **steeldriver said:**
> Do you understand how to do it in the simpler case (when the line number is not stored in a variable)? That would be a start - don't run before you can walk.

You can easily select lines by number (called *addressing*) in sed : [https://www.gnu.org/software/sed/manual/sed.html#Numeric-Addresses](https://www.gnu.org/software/sed/manual/sed.html#Numeric-Addresses)

You can select lines by their *record number* (NR) in awk

Didn't know that the gnu version of sed supported modification by line number. Interesting. I don't recall that in the Unix versions of sed.

---

