---
title: "GAWK and files with no record separator"
date: 2011-04-27
forum: Programming Talk
---

### Post by Desidero on 2011-04-27
While attempting to parse a file at work today, I encountered a problem that I can't seem to solve:

I have a file that's about 10GB containing millions of records. The records are in a fixed-width format with no record separator. I'd like to use GAWK to parse the file and do a few things, but it doesn't seem to be able to handle files that don't have a record separator (RS/RT).

[SIZE=2]**Example:**[/SIZE]

Parsing a fixed-width record file with newline (\n) record separators:
```

test@ubuntu:~/Desktop$ cat test_newline 
aaabbbccc
dddeeefff
ggghhhiii
test@ubuntu:~/Desktop$ gawk '{printf "Record: %d\n\tField 1: %s\n\tField 2: %s\n\tField 3: %s\n", NR, $1, $2, $3}' FIELDWIDTHS="3 3 3" test_newline 
Record: 1
    Field 1: aaa
    Field 2: bbb
    Field 3: ccc
Record: 2
    Field 1: ddd
    Field 2: eee
    Field 3: fff
Record: 3
    Field 1: ggg
    Field 2: hhh
    Field 3: iii

```Attempting to parse a fixed-width record file with no record separators:
```

test@ubuntu:~/Desktop$ cat test_none 
aaabbbcccdddeeefffggghhhiii
test@ubuntu:~/Desktop$ gawk '{printf "Record: %d\n\tField 1: %s\n\tField 2: %s\n\tField 3: %s\n", NR, $1, $2, $3}' FIELDWIDTHS="3 3 3" test_none
Record: 1
    Field 1: aaa
    Field 2: bbb
    Field 3: ccc

```When a newline or other record separator isn't present, GAWK just assumes that you only wanted the first 3 specified fields (3 fields with 3 characters each) from the entire line rather than chopping the line up into records of 9 characters. I tried using RS=".{9}" and then chopping up RT (which should contain the text matched by RS when RS is a regular expression), but that didn't seem to work for some reason:

```

test@ubuntu:~/Desktop$ cat test_none
aaabbbcccdddeeefffggghhhiii
test@ubuntu:~/Desktop$ gawk --posix '{print RT, NR}' RS=".{9}" FIELDWIDTHS="3 3 3" test_none
 1
 2
 3
 4

```As you can see, not only did it not work, but it actually gave me an incorrect record count as well. There should only have been 3 records since there are 18 characters in the file. I'm not sure if the special EOF is tested, but it shouldn't matter since it's not 9 characters long.

Do any of you know if there's something I'm missing that would make this work?

*Note: I know this can be done in other languages, but I'd really like to use GAWK if possible since it's already approved/installed in all the environments where I'd use this functionality, and I don't want to recreate all the other nice functions of GAWK.*

---

### Post by Desidero on 2011-04-27
I finally got it working using RT (needed the --re-interval option), but it's messy as hell. If any of you have a more elegant solution, please let me know!

```

test@ubuntu:~/Desktop$ gawk --re-interval -v fws="3 3 3" 'BEGIN{split(fws, fields, " ")} {val=1;print "Record " NR;for (x in fields){printf "\tField %s: %s\n", x, substr(RT,val,fields[x]); val+=fields[x]};print}' RS=".{9}" test_none
Record 1
    Field 1: aaa
    Field 2: bbb
    Field 3: ccc

Record 2
    Field 1: ddd
    Field 2: eee
    Field 3: fff

Record 3
    Field 1: ggg
    Field 2: hhh
    Field 3: iii

```

---

### Post by BkkBonanza on 2011-04-28
Why don't you just do it in bash/shell scripting? It can work quite well with fixed records by using string subscripts and substring operator.

See here for good reference on substring extraction in bash,

