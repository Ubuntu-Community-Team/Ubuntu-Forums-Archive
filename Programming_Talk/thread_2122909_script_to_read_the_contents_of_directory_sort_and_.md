---
title: "script to read the contents of directory sort and convert them to pdf"
date: 2013-03-06
forum: Programming Talk
---

### Post by jamesbon on 2013-03-06
I am having a situation where I have some pdfs in a folder which are numbered systematically 

> 
document fd13.pdf  document fd30.pdf  document fd47.pdf
document fd14.pdf  document fd31.pdf  document fd48.pdf
document fd15.pdf  document fd32.pdf  document fd49.pdf
document fd16.pdf  document fd33.pdf  document fd50.pdf

I am writing a script to convert them into a pdf

script is following
```

#!/bin/bash
pdftk "document fd1.pdf" "document fd2.pdf" "document fd3.pdf" "document fd4.pdf" "document fd5.pdf" "document fd6.pdf"
 "document fd7.pdf" "document fd8.pdf" "document fd9.pdf" "document fd10.pdf" "document fd11.pdf" "document fd12.pdf" 
"document fd12a.pdf" "document fd12b.pdf" "document fd12c.pdf" "document fd12d.pdf" "document fd13.pdf" "document fd14.pdf" 
"document fd15.pdf" "document fd16.pdf" "document fd17.pdf" "document fd18.pdf" 
output out.pdf

```
this does work also,

my problem is first I do an ls on the directory 

ls ./  > script.sh



then I have to sort the numbers which are single digit then double ones because in such an ls output
**document fd11.pdf**
comes before [B]document fd1.pdf
[/B]and also to be able to use them into my script I have to add double quotes in file name " "
this part I have to do manually.

I want to automate the addition of double quotes to file names and take the file names in a sorted order,
how do I deal these two problems?

---

### Post by schragge on 2013-03-06
Provided that you don't have thousands of files in the directory (there's a limit on how many arguments xargs will put on one line, see *xargs --show-limits*)
```
ls -v|xargs -rd$'\n' sh -c 'pdftk "$@" output out.pdf' sh
```

---

### Post by jamesbon on 2013-03-06
Thanks for answering and it works also I am seeing this kind of use of xargs for the first time I read the man page of xargs too but could not find any option sh I want to know what does xargs sh -c `something` h do? why did you use sh and -c

---

### Post by schragge on 2013-03-06
[LIST]
[*]*ls -v* sorts files by version. 
[*]The command xargs launches is the shell (sh, it's */bin/dash* in Ubuntu). It could be bash, too. 
[*]*sh -c* executes one command and exits. 
[*]That one command is [COLOR=blue]pdftk "$@" output out.pdf[/COLOR] 
[*]All that comes after this are shell parameters. 
[*]The first one (sh) is actually $0. $1, $2, $3, and so on are supplied by xargs. 
[/LIST]
In this case, $0 could be anything. I've chosen [COLOR=blue]sh[/COLOR], but e.g. [COLOR=blue]jamesbon[/COLOR] would work, too:
```
ls -v|xargs -rd$'\n' sh -c 'pdftk "$@" output out.pdf' jamesbon
```
or even ```
ls -v|xargs -rd$'\n' sh -c '$0 "$@" output out.pdf' pdftk
```

---

