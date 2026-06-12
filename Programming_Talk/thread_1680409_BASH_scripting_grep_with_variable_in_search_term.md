---
title: "BASH scripting: grep with variable in search term"
date: 2011-02-02
forum: Programming Talk
---

### Post by hailholyghost on 2011-02-02
Hey all,

I'm trying to get the following BASH script working:

"#!/bin/bash

i=1
for ((i=50; i<251; i+=50))
do
	#ptraj prmtop < extract.$i
	grep -v WAT $ins.wat.pdb.$i0 | grep -v TER > $ins.pdb
done"

I am trying to make snapshots of a molecular dynamics simulation every 50 nanoseconds to 250 ns.  The first command worked beautifully so its commented out.

The variable $i stands for 50, 100, 150, 200, and 250.  The files end in 500 for 50ns so that's why I put "$i0" in.

The problem is that I don't know how to put variables like $i into the "grep" function.  I've tried putting the escape character "\" in there but to no avail.

I'm a total n00b, any help is very much appreciated :cool:

---

### Post by gmargo on 2011-02-02
Try "${i}0" instead of "$i0".

---

### Post by hailholyghost on 2011-02-02
Hi gmargo!

Thanks for taking time to look at that for me.

The script, as
"
#!/bin/bash

i=1
for ((i=50; i<500; i+=50))
do
#ptraj prmtop < extract.$i
grep -v WAT ${i}ns.wat.pdb.${i}0 | grep -v TER > ${i}ns.pdb
done"

worked wonderfully.

Thank you so much gmargo!!!!

---