[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

eg.```


while read line; do
    echo ${line:0:3}
    echo ${line:3:3}
    echo ${line:6:3}
done<file.txt


```

You could make an array of record sizes and loop on that to break out any number of given record widths, (I just made this up but haven't checked syntax), eg.

```

records="3 3 3 5 3 2"
x=0
while read line; do
    for w in records; do
        echo ${line:x:w}
        x += w
    done
done<file.txt

```

---

### Post by Desidero on 2011-04-28
I can't read a line because the entire file is one line. The files I'm messing with are 10GB+ which won't fit in RAM. I'm trying to play with files without bringing the servers to their knees with 100% memory utilization and some swap file action.

The goal was to find a way to use GAWK's built-in fixed-width field separation (FIELDWIDTHS) along with some sort of record length limiter instead of an actual record separator (e.g. newline) to quickly and easily parse the files.

Thank you for your response though!

*edit*

I guess I have another request if anyone knows as well:
The substr function is a bit slow. Is there a faster way to chop up a string in awk? My test case with 10,000,000 small records takes ~50 seconds to parse a file with no delimiters using substr to get each field while a test script that does basically the same thing with a delimited file takes ~28 seconds. If you check the code, you'll see that I added a few unnecessary steps to the second one to try and make it so substr was the only significant difference:

This is parsing a 10,000,000 record file with no field or record separator (substr used to parse out fields):
```

time gawk --re-interval -v fws="3 3 3" 'BEGIN{split(fws, fields, " ")} {val=1;for (x in fields){printf "%s ", substr(RT,val,fields[x]); val+=fields[x]}print}' RS=".{9}" dumpfile >/dev/null

real    0m49.523s
user    0m47.339s
sys    0m1.012s

```This is parsing a 10,000,000 record file with " " as the field separator and "\n" as the record separator:
```

test@ubuntu:~/Desktop$ time gawk --re-interval -v fws="3 3 3" 'BEGIN{split(fws, fields, " ")} {val=1; for (x in fields){printf "%s ", $x; val+=fields[x]}print ""}' dumpfile2 >/dev/null

real    0m28.087s
user    0m26.554s
sys    0m1.320s

```The built-in parsing is obviously going to be faster than any custom parsing I can implement, but it'd be nice if I could get a bit closer than that. It takes over 50% longer.

---

### Post by BkkBonanza on 2011-04-28
Ah, yes, then read with -n option will read a fixed number of chars,

read -n 18 line

and not based on \n as terminator. In any case it seems you want to use GAWK even if it's less elegant/simple.

---

### Post by Arndt on 2011-04-28
> **Desidero said:**
> I can't read a line because the entire file is one line. The files I'm messing with are 10GB+ which won't fit in RAM. I'm trying to play with files without bringing the servers to their knees with 100% memory utilization and some swap file action.


I would probably write a small C program to convert the file into something which the advanced tools can handle better.

---

### Post by Desidero on 2011-04-28
> **BkkBonanza said:**
> Ah, yes, then read with -n option will read a fixed number of chars,

read -n 18 line

and not based on \n as terminator. In any case it seems you want to use GAWK even if it's less elegant/simple.

I prefer to use GAWK, but I'm not opposed to using something else if it's faster and still easy to work with field data. I would like to avoid compiled languages like C though since I'm not very familiar with C and I won't be performing the same operation every time. It's not very practical to compile a C program every time I want to do something with a data file. 

I wasn't aware of the -n option on read, so I tried it. Here are the results:

```

test@ubuntu:~/Desktop$ i=0
test@ubuntu:~/Desktop$ time while read -n9 line; do i=$((i+1)); done < dumpfile;echo $i

real    5m44.509s
user    3m0.939s
sys    2m39.342s
10000000

```

Not so good, and this is just for a basic record counter; it's not doing anything with the data. I do appreciate the suggestion though. If you can think of anything else, let me know!

---

### Post by DaithiF on 2011-04-28
breaking a single long line into shorter lines (representing records) sounds like a job for the fold command ... so if your records are 50 bytes each, (for example), then

```
fold -b -w 50 yourfile | gawk { do your fixed width field parsing here ...
```

---

### Post by DaithiF on 2011-04-28
or to use your example from above:
```
$ fold -b -w 9 testnone | gawk '{printf "Record: %d\n\tField 1: %s\n\tField 2: %s\n\tField 3: %s\n", NR, $1, $2, $3}' FIELDWIDTHS="3 3 3"
Record: 1
        Field 1: aaa
        Field 2: bbb
        Field 3: ccc
Record: 2
        Field 1: ddd
        Field 2: eee
        Field 3: fff
Record: 3
        Field 1: ggg
        Field 2: hhh
        Field 3: iii

```

---

### Post by BkkBonanza on 2011-04-28
> **Desidero said:**
> 
real    5m44.509s
user    3m0.939s
sys    2m39.342s
10000000


That does seem really slow but how does it compare to splitting with Gawk?

---

### Post by Desidero on 2011-04-28
> **DaithiF said:**
> or to use your example from above:
```

$ fold -b -w 9 testnone | gawk '{printf "Record: %d\n\tField 1: %s\n\tField 2: %s\n\tField 3: %s\n", NR, $1, $2, $3}' FIELDWIDTHS="3 3 3"
Record: 1
        Field 1: aaa
        Field 2: bbb
        Field 3: ccc
Record: 2
        Field 1: ddd
        Field 2: eee
        Field 3: fff
Record: 3
        Field 1: ggg
        Field 2: hhh
        Field 3: iii 
```

That's interesting. I'll have to try that out when I get home. I have to make sure that piping from fold to gawk doesn't load the entire file into memory. I'll let you know how it goes.





[QUOTE=BkkBonanza]That does seem really slow but how does it compare to splitting with Gawk?[/QUOTE]7.5 seconds. Gawk takes about 1/50 of the time that reading from bash takes... or you could say it's 4605% faster, which sounds pretty awesome!

```

time gawk --re-interval 'END{print NR}' RS=".{9}" dumpfile
10000000

real    0m7.481s
user    0m7.204s
sys    0m0.104s

```

---

### Post by DaithiF on 2011-04-28
> **Desidero said:**
> I have to make sure that piping from fold to gawk doesn't load the entire file into memory.
Theres no reason I can think of why it would ... so i'll be very surprised if thats what happens.

---

### Post by BkkBonanza on 2011-04-28
So you're saying that Gawk breaks up a 10GB file in 7.5 seconds? Or about 1.5 GB/s???
Something sounds not right. Even using dd to copy data would run about 5 minutes on many systems.

---

### Post by Desidero on 2011-04-28
> **BkkBonanza said:**
> So you're saying that Gawk breaks up a 10GB file in 7.5 seconds? Or about 1.5 GB/s???
Something sounds not right. Even using dd to copy data would run about 5 minutes on many systems.

Sorry, I didn't explain that well.

All of my tests were done at home rather than on live files in the work environment. My test file was 90,000,000 bytes (~86MB) and contained 10,000,000 records that were 9 bytes each. Each record consisted of 3 fields with 3 bytes each.

That works out to 12.2MB/sec using GAWK to get a record count or 0.25MB/sec using read to get a record count.

---

### Post by BkkBonanza on 2011-04-28
Ah, that makes a lot more sense. Still, I wonder by bash is so horribly slow!

---

### Post by Arndt on 2011-04-28
I didn't know about 'fold' when I suggested writing a special-purpose C program to transform the data file. My attempt at such a program are no faster than 'fold'.

---

### Post by Desidero on 2011-04-28
Very nice! This is perfect! Thanks so much for your help!

Timings with print
```

test@ubuntu:~/Desktop$ time fold -b -w 9 dumpfile | gawk '{printf "Record: %d\n\tField 1: %s\n\tField 2: %s\n\tField 3: %s\n", NR, $1, $2, $3}' FIELDWIDTHS="3 3 3" >/dev/null

real    0m38.296s
user    0m33.506s
sys    0m4.332s

```
Timing to count the number of records:
```

test@ubuntu:~/Desktop$ time fold -b -w 9 dumpfile | gawk 'END{print NR}' FIELDWIDTHS="3 3 3"
10000000

real    0m2.374s
user    0m0.008s
sys    0m2.304s

```

Timings for a less complicated print (basically just reformats it to the "standard" awk input format)
```

test@ubuntu:~/Desktop$ time fold -b -w 9 dumpfile | gawk '{print $1 " " $2 " " $3}' FIELDWIDTHS="3 3 3" >/dev/null

real    0m19.395s
user    0m12.817s
sys    0m8.037s

```

---

