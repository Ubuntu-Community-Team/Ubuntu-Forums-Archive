---
title: "BASH skipping values in loop"
date: 2011-09-13
forum: Programming Talk
---

### Post by hailholyghost on 2011-09-13
Hello Linux experts):P,

I am attempting to extract segments of a large output file and put each segment into its own file.

My script:
```
#!/bin/bash

#pull out structures from Gaussian09 Scan.

for ((x=43, y=44; x<1200, y<1200; x+=43, y+=46))
do
 grep -A 43 'Z-MATRIX' structures.out | head -$x | tail -39 > tmp_Zmatrix
 CHI="`grep '11     11  C' tmp_Zmatrix | awk '{print $11}' | sed 's/.$//g'`"
 EPSILON="`grep '15     15  C' tmp_Zmatrix | awk '{print $11}' | sed 's/.$//g'`"
 ZETA="`grep '32     32  O' tmp_Zmatrix | awk '{print $11}' | sed 's/.$//g'`"
 echo $CHI $EPSILON $ZETA
 echo 39 > ppa18_chi$CHI\_epsilon$EPSILON\_zeta$ZETA.xyz
 echo ppa18_chi$CHI\_epsilon$EPSILON\_zeta$ZETA >> ppa18_chi$CHI\_epsilon$EPSILON\_zeta$ZETA.xyz
 grep -A 44 'Z-Matrix orientation:' structures.out | head -$y | tail -39 | awk '{print $2, $4, $5, $6}' | sed -e 's/^1 /H /g' -e 's/^6/C/g' -e 's/^7/N/g' -e 's/^8/O/g' -e 's/^15/P/g' >> ppa18_chi$CHI\_epsilon$EPSILON\_zeta$ZETA.xyz
 rm tmp_Zmatrix
done

```

The problem, I think, is in the for loop title (something about different steps being used).  I used the "echo" line as a function check.  As you can see, it skips certain values (the first two columns shouldn't change):

```

62.990 179.970 -179.140
62.990 179.970 -164.740
62.990 179.970 -150.340
62.990 179.970 -135.940
62.990 179.970 -121.540
62.990 179.970
62.990 179.970
62.990 179.970
62.990 179.970 -78.340
62.990 179.970 -63.940
62.990 179.970 -49.540
62.990 179.970 -35.140
62.990 179.970 -20.740
62.990 -6.340
62.990 8.060
22.460
179.970 36.860
179.970 51.260
62.990 179.970 65.660
62.990 179.970 80.060
62.990 179.970 94.460
62.990 179.970 108.860
62.990 179.970 123.260
62.990 179.970 137.660
62.990 179.970 152.060
62.990 179.970 166.460

```

I have checked the file structures.out and the data *is* there, but the script isn't extracting and reporting like it should.  I don't understand why it does this for some lines, and not others.

How can I change the script to get all values to appear?

Thanks for your expertise!
-Dave

---

### Post by Vaphell on 2011-09-13
holy crap :)
advice: stop using backticks and use $() instead to capture command outputs

how big is the file? Can you create a simplified example that bugs your loop out?
some sample data would be cool. Either grep doesn't catch anything or awk spits out a single character which is destroyed by sed down the road.

---

### Post by hailholyghost on 2011-09-13
Hi Vaphell! 

thanks for replying!  I actually fixed that problem a few hours later.  Unfortunately, I ran into another one.  In Perl, I can add numbers to a variable rather easily.  However the same doesn't appear to be true in Bash.

I just want to add 360 to ZETA if it is less than 0, so all my numbers will be positive.  I've attempted to do this with an "if" conditional in line 12.  I've just included the important part:

```

...
 ZETA="`grep '32     32  O' tmp_Zmatrix | awk '{print $11}' | sed 's/.$//g'`"
	if ["$ZETA" -lt 0]; then
		ZETA=$(($ZETA + 360))
	fi
 ...
```

I've tried many different ways of adding 360 to something, this is so easy, it should work!!!

thanks for your time,
-Dave

---

### Post by Vaphell on 2011-09-13
drop if and go with modulo arithmetic
```
$ x=0; echo $(((x+360)%360))
0
$ x=-1; echo $(((x+360)%360))
359
$ x=700; echo $(((x+360)%360))
340

```

bash arithmetic works only with integers though

EDIT:
another way: echo the equation and pipe it to bc
```
$ x=-0.00001; echo "($x+360)%360" | bc
359.99999
$ x=-94.2; echo "($x+3600)%360" | bc
265.8


```

---

### Post by sisco311 on 2011-09-13
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

Oh, and learn more about awk, you can replace all the grep .. | sed .. | awk .. commands with a one awk. I'm not very good with awk, but intead of **grep foo | awk '{print $1}'** you can use **awk '/foo/{print $1}'** 

Also check out the links from my signature.

---

### Post by hailholyghost on 2011-09-13
Hi sisco311 and Vaphell!

thank you so much!!  Vaphell, your suggestion worked beautifully.

sisco311, I will improve the script once I get the time.  I have to modify the other 2 variables now, and get the output from this into the supercomputing cluster.

THANKS SO MUCH!!!

```
#!/bin/bash

#pull out structures from Gaussian09 Scan.

grep -A 41 'Z-MATRIX (ANGSTROMS AND DEGREES)' structures.out > zmat_list.txt
for ((x=44, y=44; x<1175, y<1200; x+=43, y+=46))
do
 head -$x zmat_list.txt | tail -39 > tmp_Zmatrix
 CHI="`grep '11     11  C' tmp_Zmatrix | awk '{print $11}' | sed 's/.$//g'`"
 EPSILON="`grep '15     15  C' tmp_Zmatrix | awk '{print $11}' | sed 's/.$//g'`"
 FALSEZETA="`grep '32     32  O' tmp_Zmatrix | awk '{print $11}' | sed 's/.$//g'`"
        ZETA="`echo "($FALSEZETA+360)%360" | bc`"
 echo $CHI $EPSILON $ZETA
 echo 39 > ppa18_X$CHI\_E$EPSILON\_Z$ZETA.xyz
 echo ppa18_X$CHI\_E$EPSILON\_Z$ZETA >> ppa18_X$CHI\_E$EPSILON\_Z$ZETA.xyz
 grep -A 44 'Z-Matrix orientation:' structures.out | head -$y | tail -39 | awk '{print $2, $4, $5, $6}' | sed -e 's/^1 /H /g' -e 's/^6/C/g' -e 's/^7/N/g' -e 's/^8/O/g' -e 's/^15/P/g' >> ppa18_X$CHI\_E$EPSILON\_Z$ZETA.xyz
 rm tmp_Zmatrix
done

```

---

