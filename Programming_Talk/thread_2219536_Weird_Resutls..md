---
title: "Weird Resutls."
date: 2014-04-24
forum: Programming Talk
---

### Post by ylafont on 2014-04-24
```
while read CHANNEL; do
    Stream=($CHANNEL)
    LastArray=${#Stream[@]}


    Frequency="${Stream[0]}"
    UScable="${Stream[1]}"
    Program="${Stream[3]}"
    ChannelNo="${Stream[4]}"
**    FileName="${Stream[@]:5:$LastArray}"**
[B]    FileName1=$ChannelNo" - "$FileName".strm" <  did not work
   FileName1="$ChannelNo - $FileName.strm"  <- did not work[/B]
    echo  $FileName1
    touch Streams/$FileName1
    
    # echo $Frequency $UScable $Program
    # echo 'hdhomerun://'$HDHomeID'-0/tunner0?channel=auto:'$UScable'&program='$Program > Streams/$ChannelNo' - '$FileName'.strm'
    #echo 'hdhomerun://'$HDHomeID'-0/tunner0?channel=auto:'$UScable'&program='$Program > Streams/$ChannelNo' - '$FileName'.strm'
done < $HDDATA

```

I am trying to create some files with filenames base on a concatenation of two variables.  I must be missing something since i am getting strange results. When I check the file name to be created $FileName or $FileName1  it prints out fine.


From this 
```

1561 - History Channel.strm
1563 - Discovery Espan.strm
1564 - Nat Geo Mundo.strm
1567 - Canal Once.strm
1570 - Ultra Docu HD.strm
1582 - Fox Life.strm
1583 - Pasiones.strm
1584 - Univision tlNov.strm
1585 - Ultra Luna HD.strm
```


to this.
```

-rw-r--r-- 1 root root       0 Apr 24 03:58 Histor.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 History
 -r--r-- 1 root root          0 Apr 24 03:58 Velocity.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 Veria
-rw-r--r-- 1 root root       0 Apr 24 03:58 VH1
-rw-r--r-- 1 root root       0 Apr 24 03:58 Viendo
-rw-r--r-- 1 root root       0 Apr 24 03:58 Vie.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 (Viet).strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 View.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 VME
-rw-r--r-- 1 root root       0 Apr 24 03:58 V-me.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 WAPA
-rw-r--r-- 1 root root       0 Apr 24 03:58 WDCA
-rw-r--r-- 1 root root       0 Apr 24 03:58 WDCA-DTV.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 WDCW
-rw-r--r-- 1 root root       0 Apr 24 03:58 WE
-rw-r--r-- 1 root root       0 Apr 24 03:58 Weather
-rw-r--r-- 1 root root       0 Apr 24 03:58 Well.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 Wes.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 Westerns.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 (We.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 We.strm
-rw-r--r-- 1 root root       0 Apr 24 03:58 (West).strm

```

I also receive 
1787 - DW Amerika.strm
./x.sh: line 33: Streams/$FileName1: ambiguous redirect
1788 - ProSiebenSAT.1W.strm
./x.sh: line 33: Streams/$FileName1: ambiguous redirect

if i try to echo the files.



Weird.   have i not included something?

---

### Post by ylafont on 2014-04-24
> **ylafont said:**
> [CODE]while read CHANNEL; do
     echo 'hdhomerun://'$HDHomeID'-0/tunner0?channel=auto:'$UScable'&program='$Program > Streams/**"$ChannelNo -  $FileName.strm"**


Looks like double quotes on the line did the trick.  Not sure why it did not work on the variable line.

---

### Post by Vaphell on 2014-04-24
any sample of the input data, especially these lines responsible for errors?

can't you split the row directly, with
```
while read -a array; do ...
```
?
It's possible the array is not required in the first place, why not
```
while read freq uscable _ prog channel filename; do ...
```
?


either way it looks like a word splitting problem. Unquoted var with space(s) gets cut to pieces and you dont redirect to *> "some file"* but to *> "some" "file"* <- ambiguous redirect. Always quote your variables.

---

### Post by ylafont on 2014-04-24
Here is the sample data

 ```
213000000     13     13      549     94 CBS Sports Ntwk
 129000000     15     15      588     96 SportsNet NY (O
 627000000     91     91      787     97 NESN National
 447000000     61     61      118     100 CNN
 447000000     61     61      119     101 CNN Headline Ne
 663000000     102     102      121     102 CNBC
 411000000     55     55      122     103 MSNBC
 411000000     55     55      123     104 Bloomburg TV
 447000000     61     61      124     105 CNN Internation
 789000000     123     123      125     106 CNBC World
 609000000     88     88      505     107 BBC World
 411000000     55     55      470     108 Fusion
 411000000     55     55      127     109 C-SPAN
 693000000     107     107      128     110 C-SPAN 2
```
 
read the file line by line and places it in an array.  there weird part was that  it print fine with echo. I think tried the "[COLOR=#000000][FONT=Ubuntu Mono]while read -a array; do ..."  [/FONT][/COLOR] not sure what the result where, will try again.

---

### Post by steeldriver on 2014-04-24
How about something like

```

while read -r freq uscable _ prog _ name; do 
  touch tests/"$name"
done < channeldata 

```

```

$ ls -l tests
total 0
-rw-rw-r-- 1 user user 0 Apr 24 18:57 BBC World
-rw-rw-r-- 1 user user 0 Apr 24 18:57 Bloomburg TV
-rw-rw-r-- 1 user user 0 Apr 24 18:57 CBS Sports Ntwk
-rw-rw-r-- 1 user user 0 Apr 24 18:57 CNBC
-rw-rw-r-- 1 user user 0 Apr 24 18:57 CNBC World
-rw-rw-r-- 1 user user 0 Apr 24 18:57 CNN
-rw-rw-r-- 1 user user 0 Apr 24 18:57 CNN Headline Ne
-rw-rw-r-- 1 user user 0 Apr 24 18:57 CNN Internation
-rw-rw-r-- 1 user user 0 Apr 24 18:57 C-SPAN
-rw-rw-r-- 1 user user 0 Apr 24 18:57 C-SPAN 2
-rw-rw-r-- 1 user user 0 Apr 24 18:57 Fusion
-rw-rw-r-- 1 user user 0 Apr 24 18:57 MSNBC
-rw-rw-r-- 1 user user 0 Apr 24 18:57 NESN National
-rw-rw-r-- 1 user user 0 Apr 24 18:57 SportsNet NY (O

```

---

