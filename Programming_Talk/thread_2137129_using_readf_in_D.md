---
title: "using readf in D"
date: 2013-04-19
forum: Programming Talk
---

### Post by checoimg on 2013-04-19
Hi guys! I'm writing a little program in D from another version I did  for my homework written in C. But it doesn't work very well. First it  takes two reads for the first input from the user and second it only  calculates tcsleep. I compiled it with GDC and DMD and got the same result. Thank you in advance!

```
import std.stdio;
import std.c.stdlib;
void main()
{
immutable sitc = 1.66;
immutable sleepc = 1.08;
float tcsleep, tcsit, tc;
int minsleep, minsit;
write("Input number of minutes sleep : \n");
readf("%d ", &minsleep);

write("Input number of minutes sitting : \n");
readf("%d ", &minsit);

write("Thanks!\n");
tcsleep = minsit*sitc;
tcsit = minsleep*sleepc;
tc = tcsleep+tcsit;
writeln("Your total calories is : ", tc);
exit (0);
}
```

---

### Post by checoimg on 2013-04-20
Solved!

---

