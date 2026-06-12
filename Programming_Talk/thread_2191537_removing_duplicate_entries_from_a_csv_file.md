---
title: "removing duplicate entries from a csv file"
date: 2013-12-03
forum: Programming Talk
---

### Post by peter_brickles on 2013-12-03
HI Guys i have a file as below 

> 

oranges 
apples 
lemons
grapes
pears
grapes 
grapes
lemons
ornages 




I want to display only lines that have not been duplicated i dont want to just remove the duplicates 

> 
pears
apples


any way to do this from the cli ?

Many thanks Pete

---

### Post by drmrgd on 2013-12-03
First, you've not presented a CSV file; this is just a list of words.  

You can use the unique option to sort for this.  From the text you entered, I see there is some extra whitespace at the ends, which you can get rid of with a cut command (which may also be what you want to use if you really have a CSV file).  Then pipe that output to sort with the '-u' option:

This shows the trailing whitespace:
```

$ cat -A file.txt
oranges $
apples $
lemons$
grapes$
pears$
grapes $
grapes$
lemons$
ornages $ 

```

This is how to pull the unique elements:

```

$ cut -d ' ' -f1 file.txt | sort -u
apples
grapes
lemons
oranges
ornages
pears

```

---

### Post by r-senior on 2013-12-03
Awk's associative arrays could do that:

```
$ awk '{c[$1]++} END {for (f in c) if (c[f]==1) print f}' fruit.txt
apples
pears

```

This makes an associative array 'c' that keeps a count of each fruit. Once complete, the awk 'END' block iterates over the array, looking for any element that has a count of 1.

This is the structure that it builds:

```
$ awk '{c[$1]++} END {for (f in c) print f, c[f]}' fruit.txt
lemons 2
apples 1
oranges 2
pears 1
grapes 3
```

ps. I corrected the spelling of '[COLOR=#000000]*ornages'.*[/COLOR]

---

### Post by r-senior on 2013-12-03
Or, if your file was clean, i.e. didn't have the whitespace issue going on, you could just do:

```
$ sort fruit.txt | uniq -u
apples
pears
```

---

### Post by drmrgd on 2013-12-03
> **r-senior said:**
> Awk's associative arrays could do that:

```
$ awk '{c[$1]++} END {for (f in c) if (c[f]==1) print f}' fruit.txt
apples
pears

```

This makes an associative array 'c' that keeps a count of each fruit. Once complete, the awk 'END' block iterates over the array, looking for any element that has a count of 1.

This is the structure that it builds:

```
$ awk '{c[$1]++} END {for (f in c) print f, c[f]}' fruit.txt
lemons 2
apples 1
oranges 2
pears 1
grapes 3
```

ps. I corrected the spelling of '[COLOR=#000000]*ornages'.*[/COLOR]

Nice!  I think you could simplify this even further by just printing the associative array keys without checking the count since the keys have to be unique by nature. Also in Perl:

```

$ perl -lane '$hash{$F[0]}++; END { print $_ for sort keys %hash }' file.txt 
apples
grapes
lemons
oranges
ornages
pears

```

Of course that assumes that one doesn't want to know how many times the elements repeat in the output.

---

### Post by r-senior on 2013-12-03
> **drmrgd said:**
> I think you could simplify this even further by just printing the associative array keys without checking the count since the keys have to be unique by nature.
OP only wants the fruits of which there are no duplicates, i.e. apples and pears. Hence the check for the count.

I don't know Perl but it is is remarkably similar to awk in this example! I had to look twice!

---

### Post by drmrgd on 2013-12-03
> **r-senior said:**
> OP only wants the fruits of which there are no duplicates, i.e. apples and pears. Hence the check for the count.

I don't know Perl but it is is remarkably similar to awk in this example! I had to look twice!

Oh!  You may be right!  I didn't interpret the question that way (I thought the OP just wanted all unique entries), but re-reading it, I think it could be that the answer sought after is indeed 'apples' and 'pears'.

Yes, Perl and AWK are very similar for a lot of things, which makes sense since AWK spawned Perl.  To me, Perl is like AWK on steroids :)

---

### Post by ofnuts on 2013-12-03
> **peter_brickles said:**
> 
I want to display only lines that have not been duplicated i dont want to just remove the duplicates 

any way to do this from the cli ?

```

sort data_file | uniq -c | grep '^\ *1 ' | tr -s ' ' | cut -d ' ' -f 3-

```
In slow motion:
[LIST]
[*]sort the data 
[*]call uniq to replace consecutive occurrences by a single occurrence prefixed by a count 
[*]keep only the lines with a count of 1 
[*]remove the count, display the rest 
[/LIST]

The "grep|tr|cut" can likely be replaced by a single awk call.

---

### Post by steeldriver on 2013-12-03
You could also do the associative array approach natively in bash 4+ I think

```

$ declare -Ai fruitcount
$ while read -r fruit; do (( fruitcount[$fruit]++ )); done < fruit
$ 
$ for fruit in ${!fruitcount[@]}; do [[ ${fruitcount[$fruit]} -eq 1 ]] && echo "$fruit"; done
apples
pears

```

but obviously it's not as compact as r-senior's awk version

---

### Post by r-senior on 2013-12-03
Groovy? :)

```
$ groovy -e 'def c=[:];new File(args[0]).each{c[it]=(c[it]?:0)+1};c.findAll{!--it.value}.each{println it.key}' fruit.txt 
apples
pears

```

---

