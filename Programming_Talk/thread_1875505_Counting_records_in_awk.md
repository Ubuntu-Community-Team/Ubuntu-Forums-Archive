---
title: "Counting records in awk"
date: 2011-11-04
forum: Programming Talk
---

### Post by mirkob on 2011-11-04
I very new (I mean, I never used any of it before) at grep and awk but have this script I need to do for a customer. 
  It is pretty simple an I could do it in my sleep in C but for security and practicability reason it woul be great to do it in a interpreted language so the customer could see what it being done and they can modify it if the condition changes.
   
  Basically I need to analyze a file and issue a command file as output for certain records.
  Using grep I can pipe only the relevant records to awk.
  It looks like that
  [FONT=&quot]/foo/bar/t001.dat[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]/foo/bar/t002.dat[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
   
  What I need to do is for each ‘.dat’  record , if the number of  records  ‘SOMETHINGOR OTHER’ below is => 4 then print ‘cp /foo/bar/…’ to sdtout if not go to the next record


  Is that something that can be done on a command line or do I need to write a small awk program.
  Thank you for your help

---

### Post by Vaphell on 2011-11-04
you can count rows directly with grep (-c), assuming that 1 record = 1 line
```
#!/bin/bash

for f in /foo/bar/*.dat
do
  occ=$( egrep -c '^12376718' "$f" )
  if [ $occ -ge 4 ]
  then
    echo $occ : cp "$f".....
  else
    echo $occ : "$f" fail
  fi
done
```

if your records have more complicated structure you'd need awk with defined record separator```

awk 'BEGIN{ RS="..." } END { print NR }'
```
for example
```
 echo a:b c:d e:f | awk 'BEGIN {RS=" " }; END { print NR }'
3
``` optionally you can add FS to define field separator if you need to get deeper

also awk can do pattern matching so grep is not required at all
changing occ=... line to
```
occ=$( awk 'BEGIN { c=0 }; /^12376718/ { c++ }; END { print c } ' "$f" )
```
yields the same results
```
----- egrep -----
4 : cp t001.dat.....
2 : t002.dat fail
0 : t003.dat fail
6 : cp t004.dat.....
----- awk -----
4 : cp t001.dat.....
2 : t002.dat fail
0 : t003.dat fail
6 : cp t004.dat.....

```

---

### Post by mirkob on 2011-11-05
Thanks!!
Much appreciated

I’m will start working on this but reading your reply it occurs to me that I may not have explained myself correctly. I apologize if this is the case. 

  The dat file is not the input file.
  The input fila has 2 kinds of records. One with the dat file path and name and one with the info we need to count so
  -------------- INPUT FILE BEGIN ------------------------
  [FONT=&quot]/foo/bar/t001.dat[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]/foo/bar/t002.dat[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]/foo/bar/t003.dat[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  [FONT=&quot]12376718 SOMETHINGOR OTHER[/FONT]
  -------------- INPUT FILE END ------------------------

---

### Post by ofnuts on 2011-11-05
```

tr '\n' '|' < $file | sed -e 's/|\//\n\//g' | egrep -e '(\|.+){4}' | cut -d '|' -f 1

```In slow motion:

[LIST=1]
[*]replace all LF by a | (this is assuming you don't use '|' anywhere in the results...)
[*]replace "|/" by "LF/", in other words, restore the line feed before every file name: the original file is now collapsed into one line per file
[*]find those lines with at least 4 '|' (those that had at least 4 lines of data in the original)
[*]cut the filename
[/LIST]

---

### Post by mirkob on 2011-11-05
This is great.
Really!
It works like a charm and it is elegant.
The whole script is on one line.
Then I started working on it to adapt it for when the .dat file is under file and I hit a snag.
The \ is used as separator in the script and has special meaning in sed.
------------- INPUT FILE BEGIN ------------------------
\\server\foo\bar\t001.dat
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
\\server\foo\bar\t002.dat
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
\\server\foo\bar\t003.dat
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
------------- INPUT FILE END ------------------------

Thanks

---

### Post by ofnuts on 2011-11-06
> **mirkob said:**
> This is great.
Really!
It works like a charm and it is elegant.
The whole script is on one line.
Then I started working on it to adapt it for when the .dat file is under file and I hit a snag.
The \ is used as separator in the script and has special meaning in sed.
------------- INPUT FILE BEGIN ------------------------
\\server\foo\bar\t001.dat
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
\\server\foo\bar\t002.dat
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
\\server\foo\bar\t003.dat
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
12376718 SOMETHINGOR OTHER
------------- INPUT FILE END ------------------------

ThanksIn the sed expressions, the "/" in your file is expressed as "\/", and the "\" would be expressed as "\\" so the change is trivial:
```

tr '\n' '|' < $file | sed -e 's/|\\/\n\\/g' | egrep -e '(\|.+){4}' | cut -d '|' -f 1

```

---

### Post by mirkob on 2011-11-07
> **ofnuts said:**
> In the sed expressions, the "/" in your file is expressed as "\/", and the "\" would be expressed as "\\" so the change is trivial:
```

tr '\n' '|' < $file | sed -e 's/|\\/\n\\/g' | egrep -e '(\|.+){4}' | cut -d '|' -f 1

```


It was trivial.
I thought I tried that. Obviously I was messing with the delimiters.
Thanks again
This thread can be marked as resolved

---

