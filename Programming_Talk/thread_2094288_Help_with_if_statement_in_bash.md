---
title: "Help with if statement in bash"
date: 2012-12-13
forum: Programming Talk
---

### Post by JCM_Pico on 2012-12-13
Hi there,

I'm having trouble using numbers in an if statement in bash...

```

for (( i=0; i<=3; i++  )) ; do
   for (( j=0; j<=9; j++ )) ; do

#       awk '!/^(0([6-9])+|[1-2]+([0-9])+)h([ |0-9|a-z|A-Z|\-|.])*$/' 00h00_${i}${j}-12-2011 > tmp_file1

      if [ ${i} == 0 ] && [ ${j} == 0 ] ; then
         # DO NOTHING
      echo 'a' 
      elif [ ${i} < 1 ] ; then

        # k=$(( i + 1 ))
         echo 'k'        
#          awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*(0([2-9])+|[1-3]+([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2

      else
      echo 'b'
      fi

   done
done

```

it seams that there is some problem with the elif [ ${i} < 1 ] ; then

 line 11: 1: No such file or directory

How can I say to bash that if i is less than #one to execute a task?

---

### Post by Vaphell on 2012-12-13
[ ] uses -lt (less than), -gt (greater than), -eq (equal), -ne (not equal)
if you want <, > ,== for integer operations you can put your condition in (( ))

do you really need that double for-loop? *for i in {00..39}* would do the same, though i see it is used in date and that range doesn't really fit. In case you wanted to get a single digit - ${i:0:1} or ${i:1:1}

out of curiosity, what is that huge awk expression supposed to do?

---

### Post by JCM_Pico on 2012-12-13
> **Vaphell said:**
> [ ] uses -lt (less than), -gt (greater than), -eq (equal), -ne (not equal)
if you want <, > ,== for integer operations you can put your condition in (( ))

do you really need that double for-loop? *for i in {00..39}* would do the same, though i see it is used in date and that range doesn't really fit. In case you wanted to get a single digit - ${i:0:1} or ${i:1:1}

out of curiosity, what is that huge awk expression supposed to do?

Thanks... with (()) it works fine =)

the huge regular expression in awk is used to remove unwanted lines that match certain characteristics (dates) in big txt files....

---

### Post by Vaphell on 2012-12-13
what about the number range? your loops produce 0-39
i wouldn't say it fits 00h00_${i}${j}-12-2011

---

### Post by JCM_Pico on 2012-12-13
> **Vaphell said:**
> what about the number range? your loops produce 0-39

Indeed, the 2 loops will slowdown the script... but to be able to remove all the unwanted lines I need to created several different regular expression... that depend from the two digits of the loop separately

---

### Post by Vaphell on 2012-12-13
you seem to skip 0 and i am not convinced 39 is a proper value either

wouldn't this be better?
```
for i in {01..30}
do
  echo ${i:0:1} ${i:1:1}  # separate digits
  if [ ${i:0:1} = 0 ]
  then
    ...
  else
    ...
  fi
done
```

---

### Post by JCM_Pico on 2012-12-13
> **Vaphell said:**
> you seem to skip 0 and i am not convinced 39 is a proper value either

wouldn't this be better?
```
for i in {01..30}
do
  echo ${i:0:1} ${i:1:1}  # separate digits
  if [ ${i:0:1} = 0 ]
  then
    ...
  else
    ...
  fi
done
```

Cool... That is a very nice way to do it.... thank you =)

---

### Post by JCM_Pico on 2012-12-13
I have other question if you don't mind....

This loop needs to be embed in another loop that only contains 4 indices and they are independent... is it possible to make it to run in parallel with bash?

---

### Post by Vaphell on 2012-12-13
what problem do you want to solve exactly that it requires parallel execution?

---

### Post by JCM_Pico on 2012-12-13
> **Vaphell said:**
> what problem do you want to solve exactly that it requires parallel execution?

