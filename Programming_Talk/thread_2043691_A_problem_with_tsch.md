---
title: "A problem with tsch"
date: 2012-08-17
forum: Programming Talk
---

### Post by Bduke on 2012-08-17
I have a rather specific problem, and I think this form may be too general, so help in moving it to a more specific forum would be appreciated. I came across a set of csh scripts that were giving an incorrect result. Basically the script searches output for a the value of a specific variable that is printed and compares it with a known result and a tolerance. It should report  failure if the absolute difference from the known result is greater than the tolerance. The scripts reported that the test was not a failure even though the values it reported should have lead to failure being reported.

I have now discovered that on Ubuntu 12.04, the bug shows up when the scripts use tcsh but not if I use the older BSD csh, which is available as an alternative csh. Note, if that alternative is not installed, csh is a soft link to tsch.

I wrote two small scripts that reproduce the error:-

test

```

#!/bin/tcsh
set E0=1.0
set E=2.0
set tol=0.5
set ierr=0
set Eerr=`./chk $E $E0 $tol`
if($status != 0) set ierr=1
echo $ierr

```

chk

```

#!/bin/tcsh
set diff=`echo $1 $2 | awk '{ if($1>$2) printf "%.1e",$1-$2 ; else printf "%.1e",$2-$1 }'`
exit `echo $diff $3 | awk '{ if($1>$2) print 1 ; else print 0 }'`

```

E - E0 is greater than tol, but running these prints "0". Changing tcsh to csh prints "1" as it should. If E0 is changed to 1.9, so E - E0 is less than tol, both tcsh and csh print "0".

This is with  tsch 6.17.06. So csh gives the correct result and tcsh gives an incorrect result.

I can not test other versions of tsch on Ubuntu, but on Suse, with tsch 6.15.00 and 16.17.02, it gives the correct response of "1" if E - E0 is greater than tol and "0" is E - E0 is less than tol. 

So, is this a problem only with tsch 6.17.06? Or is it a Ubuntu problem.  Could someone run the "test" script with other versions of tsch and perhaps earlier Ubuntu versions? Can anyone throw any light on this?

Note, I do not want to be told to use the bash script. I know it would be better, but the actual scripts I use are quite complex and they come with a large fortran program along with a lot of scripts that are all csh scripts and the authors are not going to change to bash. In total there would be nearly 70 scripts to rewrite.

Regards, Brian Duke

---

### Post by steeldriver on 2012-08-17
quick bit of googling finds this - I can't find anything Ubuntu-specific but it sounds exactly like what you are seeing

[http://stackoverflow.com/questions/11411346/in-tcsh-how-do-you-get-the-exit-status-of-a-command-in-backquotes](http://stackoverflow.com/questions/11411346/in-tcsh-how-do-you-get-the-exit-status-of-a-command-in-backquotes)

so it looks like to get the default csh behaviour you need to use
```
set anyerror
```at least until the change is reverted

---

### Post by Bduke on 2012-08-17
Many thanks for a quick reply. What a strange error. I am glad that it will be reverted in the 6.18 release of tsch. I did try googling, but your google skills are clearly better than mine. I will try adding "set anyerror" to three scripts that may need it to check whether it fixes the real problem, but if it works, It will need the developers of this package to add it to about 70 scripts.

Thanks, Brian

---

### Post by sisco311 on 2012-08-17
Thread moved to **Programming Talk**.

---

