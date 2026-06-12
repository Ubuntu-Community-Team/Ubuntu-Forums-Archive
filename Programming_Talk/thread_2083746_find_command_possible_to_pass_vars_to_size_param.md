---
title: "find command: possible to pass vars to size param ?"
date: 2012-11-13
forum: Programming Talk
---

### Post by thaitang on 2012-11-13
I want to determine the most common size (bracket) of files in a dir and would like to be able to write a loop but I wonder if it is possible to pass $vars to the size parameter in find like I pasted below?
```
let avgNum=10
let loSz=10000
let hiSz=19000
while [[ "$avgNum" -lt 110 ]]; do
	fNum=`find . -maxdepth 1 -type f -name "*.html" -size +'$loSz' -size -'$hiSz' | wc -l`
	echo "$fNum"
	let avgNum+=10
	let loSz+=10000
	let hiSz+=10000
done

```

Also, for the the $fNum var how might I go about appending the current value of $avgNum to the var name so each iteration the $fNum would actually read something like $fNum10 then $fNum20 and so on.

thanx
tt

---

### Post by Vaphell on 2012-11-13
yes, but you need to use double quotes or skip them entirely - single quotes make their content literal, $var won't be substituted by its value.
that said, your approach is wasteful as it will scan the same dirs/file over and over again.

---

### Post by thaitang on 2012-11-14
Ok so I managed to get the find command to work with vars by enclosing the vars in curly braces:
```
fNum=`find . -maxdepth 1 -type f -name "*.html" -size +${loSz} -size -${hiSz} | wc -l`
```
neither single, double, nor no quotes worked.

I am thinking of dumping the results to an array, but of all the bash array examples and tuts I have read none show nor mention how to return the index of an element rather than the value associated with the index. So if the 9th element of the array created in a loop contains the value desired, how would I be able to query what the index number is, being 9, or 8 I guess since bash array begin with index 0.

> that said, your approach is wasteful as it will scan the same dirs/file over and over again.
not sure what you mean. The loop will run once to scan all of the files in the specificed dir and then I will try to use an array to dump the results to and then access the result to continue on in the script acting on the desired results returned. There won't be any endless loop of scanning dir/files over and over and over and over...

---

### Post by Vaphell on 2012-11-14
you run *find* n times, 1 for every size range. Find will have to look at every file to check the conditions either way. That is wasteful because it can be done in a single *find* run

> I am thinking of dumping the results to an array, but of all the bash array examples and tuts I have read none show nor mention how to return the index of an element rather than the value associated with the index. So if the 9th element of the array created in a loop contains the value desired, how would I be able to query what the index number is, being 9, or 8 I guess since bash array begin with index 0.

it can't really be done. you could try looping over the array ( *for(( i=0; i<${#array[@]}; i++)); do echo ${array[****i]}; done* ), checking the value and printing the index when the match is found but it's inherently ambiguous.
 What would happen if your array is like this ( 0 0 0 1 1 2 3 4 4 )? you would probe it with 0, what index should be returned? 0, 1 or 2?


my approach
```
#!/bin/bash

t=( 1000 {1..9}0000 {1..9}00000 1000000{,0,00,000,0000,00000} )

echo thresholds: ${t[@]}

c=0
while read s
do
  while (( s>t[c] )); do ((c++)); (( sizes[t[c]]=0 )); done
  (( sizes[t[c]]++ ))
done < <( find . -maxdepth 1 -type f -printf "%s\n" | sort -n )

sp=-1
for s in ${!sizes[@]}
do
  echo "$((sp+1))-$s: ${sizes[s]}"
  sp=$s
done
```
output
```
$ ./fsizes.sh 
thresholds: 1000 10000 20000 30000 40000 50000 60000 70000 80000 90000 100000 200000 300000 400000 500000 600000 700000 800000 900000 1000000 10000000 100000000 1000000000 10000000000 10000000000
0-1000: 135
1001-10000: 25
10001-20000: 3
20001-30000: 1
30001-40000: 3
40001-50000: 0
50001-60000: 1
60001-70000: 0
70001-80000: 0
80001-90000: 0
90001-100000: 1
100001-200000: 0
200001-300000: 1
300001-400000: 2

```
find output is only file sizes, sorted numerically. Then i iterate over that set of data and check listed thresholds from the bottom up. Triggered condition means adding 1 to proper array element.

---

### Post by thaitang on 2012-11-14
> you run find n times, 1 for every size range. Find will have to look at every file to check the conditions either way. That is wasteful because it can be done in a single find run
ah yes I see what you mean. Yeah unfortunately I am sure much of my bash scripting is pretty inefficient, but at the end of the day the job generally gets done. I hope, however, it gets better the more I learn.