This is the code util now 

```
#!/bin/bash

#for ij in {01..31}; do
for ij in 01; do
   i=${ij:0:1}; j=${ij:1:1}

   awk '!/(0([6-9])+|[1-2]+([0-9])+)h([ |0-9|a-z|A-Z|\-|.])*/' "00h00_${ij}-12-2011" > tmp_file1

   if [[ ${i} == 0 ]] && [[ ${j} != 9  ]]; then

      k=(${j} + 1); l=(${i} + 1)
      awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*('${i}'(['${k}'-9])+|['${l}'-3]+([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2
      
   elif [[ ${i} == 0 ]] && [[ ${j} == 9  ]]; then

      k=(${j} + 1); l=(${i} + 1)
      awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*('${l}'([0-9])+|['${l}'-3]+([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2

   elif [[ ${i} != 0 ]] && [[ ${j} != 9  ]]; then

      k=(${j} + 1); l=(${i} + 1); m=(${i} - 1)
      awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*('${i}'(['${k}'-9])+|['${l}'-3]+([0-9])+|'${m}'([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2
      
   elif [[ ${i} != 0 ]] && [[ ${j} == 9  ]]; then

      k=(${j} + 1); l=(${i} + 1); m=(${i} - 1)
      awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*('${l}'([0-9])+|['${l}'-3]+([0-9])+|'${m}'([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2

   elif [[ ${j} == 0  ]]; then

      k=(${j} + 1); l=(${i} + 1); m=(${i} - 1)
      awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*('${i}'([0-9])+|['${i}'-3]+(['${l}'-9])+|'${m}'([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2

   else
      echo '!!! CAUTION !!! Something doesnt match...'
   fi

   mv tmp_file2 "00h00_${ij}-12-2011"
#   rm tmp_file1

done



## FOR 00 h FILES
# awk '!/^(0([6-9])+|[1-2]+([0-9])+)h([ |0-9|a-z|A-Z|\-|.])*$/' 00h00_01-12-2011 > tmp_file1
# awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*(0([2-9])+|[1-3]+([0-9])+|0([0-9]))-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2
# awk '!/(06h([1-9])+)([0-9a-zA-Z|\-|.| ])+/' tmp_file2 > tmp_file3

# mv tmp_file3 00h00_01-12-2011
# rm tmp_file*

## FOR 06 h FILES
# awk '!/^(1([2-9])+|[2]+([0-9])+)h([ |0-9|a-z|A-Z|\-|.])*$/' 06h00_01-12-2011 > tmp_file1
# awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*(0([2-9])+|[1-3]+([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2
# awk '!/(12h([1-9])+)([0-9a-zA-Z|\-|.| ])+/' tmp_file2 > tmp_file3

# mv tmp_file3 06h00_01-12-2011
# rm tmp_file*

## FOR 12 h FILES
# awk '!/^(1([8-9])+|[2]+([0-9])+)h([ |0-9|a-z|A-Z|\-|.])*$/' 12h00_01-12-2011 > tmp_file1
# awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*(0([2-9])+|[1-3]+([0-9])+)-([0-9|\-|.| ])*/' tmp_file1 > tmp_file2
# awk '!/(18h([1-9])+)([0-9a-zA-Z|\-|.| ])+/' tmp_file2 > tmp_file3

# mv tmp_file3 12h00_01-12-2011
# rm tmp_file*

## FOR 18 h FILES
# awk '!/([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*(0([2-9])+|[1-3]+([0-9])+)-([0-9|\-|.| ])*/' 18h00_01-12-2011 > tmp_file3

# mv tmp_file3 18h00_01-12-2011


```


I have to repeat this for cycle for other files that start with 06*, 12* and 18*.... the parallel programming it was just if it was feasible with "low end" in bash....

