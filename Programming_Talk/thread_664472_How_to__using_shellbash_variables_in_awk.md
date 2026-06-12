---
title: "How to : using shell/bash variables in awk"
date: 2008-01-11
forum: Programming Talk
---

### Post by Claus7 on 2008-01-11
Hello,

I was trying to use shell variables and "pass" them to an awk pattern. In order to do so I did the following :

read step
echo $step

awk -v t=$step '{print t}'
awk "/$step/,/2000/" input > output_$step.txt

Watch out the double " " marks that enclose the pattern!

Helpful link:
[http://sunsite.ualberta.ca/Documentation/Gnu/gawk-3.1.0/html_chapter/gawk_8.html#SEC115](http://sunsite.ualberta.ca/Documentation/Gnu/gawk-3.1.0/html_chapter/gawk_8.html#SEC115)

EDIT: in case we want to use more than one variable in awk then we have to type -v in front of each variable we want to use. For example if we have x and y variables then the above example becomes:
awk -v x=$x -v y=$y '{print...} file1 > file2

Regards!

---

