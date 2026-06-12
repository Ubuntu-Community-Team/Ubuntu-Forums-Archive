---
title: "csh programming trouble"
date: 2009-06-12
forum: Programming Talk
---

### Post by perhaugaard on 2009-06-12
Dear users,

I do not know if this is the right forum to submit this question but I will try.

I have written a small program in csh that should help me do some calculations. Here is the part of my script with does not work as expected:

cat <<_EOF_ >! $prg
BEGIN {
n=0;
dftot=0.0;
dflim=1000;
}
{
df=(double)\$1;
n=n+1;
dftot=dftot+df;
if (dftot/n>2.0) dflim=df;
}
END { printf dflim;
}
_EOF_
cat $prg >! code.prg

cat data.dat | sort -n -r | awk -f $prg >$dflim
cat $dflim >! data.dflim

data.dat contains a series of data which is to be evaluated by $prg and sent as output to data.dflim. BUT nothing seem to happen and the only data written to data.dflim is 1000. I was expecting something else.

Does anyone have any idea of what can be wrong?


Any help is appreciated

/Per

---

### Post by ghostdog74 on 2009-06-12
what calculations are you doing. show examples. don't use csh.

---

### Post by perhaugaard on 2009-06-12
Hey,

Other people have told me not to use csh and I start to understand why :) But it is the language people I know use so... But which free Linux-programming language do you recommend?

I am actually using a daylighting program to extract data from a picture and doing calculations on these data and hereafter making a new picture using the new data. 

The part of the programme I uploaded is supposed to evaluate the data in data.dat and pass the evaluation of each data set in data.dat to a new file data.dflim.

data.dat looks like
9.5
9.3
2.1
0.8
etc.

I expect that each data set in data.dat will match data in data.dflim as:

data.dat     data.dflim
9.5             2
9.3             2
2.1             2
0.8            1000

I can allways e-mail or upload all files from my debugging mode.


/Per

---

### Post by ghostdog74 on 2009-06-12
you can use awk to do calculations. similar, if you have languages like Perl/Python on your systems, they can perform calculations better than using csh.

---

### Post by Arndt on 2009-06-12
> **ghostdog74 said:**
> you can use awk to do calculations. similar, if you have languages like Perl/Python on your systems, they can perform calculations better than using csh.

Yes. A common way of doing things is to use one language for everything (or most things, at least), for example Perl, or python, or awk. Another is to use sh for the logic (including file selection and input/output redirection), and call other programs (like expr or perl or awk or sed or python, etc) for the calculations (including text processing).

---

