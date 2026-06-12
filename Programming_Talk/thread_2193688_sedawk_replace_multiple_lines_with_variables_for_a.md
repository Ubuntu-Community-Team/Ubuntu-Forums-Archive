---
title: "sed/awk replace multiple lines with variables for a lammps - tfreq conversion script."
date: 2013-12-14
forum: Programming Talk
---

### Post by Arisinhell on 2013-12-14
[SOLVED]
(see post #6)

Hello!

Im trying to convert some datafiles from this format (lammps velocity files):

ITEM: TIMESTEP
1
ITEM: NUMBER OF ATOMS
924
ITEM: BOX BOUNDS pp pp pp
0 67.4728
0 62.565
0 45.105
ITEM: ATOMS type vx vy vz 
3.96234 2.15174 -3.08438 
4.81728 -4.71916 2.30628 
4.57479 2.70962 -0.816817
...
ITEM: TIMESTEP
2
ITEM: NUMBER OF ATOMS
924
ITEM: BOX BOUNDS pp pp pp
0 67.4728
0 62.565
0 45.105
ITEM: ATOMS type vx vy vz 
2.61854 3.17183 -2.45742 
-0.322279 1.69319 2.70096 
2.94569 -3.51979 0.784884 
.. ect

to this format:


"frame" "time" (eg  1 0)
3.96234 2.15174 -3.08438 
4.81728 -4.71916 2.30628 
4.57479 2.70962 -0.816817
...
"frame" "time" (eg  2 1)
2.61854 3.17183 -2.45742 
-0.322279 1.69319 2.70096 
2.94569 -3.51979 0.784884 
.. ect

Ive already made a bash script to do this:


#!/bin/bash
sed -e '/TIMESTEP/,+7d' velmps.dat > out   (deletes the first 8 lines from the text that needs to be deleted (total lines 9))

Atoms=924
timestep=.0032
framestep=4

for i in {1..2049}
do

Tline=`echo "scale=5; ($i+($i-1)*$Atoms)" | bc -l`;
Tframe=`echo "scale=5; ($i*$framestep)" | bc -l`;
Ttimestep=`echo "scale=5; ($i-1)*$timestep" | bc -l`;

sed -e ''$Tline's/.*/'$Tframe' '$Ttimestep'/' out > out.tmp
mv out.tmp out

done
mv out myrun.vel 


but it is really unsophisticated and way to slow (takes from 40-90 mins!)
Can you please show me an alternative based on sed or awk?

something like:

sed/awk 
(i from 1 to number) 
{
replace the "function[i]" line with the text "(function1[i] function2[i]"
}

Thanks a lot in advance!

---

### Post by steeldriver on 2013-12-14
I don't really understand your conversion specification (it would be much easier to follow if you used ```
 tags in your post!) however if you're trying to separate the file into records that you can then process further with your bash script, you could use gawk to split it based on string ...\n as a **record separator** (regular awk doesn't allow multi-character record separators iirc) and possibly ITEM: as a field separator e.g.

[CODE]
$ gawk 'BEGIN{RS="[.][.][.]\n"; FS="ITEM: "} {print $5}' file.lampps 
ATOMS type vx vy vz
3.96234 2.15174 -3.08438
4.81728 -4.71916 2.30628
4.57479 2.70962 -0.816817

ATOMS type vx vy vz
2.61854 3.17183 -2.45742
-0.322279 1.69319 2.70096
2.94569 -3.51979 0.784884 

```

You could probably do the calculations easier right in awk as well, rather than using bash / bc

---

### Post by Arisinhell on 2013-12-14
Thanks for the fast reply!

Well to be clear i just need a script to (for example):

replace the 1st line of a file with "1" "space" "2"
replace the 11th line of the same file with "5" "space" "4"
replace the 21th line of the same file with "9" "space" "6"
..
replace the (1+10*i)th line of the same file with "1+i*4" "space" "2*(i+1)"
..
replace the (1+10*n)th line of the same file with "1+n*4" "space" "2*(n+1)"

assuming i goes from 0 to n

Those functions of i are just examples.

---

### Post by erind on 2013-12-15
> **Arisinhell said:**
> Thanks for the fast reply!

Well to be clear i just need a script to (for example):

replace the 1st line of a file with "1" "space" "2"
replace the 11th line of the same file with "5" "space" "4"
..
replace the (1+10*i)th line of the same file with "1+i*4" "space" "2*(i+1)"

[...]
Those functions of i are just examples.

I'm not completely sure what you're after, but based on your examples you can try this:

```

awk ' /ITEM: TIMESTEP/ { flag=0 }
                  flag { print }
      /ITEM: ATOMS type/ { flag=1; print 1+(i*4) " " 2*(i+1); i++ }

    '  velmps.dat
```

Output:
```

**1 2**
3.96234 2.15174 -3.08438
4.81728 -4.71916 2.30628
4.57479 2.70962 -0.816817
...
**5 4**
2.61854 3.17183 -2.45742
-0.322279 1.69319 2.70096
2.94569 -3.51979 0.784884
...

```


Going off the script in your first posting, you can insert the variables in awk like so:

```
Atoms=924
timestep=.0032
framestep=4

awk -v atoms="$Atoms" -v timest="$timestep" -v framest="$framestep"   '

      /ITEM: TIMESTEP/ { flag=0 }
                  flag { print $0 }
      /ITEM: ATOMS type/ { flag=1; print (i+(i-1)*atoms) " " (i*framest) " " ((i-1)*timest); i++ }

    '  velmps.dat
```

If you need a floating point number with a given precision printed out, use printf, say for precision 5 it'd be: ```
printf "%.5f", (i+1)...
```
[https://www.gnu.org/software/gawk/manual/html_node/Control-Letters.html#Control-Letters](https://www.gnu.org/software/gawk/manual/html_node/Control-Letters.html#Control-Letters).

---

### Post by Arisinhell on 2013-12-16
Thanks a lot!
That was exactly what i was looking for!

Ill adjust the script and then ill post it for other users to see..

---

### Post by Arisinhell on 2013-12-16
[SOLVED]

ok here's the full code for anyone interested.
Its much faster than the on at the OP (secs instead of hours)
__________________________________________
#~/bin/bash
#  PROGRAM lammps2tfreq velocity converter
#  1) dump the velocity on lammps every "FrameStep" frames with a timestep of "TimeStep" as (for ex.):
#      *dump dvel all custom 4 velmps.dat vx vy vz*
#  2) run the script to produce the velocity file (myrun.vel) compatible with tfreq. 

#  Set the Parameters
FrameStep=4
TimeStep=0.0008

#  Start

Time=$(awk 'BEGIN { print '$FrameStep'*'$TimeStep' }')

awk '
      /ITEM: TIMESTEP/ { flag=0 }
      flag { print }
      /ITEM: ATOMS/ { flag=1; print 1+(i*'$FrameStep') " " (i*'$Time'); i++ }
    ' velmps.dat > myrun.vel

#  END
echo "Done!"
_____________________________________________
Thanks a lot, you may close the thread now.

---

