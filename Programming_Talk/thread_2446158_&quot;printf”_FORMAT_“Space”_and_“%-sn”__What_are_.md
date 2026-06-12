---
title: "&quot;printf” FORMAT: “Space” and “%-s\n”  What are these parts meaning?"
date: 2020-06-25
forum: Programming Talk
---

### Post by Captain Cookie on 2020-06-25
Although I am learning shell scripts, there is a sample line that I can not understand in a tutorial on the page below.
[http://linuxcommand.org/lc3_wss0130.php](http://linuxcommand.org/lc3_wss0130.php)

Could anybody tell me the first line's meaning in the code below? 
These lines are modified from the original code to shorten.

```

format="%8s%10s%10s   %-s\n"
printf "$format" "Dirs" "Files" "Blocks" "Directory"

total_dirs=$(find $HOME -type d | wc -l)
total_files=$(find $HOME -type f | wc -l)
total_blocks=$(du -s $HOME)

printf "$format" $total_dirs $total_files $total_blocks

```
###


My questions are about the second half of the fist line.


1) About the usage of "space":


If there are 3 spaces between $3 and $4 in the "format", the outputted line also has 3 space between $3 and $4? 
 
2) About "%-s\n" part:


What is the meaning of "-(hyphen)" in this sample code?
I got same output result, even if I removed it.

###

Thank you for reading and I am waiting for your help!

---

### Post by TheFu on 2020-06-26
The manpage for bash has a section for printf which explains the format stuff.  printf formats usually follow the C-style printf() function, so format explanations for the C version usually are correct too.
```

       printf [-v var] format [arguments]
              Write the formatted arguments to the standard output  under  the
              control  of  the  format.  The -v option causes the output to be
              assigned to the variable var rather than being  printed  to  the
              standard output.

              The  format  is a character string which contains three types of
              objects: plain characters, which are simply copied  to  standard
              output,  character  escape  sequences,  which  are converted and
              copied to the standard output, and format  specifications,  each
              of  which  causes  printing of the next successive argument.  In
              addition to the standard printf(1) format specifications, printf
              interprets the following extensions:
```

printf(1) format spec is a reference to the section 1 manpage for "printf"

%s  is a string.
%Ns is a string limited to the number specified as 'N', right justified
%-Ns is a string limited to the number specified as 'N', left justified> 
       -      The converted value is to be left adjusted on the  field  bound&#8208;
              ary.  (The default is right justification.)  The converted value
              is padded on the right with blanks, rather than on the left with
              blanks or zeros.  A - overrides a 0 if both are given.
   Field width
       An optional decimal digit string (with nonzero first digit)  specifying
       a  minimum  field  width.   If the converted value has fewer characters
       than the field width, it will be padded with spaces  on  the  left  (or
       right, if the left-adjustment flag has been given).

Not sure I’d trust du to return blocks.

---

### Post by Captain Cookie on 2020-08-08
Hello The Fu!  Now I've tried several format settings based on the information you provided, then I understood  printf's basic behavior.
You have helped me on other question. Thank you for lots of your supports! 
I have written study scripts, so I want to utilize the printf too.

---

