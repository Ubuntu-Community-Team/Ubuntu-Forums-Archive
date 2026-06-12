---
title: "awk command"
date: 2011-07-27
forum: Programming Talk
---

### Post by nandini_bn on 2011-07-27
Hello Everyone,
I am trying to write a command using awk but I am a bit stuck.... 
I need to compare the characters in 19th and 20th column and if they are of a particular pattern, it needs to be counted. So the file looks like this
Ref   Obs
                                       A          T
                                       T          C
                                       G        A 
                                       C        G
So I need them in two groups- Ti and Tv, so any combination of A-C, T-G, G-T and C-A needs to go under Tv and any combination of G-A , C-T, A-G and T-C needs to go under Ti. 

So I need the output like this:
Ti   Tv
24  20 

So I tried something out but obviously, its not the right one :
$ awk '
BEGIN {
        FORMAT="%-10s%-8s%-8s%-8s%s\n"
        {printf FORMAT,"Ti","Tv"}
      }
{  n[$1]++
    Tv1_[$1] += ($18 == "A")&&($19 == "C" )
    Tv2_[$1] += ($18 == "C")&&($19 == "A" )
    Tv3_[$1] += ($18 == "T")&&($19 == "G" )
    Tv4_[$1] += ($18 == "G")&&($19 == "T" )
    Ti1_[$1] += ($18 == "A")&&($19 == "G" )
    Ti2_[$1] += ($18 == "G")&&($19 == "A" )
    Ti3_[$1] += ($18 == "C")&&($19 == "T" )
    Ti4_[$1] += ($18 == "T")&&($19 == "C" )
}
END {
   for (i in n) {
      printf FORMAT,i,Ti_[Ti1,Ti2,Ti3,Ti4],Tv_[Tv1,Tv2,Tv3,Tv4]
   }
}' details.txt


Any suggestions ? Thank you.

---

### Post by Arndt on 2011-07-27
> **nandini_bn said:**
> Hello Everyone,
I am trying to write a command using awk but I am a bit stuck.... 
I need to compare the characters in 19th and 20th column and if they are of a particular pattern, it needs to be counted. So the file looks like this
Ref   Obs
                                       A          T
                                       T          C
                                       G        A 
                                       C        G
So I need them in two groups- Ti and Tv, so any combination of A-C, T-G, G-T and C-A needs to go under Tv and any combination of G-A , C-T, A-G and T-C needs to go under Ti. 

So I need the output like this:
Ti   Tv
24  20 

So I tried something out but obviously, its not the right one :
$ awk '
BEGIN {
        FORMAT="%-10s%-8s%-8s%-8s%s\n"
        {printf FORMAT,"Ti","Tv"}
      }
{  n[$1]++
    Tv1_[$1] += ($18 == "A")&&($19 == "C" )
    Tv2_[$1] += ($18 == "C")&&($19 == "A" )
    Tv3_[$1] += ($18 == "T")&&($19 == "G" )
    Tv4_[$1] += ($18 == "G")&&($19 == "T" )
    Ti1_[$1] += ($18 == "A")&&($19 == "G" )
    Ti2_[$1] += ($18 == "G")&&($19 == "A" )
    Ti3_[$1] += ($18 == "C")&&($19 == "T" )
    Ti4_[$1] += ($18 == "T")&&($19 == "C" )
}
END {
   for (i in n) {
      printf FORMAT,i,Ti_[Ti1,Ti2,Ti3,Ti4],Tv_[Tv1,Tv2,Tv3,Tv4]
   }
}' details.txt


Any suggestions ? Thank you.

I get this error:

```
awk: test.awk:3: fatal: not enough arguments to satisfy format string
	`%-10s%-8s%-8s%-8s%s
'
	            ^ ran out for this one
```

---

### Post by dethorpe on 2011-07-28
Not sure what you are trying to do , your sample data only has 2 columns, but you say you want to check the 19th & 20th!
 
Have you cut down the sample data to much, do you have an actual source data file you can post?
 
One thing I can see is that the format string has 5 placeholders but you only try to print 2 variables in the BEGIN block and 3 in the END block.

---

### Post by soltanis on 2011-07-30
I'm not sure about the awk code you posted, but here is something that does more or less what you ask:

```

# this function assumes that there are no pairings not containing T or A
function pair(a,b) { if (a == "T" || a == "A") { return a b } else { return b a } }

pair($19, $20) == "AC" || pair($19, $20) == "TG" { ti++ }
pair($19, $20) == "AG" || pair($19, $20) == "TC" { tv++ }

END { print "Ti", "Tv"; print ti, tv }

```

I assume you already set FS to something that properly splits your file fields up.

---