As an example, here is what I started with, and it works:
```
nf10k=`find . -maxdepth 1 -type f -name "*.html" -size +10000c -size -19999c | wc -l`
nf20k=`find . -maxdepth 1 -type f -name "*.html" -size +20000c -size -29999c | wc -l`
nf30k=`find . -maxdepth 1 -type f -name "*.html" -size +30000c -size -39999c | wc -l`
nf40k=`find . -maxdepth 1 -type f -name "*.html" -size +40000c -size -49999c | wc -l`
nf50k=`find . -maxdepth 1 -type f -name "*.html" -size +50000c -size -59999c | wc -l`
nf60k=`find . -maxdepth 1 -type f -name "*.html" -size +60000c -size -69999c | wc -l`
nf70k=`find . -maxdepth 1 -type f -name "*.html" -size +70000c -size -79999c | wc -l`
nf80k=`find . -maxdepth 1 -type f -name "*.html" -size +80000c -size -89999c | wc -l`
nf90k=`find . -maxdepth 1 -type f -name "*.html" -size +90000c -size -99999c | wc -l`
nf100k=`find . -maxdepth 1 -type f -name "*.html" -size +100000c -size -109999c | wc -l`

avgSize=0
avgName="zero"
if [[ "$nf10k" -gt "$avgSize" ]] ; then
	let avgSize="$nf10k"
	avgName="10k"
fi
if [[ "$nf20k" -gt "$avgSize" ]] ; then
	let avgSize="$nf20k"
	avgName="20k"
fi
if [[ "$nf30k" -gt "$avgSize" ]] ; then
	let avgSize="$nf30k"
	avgName="30k"
fi
if [[ "$nf40k" -gt "$avgSize" ]] ; then
	let avgSize="$nf40k"
	avgName="40k"
fi
if [[ "$nf50k" -gt "$avgSize" ]] ; then
	let avgSize="$nf50k"
	avgName="50k"
fi
if [[ "$nf60k" -gt "$avgSize" ]] ; then
	let avgSize="$nf60k"
	avgName="60k"
fi
if [[ "$nf70k" -gt "$avgSize" ]] ; then
	let avgSize="$nf70k"
	avgName="70k"
fi
if [[ "$nf80k" -gt "$avgSize" ]] ; then
	let avgSize="$nf80k"
	avgName="80k"
fi
if [[ "$nf90k" -gt "$avgSize" ]] ; then
	let avgSize="$nf90k"
	avgName="90k"
fi
if [ "$nf100k" -gt "$avgSize" ] ; then
	let avgSize="$nf100k"
	avgName="100k"
fi

#check whether any files exist that are less than avg file size
if [ "$avgName" == "10k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -9000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "20k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -18000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	#else
		#echo ""
	fi
elif [ "$avgName" == "30k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -25000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "40k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -35000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "50k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -45000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "60k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -50000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "70k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -60000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "80k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -70000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "90k" ] ; then
findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -80000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
elif [ "$avgName" == "100k" ] ; then
	findSmallFile=$(find . -maxdepth 1 -type f -name "*.html" -size -90000c)
	if [ -n "$findSmallFile" ] ; then
		smallFile
	fi
fi

```
But then I got it in my head I could make it better with loops, but is fast becoming a PITA.

I wonder though if you could add some comments to your suggested approach to make it easier for me to follow. Would be much appreciated.

---

### Post by Vaphell on 2012-11-14
```
#!/bin/bash

# thresholds/size brackets in ascending order
t=( 1000 {1..9}0000 {1..9}00000 1000000{,0,00,000,0000,00000} )

echo thresholds: ${t[@]}

# marker, index of t[] elem compared with sizes
c=0
# loop processes output of find -printf "%s\n" | sort -n line by line
# s holds the line/size 
while read s
do
  # compare s with t[c]
  # if necessary move marker to next element of t[] (c++)
  # until s falls below/is equal t[c]
  # for each tested bracket create element of result
  # with index=current_threshold and set it to 0
  while (( s>t[c] )); do ((c++)); (( sizes[t[c]]=0 )); done
  # being here means s <= t[c], add 1 to proper element of result
  (( sizes[t[c]]++ ))
done < <( find . -maxdepth 1 -type f -printf "%s\n" | sort -n )

sp=-1
# for s in <indices of sizes[@]>
for s in ${!sizes[@]}
do
  # print size range (previous_index-current_index) and sizes[current_index]
  echo "$((sp+1))-$s: ${sizes[s]}"
  sp=$s
done
```

i indexed result elements with their threshold number but it would work just fine if i used sizes[c] instead of sizes[t[c]]

lets say sorted find gives you
3
33
333
33333
and you have thresholds 100 1000 10000 100000
--------
initially marker points to 100
3: 3 > 100 is false, marker stays at 100
sizes[100]++ (1)
33: 33 > 100 is false, marker stays at 100
sizes[100]++ (2)
333: 333 > 100 is true, marker shifts to 1000, 333 > 1000 is false
sizes[1000]++ (1)
33333: 33333 > 1000 is true, marker shifts to 10000
33333 > 10000 is also true, marker shifts to 100000
33333 > 100000 is false
sizes[100000]++ (1)

the only thing left is printing out
0-100: sizes[100] (2)
101-1000: sizes[1000] (1)
1001-10000: sizes[10000] (0)
100001-100000: sizes[100000] (1)

---

