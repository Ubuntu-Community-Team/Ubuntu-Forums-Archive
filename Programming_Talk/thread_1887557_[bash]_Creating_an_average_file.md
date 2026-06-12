---
title: "[bash] Creating an average file"
date: 2011-11-27
forum: Programming Talk
---

### Post by The Linux Cynic on 2011-11-27
I'm a beginner to bash and I'm trying to do something which seems fairly basic:

I'd like to take a set of datafiles (lets say 30 files, named data0.txt, data1.txt ... data29.txt), and create a file called averagedata.txt, which, if data#.txt contains, for example:

0 0.573761 0.152591
1 0.507031 0.248265
2 0.466843 0.152591
3 0.439491 0.152591

, the averagedata.txt would contain data in the same format, with each field being the average of the values in that same field of every data file.

Thanks

---

### Post by MG&amp;TL on 2011-11-27
Create the file:

```
touch <myfile>
```

Read from file:

```
cat <myinputfile>
```

pipe output to another file:

```
| tee <myoutputfile>
```

So all in all, something like:

```
cat myinputfile | tee myouputfile
```

Correct me if I'm wrong or inefficient.

---

### Post by The Linux Cynic on 2011-11-27
Thank you for your prompt reply,

But if I understand what you mean, this would just concatenate my data files into one long file.

Maybe I didn't describe my goal very well. There are 30 files, with the same number of fields in each line, and the same number of lines.

I want to create a single file that is the average of those 30 files, with each field being an average of the data in the corresponding field in the 30 files.

This is a lot of words to describe something very simple. I just want a file that is "the average".

---

### Post by docbop on 2011-11-27
If you want to Average the values you need more than Bash on its own.  A scripting language with more math capabilities like awk, perl, python, or ???

---

### Post by MadCow108 on 2011-11-27
that is far from a simple task in pure bash

I would recommend a higher level language with native floating point operations (bash can only do integer arithmethic).
awk or python come to mind

short python example using numpy, doing it without is a couple more lines:
```
import glob
import numpy as np
# get list of files
files = glob.glob("data*.txt")

#read data
d = np.dstack ([np.genfromtxt(f) for f in files])

#get average
av = np.average(d, axis=2)

#write output
out = open("res.txt", "w")
for row in av:
  out.write(" ".join(map(str, row)) + "\n")
out.close()
```

---

### Post by hakermania on 2011-11-27
Ok, some raw bash here, there should be an easier way though:
```

#!/bin/bash
#Ok, reading every single file named data*.txt, as in your example

read_this_line=1 #<- we will read the 1st line first of all
line_number=$(cat data0.txt | wc -l); #<--files have the same line count, so reading the 1st so as to know the line count of everybody.

while [[ $read_this_line -le $line_number ]]; do
#first reading every single line and storing to a file, then make the average of this
#and then post it to the 'average.txt'
   rm -f average_tmp
   touch average_tmp
   for i in data*.txt; do
      sed -n "$read_this_line p" $i >> average_tmp
   done
   #Now, for example, we have every 1st or 2nd or 3rd (and so on) line of
   #every single file to average_tmp, we will now separate each value to another file
   #then read every of these files, make the average and post it to average.txt yay
   while read line; do
      #storing each value to a separate file
      first_value=${line:0:1}
      second_value=${line:2:8}
      third_value=${line:11:8}
      echo $first_value >> first_values_tmp_file
      echo $second_value >> second_values_tmp_file
      echo $third_value >> third_values_tmp_file
   done < average_tmp
   #now we have the 3 files we want, making the average out of them
   for i in *_values_tmp_file; do
   total_count=0
   all_together=0
      while read line; do
         if [[ ${line:0:1} = "." ]]; then
            line="0${line}"
         fi
         all_together=$(echo "$all_together + $line" | bc -l)
         let total_count=total_count+1;
      done < $i
      average_value=$(echo "$all_together / $total_count" | bc -l)
      if [[ ${average_value:0:1} = "." ]]; then
            average_value="0${average_value}"
      fi
      echo $average_value > $i
   done
   f_average=$(cat first_values_tmp_file)
   s_average=$(cat second_values_tmp_file)
   t_average=$(cat third_values_tmp_file)
   average_values_of_all="${f_average} ${s_average} ${t_average}"
   echo $average_values_of_all >> average.txt
   rm -f *_values_tmp_file
   let read_this_line=read_this_line+1
done
rm -f average_tmp

```tested like this:
```

alex@MaD-pc:/test$ l
average*  data0.txt  data1.txt
alex@MaD-pc:/test$ cat data0.txt 
0 0.500000 0.152591
1 0.507031 0.248265
2 0.466843 0.152591
3 0.439491 0.152591
alex@MaD-pc:/test$ cat data1.txt 
0 0.000000 0.052591
1 0.507331 0.298265
2 0.466433 0.152391
3 0.939491 0.152391
alex@MaD-pc:/test$ ./average 
alex@MaD-pc:/test$ cat average.txt 
0 0.25000000000000000000 0.10259100000000000000
1.00000000000000000000 0.50718100000000000000 0.27326500000000000000
2.00000000000000000000 0.46663800000000000000 0.15249100000000000000
3.00000000000000000000 0.68949100000000000000 0.15249100000000000000
alex@MaD-pc:/test$

```I'm pretty happy with the results, the only thing is the infinite zeros that bc leaves there, but they could be removed pretty easily, but I cannot continue this as I don't have much time right now.

---

### Post by The Linux Cynic on 2011-11-27
> I would recommend a higher level language with native floating point operations (bash can only do integer arithmethic).

Oh! I didn't realize bash doesn't have floating point operations. Good to know.

I know a bit of awk, but mostly limited to one-liners that only operate on one file. Could I get it to use multiple files like this?

---

### Post by The Linux Cynic on 2011-11-27
Thank you Hackermania! I will study your solution and see if it works for me.

---

### Post by erind on 2011-11-27
> **The Linux Cynic said:**
> Oh! I didn't realize bash doesn't have floating point operations. Good to know.

I know a bit of awk, but mostly limited to one-liners that only operate on one file. Could I get it to use multiple files like this?

Here is one way with awk:

```
	awk '{ for(i=1; i<=NF; i++) a[FNR,i]+=$i; nf=NF } 
	     END { for(x=1; x<=FNR; x++ ) 
	             for( y=1; y<=nf; y++ ) 
		       printf ( y < nf ) ? a[x,y]/(ARGC-1) " " : a[x,y]/(ARGC-1) "\n"
	         }
	    '  data*.txt
```

---

### Post by Lars Noodén on 2011-11-27
It can probably be done with an [awk one-liner](http://www.softpanorama.org/Tools/Awk/awk_one_liners.shtml):
```

awk ' { s += $2 }
   END  { print "sum is", s, " average is", s/NR }'  data*.txt

```

---