However this script does not work =( the variables i j k l or m are not going to may awk code has numbers.... =( any suggestion?

---

### Post by steeldriver on 2012-12-13
You should be able to pass shell variables into your awk command with the -v argument

```
$ i=700; awk -v var=$i '$6 == "Dec" {print var - 2;}' < <(ls -l)
```

(nonsense example - but you get the idea)

---

### Post by JCM_Pico on 2012-12-13
> **steeldriver said:**
> You should be able to pass shell variables into your awk command with the -v argument

```
$ i=700; awk -v var=$i '$6 == "Dec" {print var - 2;}' < <(ls -l)
```

(nonsense example - but you get the idea)

ok... it prints the ll -l command replacing the name with 698... but how can I write sothing-698 ????

---

### Post by Vaphell on 2012-12-13
you should describe exactly what you are dealing with

i see you have a bunch of files with names in ${hr}h00_${day}-12-2011 format. Now what?

---

### Post by steeldriver on 2012-12-13
Agreed -  having looked at your awk expression I'm not sure you are going to be able to do what you want that way - as far as I know you can't use variables in a regex character range like [1-9] (i.e. the problem is NOT about passing variables into awk - it's about using variables within a regex)

Maybe take a step back and tell us what end result you are trying to achieve and someone will be able to suggest another way to go about it?

---

### Post by Vaphell on 2012-12-13
it is possible to create regex variable and use let's say *$0 ~ rgx*

that said, smart approach saves 80% of work and knowing exact conditions helps create proper solution.

---

### Post by JCM_Pico on 2012-12-17
Has you already have noticed the file names have a format to its respective date...
by example for the 00h of December 1st the name is 00h00_01-12-2011
I have a file for every 6 hours... and the files contain data range the next 7 following days... and the data is repeated 1000x for different measuring points... However I only want the first 10 lines of each date for every measuring point... 
The files are huge so to handle them easily I thought that it would be easy to remove the unwanted lines with regex... and it was... the problem is to implement the regexp in a bash scrip to remove the unwanted data from the files with different dates....
That's the reason for using bash variables within the regex... because the regex will change accordingly to the name of the file  

The file is formatted like this:
```
time1 location1       day-month-year    data
time2 location1       day-month-year    data
...
timen location1       day-month-year    data
time1 location2       day-month-year    data
time2 location2       day-month-year    data
...
timen location2       day-month-year    data
timen location1       day-month-year    data
...
time1 location1000       day-month-year    data
time2 location1000       day-month-year    data
...
timen location1000       day-month-year    data
```

Given your replies ... I was able to understand that the problem is that I'm trying to use bash variable in the regex... Any idea how passed them to the regex?

---

### Post by steeldriver on 2012-12-17
like Vaphell said, you should be able to use a ~ regex e.g.

```
$ cat myfile
2012-11-23 23:52:08.984954264 -0500
2012-11-14 08:47:03.366957406 -0500
2012-11-14 08:49:01.715544023 -0500
2012-08-19 18:31:52.435528412 -0400
2012-08-24 09:43:06.627363866 -0400
2012-12-02 08:55:36.924589458 -0500

``````
$ mo=08; awk -v d="2012-$mo-[0-9]+" '$1 ~ d {print d, $0}' myfile 
2012-08-[0-9]+ 2012-08-19 18:31:52.435528412 -0400
2012-08-[0-9]+ 2012-08-24 09:43:06.627363866 -0400

```

---

### Post by JCM_Pico on 2012-12-17
Ok... I've solved the problem....

I was  not being able to use shell variables within the awk because of the !/

Using the above method I was able to pass the !/ as a element of the awk and the regex with the embedder shell variable...

```
awk '!/'"([0-9])+h([0-9)+( )([a-zA-Z0-9])+( )*("${i}"(["${k}"-9])+|["${l}"-3]+([0-9])+)-([0-9|\-|.| ])*/" tmp_file1 > tmp_file2
```

Thank you for all those how helped =)

---

