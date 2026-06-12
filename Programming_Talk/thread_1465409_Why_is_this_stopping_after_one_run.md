---
title: "Why is this stopping after one run?"
date: 2010-04-29
forum: Programming Talk
---

### Post by newport_j on 2010-04-29
The following script code I got off the internet for running a program and collecting data in gmon.out and moving to gmon.sum which has all the data. This is then run with gprof.


for i in 'seq 1 100'; do
  ./grab32
  mv gmon.out gmon.sum.$i
done

gprof -s ./grab32 gmon.out

gprof ./grab32 gmon.sum


However, it runs just one cycle and stops. The error is:

mv: target `100' is not a directory

I am not sure as to what it means. The script should run the program 100 times collecting the data as it goes. But it stops with only one run the that error message:

mv: target `100' is not a directory


Why is it doing this?

Obviously, I modified the program to fit my program name grab32, but that is all.

Why does it fail after one run?


Newport_j

---

### Post by limey_rick on 2010-04-29
Could it be the shell variable $i has a space leading the number?  The command would look like this:

mv gmon.out gmon.sum. 100

instead of this:

mv gmon.out gmon.sum.100

---

### Post by MadCow108 on 2010-04-29
seq has to be in backticks `seq...` not quotes 'seq..'

---

