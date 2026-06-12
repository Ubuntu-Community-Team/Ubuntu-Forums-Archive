---
title: "BASH Line Parsing Question"
date: 2011-12-07
forum: Programming Talk
---

### Post by hantechbl on 2011-12-07
I'm working on a little script that will parse log files and will take certain blobs of text, currently have something where it will take the line and loop for each line I plan on having an output redirector using echo to save the modified output as a different file and then delete the original entirely.  Do you know how I could accept a line kinda like how a parameters are passed to a command, so that I can use $1, $2, $3?
Log file field length is variable, so I can't process based on length.  Log kinda looks like this:
```
text longertext text text blobsotext
supertext evenlongertext nottext text text

```
So I currently have a loop setup to parse each line, it's just a matter of getting it to select each string, kinda like how explode() works on php

---

### Post by papibe on 2011-12-07
You can read a regular line and then call a function with the line as a parameter. Inside the function you'll be able to access each word as a parameter.

For example:
```
#!/bin/bash

function parse_line
{
	for word in $@; do
		echo "$word"
	done
}

while read -r line; do
	parse_line $line
done

```
Does that help?
Regards.

---

### Post by hantechbl on 2011-12-07
It would help if there was a way that I could perform checks with the data, but the problem is that each line has specific types of data for each column, so like for example date-stamp is column one, time is column 2, and then there are other data types for other columns, for each line I need to select a column and assign it into a variable, columns are seperated by a space.

---

### Post by josephmills on 2011-12-07
Please take a couple of min to look at 
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

I hope that this can help you in the future.

---

### Post by papibe on 2011-12-08
I think we can come up with more suggestions/directions if you post sample data, and the output you would like to see.

Regards.

BTW, take a look at 'awk'. It handles columns much better that bash.

---

### Post by hantechbl on 2011-12-08
Alright, I've got that part solved now, (Using: | cut -d ' ' -f 2)  but I have a kinda easy question, but I haven't been able to figure it out:
I perform the aritmatic function:
minutes=$((${rndsec}/60))
And I get an error: /60: syntax error: operand expected (error token is "/60"), do any of you guys know how to fix this/what I did wrong?

---

### Post by papibe on 2011-12-08
It looks like ${rndsec} does not have a numeric value assigned to it.

Regards.

---

### Post by josephmills on 2011-12-08
this is not meant to be blunt please dont take it that way.
use more quotes!" They are vital. Also, learn the difference between ' and " and `. Please See [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes) and [http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words).
Hope that this helps :)

---

### Post by hantechbl on 2011-12-08
Odd, input is processed by: rndsec=$elapsed | cut -d . -f 1
where elapsed equals 2501.075, the purpose of the cut is to cut off data after decimal, is that why it's not working?

---

### Post by josephmills on 2011-12-08
after talking about this on irc I have come to this 
```

<newbot> # minutes=$((${rndsec}/60))
<evalbot> newbot: bash: /60: syntax error: operand expected (error token is "/60")

<newbot> anwhat is  (error token is "/60")
<yitz_> # minutes=$((RANDOM /  60 ))
<evalbot> yitz_: no output
<dualbus> newbot: rndsec is empty

<yitz_> # minutes=$(( /  60 ))
<evalbot> yitz_: bash: /  60 : syntax error: operand expected (error token is "/  60 ")
<newbot> what is  (error token is "/60") ?

<yitz_> It means that "/60" isn't a valid math string
<dualbus> newbot: it means that you can't divide the empty string by 60
<newbot> how to fix ?
<dualbus> '/' is a binary operator, so it expects two arguments

<dualbus> newbot: but making sure rndsec contains something


!faq 1
http://mywiki.wooledge.org/BashFAQ/001 -- How can I read a file (data stream, variable) line-by-line (and/or field-by-field)?

```

Hope that this helps :D

---

### Post by Vaphell on 2011-12-08
dropping decimal part
```
$ x=123.456; y=${x/.*/}; echo $x $y
123.456 123
```

integer math works with empty variables (they are treated as 0) but you have to drop $ from the variable. I guess it's a difference between constructing a literal string before calculating ($var is substituted and then bash does math on '/60') and giving a formula to solve (integer arithmetic sees var as a variable in 'var/60' and if var is empty, uses 0)

```
$ x=; y=$(($x/60)); echo x=$x y=$y
bash: /60: syntax error: operand expected (error token is "/60")
$ x=; y=$((x/60)); echo x=$x y=$y
x= y=0
$ x=2000; y=$(($x/60)); echo x=$x y=$y
x=2000 y=33
$ x=2000; y=$((x/60)); echo x=$x y=$y
x=2000 y=33

```

fields in lines of variable length with arrays (though awk is more suited)
```
while read -a arr
do
  echo '(' ${arr[@]} ')' size: ${#arr[@]}
  for(( i=0; i<${#arr[@]}; i++ ))
  do
    echo arr[$i]=${arr[i]}
  done
done <<< $'a b c\nd e f g h\ni j'

( a b c ) size: 3
arr[0]=a
arr[1]=b
arr[2]=c
( d e f g h ) size: 5
arr[0]=d
arr[1]=e
arr[2]=f
arr[3]=g
arr[4]=h
( i j ) size: 2
arr[0]=i
arr[1]=j

``` to use data from file replace <<< "string" with < input.file

---

### Post by hantechbl on 2011-12-08
Well Uh, I guess I kinda got lost in Vaphall's example, but from the sounds of it I'm processing the data wrong, and it's performing some sort of action to the data? That's what I got from it.  I'm still confused and I haven't been able to get it to work so here's something similar to what i have:
I also need a way to take off numbers after the decimal.
```

cat $local_file | while read line; do
rndsec=$line | cut -d ' ' -f 2
minutes=$(($rndsec/60))
echo $minutes >> $outputfile
done

```
Input: local file
```
55902 452.076 xx.xx.xxx.xx xxxx xxxxxxxx xxxxxxxxxx 0.014812401 0.000054084
```

---

### Post by Vaphell on 2011-12-08
```
#!/bin/bash

local_file=in.txt
output_file=out.txt

while read f1 f2 junk
do
 echo line: $f1 $f2 $junk
  minutes_int=$((${f2/.*/}/60))
  echo "int(${f2/.*/}/60)=$minutes_int"
  minutes_float=$( bc -l <<< "${f2/.*/}/60" )
  echo "${f2/.*/}/60=$minutes_float"
done < $local_file
```
output:
```
$ ./f2.sh 
line: 55902 452.076 xx.xx.xxx.xx xxxx xxxxxxxx xxxxxxxxxx 0.014812401 0.000054084
int(452/60)=7
452/60=7.53333333333333333333
```

---

### Post by hantechbl on 2011-12-08
Hello, I just read the post and I didn't see the file being loaded anywhere within the loop, is it automatically loaded via in?  And out?  and then the rest of the parameters are stored in junk?  Also It shouldn't display output, it should just write it to a file, in one line I just need to modify the second column and put it back in the original format with the modified second column.

---

### Post by Vaphell on 2011-12-09
> Hello, I just read the post and I didn't see the file being loaded anywhere within the loop, is it automatically loaded via in?

```
while read ...
do
  ...
done **< $local_file**
```

if i redirected output to file, there would be no output in terminal and i would have nothing to paste. I merely showcased how to do integer and float math. Do what you want with it, you know how to redirect stuff.

also you can and most likely should use awk
```
awk '{ $2=int($2)/60; print }' in.txt > out.txt
```
that's all you need to do to modify second field on the fly

---

