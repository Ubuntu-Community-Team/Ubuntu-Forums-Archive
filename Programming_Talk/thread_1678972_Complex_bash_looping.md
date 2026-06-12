---
title: "Complex bash looping"
date: 2011-01-31
forum: Programming Talk
---

### Post by hailholyghost on 2011-01-31
Hey all,

I'm running a molecular dynamics simulation 200 times.  I'd like to automate this in a BASH script, but I can't find a tutorial online that would let me loop the following command:

The first command would go:

[con@malatya02]$ mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_1.out -p prmtop -c inpcrd -r anneal_1.rst -x siman_1.mdcrd > /dev/null

the second would go:

[con@malatya02]$ mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_2.out -p prmtop -c anneal_1.rst -r anneal_2.rst -x siman_2.mdcrd > /dev/null

...

until the 200th is

[con@malatya02]$ mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_200.out -p prmtop -c anneal_199.rst -r anneal_200.rst -x siman_200.mdcrd > /dev/null

The variables in each argument within the command are inter-related (i.e. the output from command X is the input for command X+1, so the nearest I can figure is to declare variables i and j, and loop them like i++ and j++ but I'm not even sure how to do that!

any help is appreciated ;)

---

### Post by Arndt on 2011-01-31
> **hailholyghost said:**
> Hey all,

I'm running a molecular dynamics simulation 200 times.  I'd like to automate this in a BASH script, but I can't find a tutorial online that would let me loop the following command:

The first command would go:

[con@malatya02]$ mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_1.out -p prmtop -c inpcrd -r anneal_1.rst -x siman_1.mdcrd > /dev/null

the second would go:

[con@malatya02]$ mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_2.out -p prmtop -c anneal_1.rst -r anneal_2.rst -x siman_2.mdcrd > /dev/null

...

until the 200th is

[con@malatya02]$ mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_200.out -p prmtop -c anneal_199.rst -r anneal_200.rst -x siman_200.mdcrd > /dev/null

The variables in each argument within the command are inter-related (i.e. the output from command X is the input for command X+1, so the nearest I can figure is to declare variables i and j, and loop them like i++ and j++ but I'm not even sure how to do that!

any help is appreciated ;)

Maybe this:

```
#!/bin/bash

i=1
MAX=200

mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_1.out -p prmtop -c inpcrd -r anneal_1.rst -x siman_1.mdcrd > /dev/null

while [ $i -lt $MAX ];
do
    i1=`expr $i + 1`

    mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_$i1.out -p prmtop -c anneal_$i.rst -r anneal_$i1.rst -x siman_$i2.mdcrd > /dev/null

    i=$i1
done

```

There are more advanced looping constructs in bash, but this uses only old Bourne shell sh things.

---

### Post by hailholyghost on 2011-01-31
Thanks Arndt!

Unfortunately the script you gave didn't work, it kept saying that it didn't recognize the .rst files.

I modified it slightly:

"#!/bin/bash

i=1
j=2
MAX=200

while [ $i -lt $MAX ];
do
    mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_$j.out -p prmtop -c anneal_$i.rst -r anneal_$j.rst -x siman_$j.mdcrd > /dev/null

done"

I got a little farther, but unfortunately this just keeps cycling through anneal_2.  I've also tried 

1) removing the ">/ dev/null"
2) replacing while [ $i -lt $MAX ];

with 

while [ $i -lt $MAX ];
while [ $j -lt $MAX ];

but neither of those worked (just returned "line 13: syntax error: unexpected end of file").

Got anything else up your sleeve? lol

Thanks for trying :)

---

### Post by Arndt on 2011-01-31
> **hailholyghost said:**
> Thanks Arndt!

Unfortunately the script you gave didn't work, it kept saying that it didn't recognize the .rst files.

I modified it slightly:

"#!/bin/bash

i=1
j=2
MAX=200

while [ $i -lt $MAX ];
do
    mpirun -np 4 sander.MPI -O -i anneal.in -o anneal_$j.out -p prmtop -c anneal_$i.rst -r anneal_$j.rst -x siman_$j.mdcrd > /dev/null

done"

I got a little farther, but unfortunately this just keeps cycling through anneal_2.  I've also tried 

1) removing the ">/ dev/null"
2) replacing while [ $i -lt $MAX ];

with 

while [ $i -lt $MAX ];
while [ $j -lt $MAX ];

but neither of those worked (just returned "line 13: syntax error: unexpected end of file").

Got anything else up your sleeve? lol

Thanks for trying :)

I may have made some mistake in adapting your commands, but try removing >/dev/null and putting an "echo" in front of them so you can see if they are the commands you wanted

---

### Post by hailholyghost on 2011-01-31
Hey Arndt, 

I got it!

A for loop worked great:

"#!/bin/bash

i=1
j=2

for ((i=1, j=2; i<200; i++, j++))
do
	mpirun -np 4 sander.MPI -O -i anneal.in -o anneal$j.out -p prmtop -c anneal$i.rst -r anneal$j.rst -x siman$j.mdcrd > /dev/null
done"

Thanks so much for your help!

I really appreciate it!!!

-Dave

---

