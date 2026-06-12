---
title: "BASH variables within AWK"
date: 2012-03-23
forum: Programming Talk
---

### Post by hailholyghost on 2012-03-23
Hello,):P

```
	
#!/bin/bash

I am trying to read in shell variables by reading in the 2nd column of a file line by line.  The files look like

[CODE]0.10 165.517
0.20 165.764
0.30 181.885
...
0.90 162.31
1.00 149.89
```

I can read them in line by line by 
```
#!/bin/bash

for i in {1..9}
 do
	awk -v var="$i" 'NR==var {print $2*1000}' beta2.99
 done
```

but for some reason this script

```
#!/bin/bash

for i in {1..9}
 do
	zzz="$(awk -v var="$i" 'NR==var {print $2*1000}' beta2.99)"
	echo $zzz
 done
```

returns the error
```
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
./exp.sh: line 17: [: : integer expression expected
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
./exp.sh: line 17: [: : integer expression expected
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `{print' for reading (No such file or directory)
./exp.sh: line 17: [: : integer expression expected
```

How can I read in the AWK output into BASH variables?

Thanks for your time,
-Dave

---

### Post by Vaphell on 2012-03-23
in general that's exactly what you do - you capture the output with $() (no need to quote it, you need qoutes when you use the variable)

your snippet works for me
Could you paste your whole script? line 17 error in 5 line script does not compute. It looks like awk thinks that the script part ends earlier and {print is a file following the script part.

---

### Post by codemaniac on 2012-03-23
Cannot see any discrepancies in your codelet , as suggested by vaphell you can remove the double quotes while command substituting .
One thing just want to be sure , check if your input file beta2.99 is also in the same path where your bash script is .

---

### Post by hailholyghost on 2012-03-23
Hi Vaphell and codemaniac,
 [thanks for your prompt replies!]
the script in its entirety is:
```
#!/bin/bash

rm aform.lna.syn.99

for i in {1..9}
 do
	b2="$(awk -v var="$i" NR==var {print $2*1000}' beta2.99)"
	g2="$(awk -v var="$i" NR==var {print $2*1000}' gamma2.99)"
	b3="$(awk -v var="$i" NR==var {print $2*1000}' beta3.99)"
	g3="$(awk -v var="$i" NR==var {print $2*1000}' gamma3.99)"
	b4="$(awk -v var="$i" NR==var {print $2*1000}' beta4.99)"
	g4="$(awk -v var="$i" NR==var {print $2*1000}' gamma4.99)"
	d1h2p_2h1p="$(awk -v var="$i" NR==var {print $2*1000}' 02)"
	d2h2p_3h1p="$(awk -v var="$i" NR==var {print $2*1000}' 14)"
	d3h2p_4h1p="$(awk -v var="$i" NR==var {print $2*1000}' 07)"
	d1h1p_1h6="$(awk -v var="$i" NR==var {print $2*1000}' 11)"
	if [ "$b2" -lt "210000" ] && [ "$b2" -gt "150000" ] && [ "$g2" -lt "75" ] && [ "$g2" -gt "35" ] &&  [ "$b3" -lt "210000" ] && [ "$b3" -gt "150000" ] && [ "$g3" -lt "75" ] && [ "$g3" -gt "35" ] && [ "$b4" -lt "210000" ] && [ "$b4" -gt "150000" ] && [ "$g4" -lt "75" ] && [ "$g4" -gt "35" ] && [ "$d1h2p_2h1p" -lt "4.8" ] && [ "$d1h2p_2h1p" -gt "3.8" ] && [ "$d2h2p_3h1p" -lt "4.8" ] && [ "$d1h2p_3h1p" -gt "3.8" ] && [ "$d3h2p_4h1p" -lt "4.8" ] && [ "$d3h2p_4h1p" -gt "3.8" ] && [ "d1h1p_1h6" -gt "3.3"] && [ "d1h1p_1h6" -lt "3.9" ] ;
         then
		echo $i | awk '{print $0/10, "1"}' >> aform.lna.syn.99
	 else
		echo $i | awk '{print $0/10, "0"}' >> aform.lna.syn.99
	fi
 done
```

This script runs VERY slowly on am almost brand-new hard drive, and it doesn't even have all of the necessary conditions yet.  Perhaps Perl would be a better choice?
-Dave

---

### Post by Vaphell on 2012-03-23
it is slow because you run awk multiple times only to extract single value at a time. That's as inefficient as possible :)
go through the file(s) at once, extract all values into bash array(s) and then you can do whatever you want with them.

```
$ b2=( $( awk 'NR<10 { print $2*1000 }' beta2.99 ) )
$ echo ${b2[@]}
165517 165764 181885 162310 149890
$ echo ${b2[0]} ${b2[3]}
165517 162310
$ echo ${!b2[@]}
0 1 2 3 4

```

as you can see arrays are indexed from 0
also in bash you can use (()) to do anything integer related, like (( a++ )) or (( x < y )) instead of fugly square bracket -gt -lt -eq conditions ;-)

```
echo $i | awk '{print $0/10, "1"}'
```

in case of {1..9} awk is unnecesary, **echo "0.$i 1"** will do the same

---

### Post by sisco311 on 2012-03-24
Check out BashFAQ 001, 022 and 089 (link in my signature).

I'd try something like:
```
while read _ b2; do
    read <&3 _ g2
    read <&4 _ b3
    read <&5 _ g3
...
done < beta2.99 3< gamma2.99 4< beta3.99 ...

```

---

