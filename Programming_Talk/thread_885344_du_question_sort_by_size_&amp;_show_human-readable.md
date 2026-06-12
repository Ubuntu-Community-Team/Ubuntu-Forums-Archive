---
title: "du question: sort by size &amp; show human-readable sizes"
date: 2008-08-10
forum: Programming Talk
---

### Post by svk on 2008-08-10
Hello,

I'm trying to print out a listing of all the files (and subdirectories) within a directory along with their sizes.  I would like the output to be sorted by size (greatest to least), *and *in human-readable format.

-----------------

**EDIT on Jun 20, 2011: **As posted by [meithan]("http://ubuntuforums.org/showpost.php?p=10960739&postcount=14"), with GNU coreutils >= 7.5, which is available with Maverick and later, it's possible to do:

```

du -hs | sort -h

```Read on for the old discussion.

-----------------

Without that last restriction, I am able to generate a listing by running this command:
```

**serg@bijou:~/Pictures$ du -s ./* | sort -nr**
2172    ./Backgrounds
1540    ./100_1065.jpg
1448    ./100_1024.jpg
1192    ./100_1033.jpg
1136    ./100_1028.jpg
1128    ./100_1068.jpg
1088    ./100_1022.jpg
1032    ./100_1027.jpg
1016    ./100_1011.jpg
1008    ./100_1025.jpg
952    ./100_1021.jpg
944    ./100_1061.jpg
104    ./conference.jpg

```I can get the output in human-readable format by adding the **-h** switch to the **du** command; however, then the **sort -nr** command does not work properly (for example, it sorts 4.0K before 2.2M, because 4.0 is a bigger number than 2.2 -- it ignores the suffix).

Here's what I want the output to look like:

```

 2.2M    ./Backgrounds
1.6M    ./100_1065.jpg
 1.5M    ./100_1024.jpg
 1.2M    ./100_1033.jpg
 1.2M    ./100_1028.jpg
 1.2M    ./100_1068.jpg
 1.1M    ./100_1022.jpg
 1.1M    ./100_1027.jpg
 1016K    ./100_1011.jpg
 1008K    ./100_1025.jpg
 952K    ./100_1021.jpg
 944K    ./100_1061.jpg
 104K    ./conference.jpg

```Unfortunately, this one had to be hand crafted -- I don't know how I could rewrite the command to get it to show this.

Can sed or awk be used to accomplish this?  Or would I have to write a script?  I'm only marginally familiar with any of these tools, so I would like some help.

Thank you in advance!

---

### Post by ghostdog74 on 2008-08-10
you can write you own routine, or if you insist on using du
```

# du -k * | sort -nr | cut -f2 | xargs -d '\n' du -sh

```

---

### Post by svk on 2008-08-11
Thank you very much, very clever!  I understood each individual sub-command, but I wouldn't have thought of putting them together like this.

The only change I made to make it do *exactly* what I wanted:
du -k**s** * | sort -nr | cut -f2 | xargs -d '\n' du -sh
Because I didn't want it to descend into subdirectories.

Thank you very, very much!

---

### Post by jsaunders on 2009-10-05
Thanks for this!  Works great.  A slight twist if you will from my own personal usage (aliases stem from my slackware days, old habits die hard):

alias v='ls -lh'
alias vv="du --max-depth=1 -k | sort -nr | cut -f2 | xargs -d '\n' du -sh"

Cheers,

jsaunders

---

### Post by lavinog on 2009-11-09
> **jsaunders said:**
> Thanks for this!  Works great.  A slight twist if you will from my own personal usage (aliases stem from my slackware days, old habits die hard):

alias v='ls -lh'
alias vv="du --max-depth=1 -k | sort -nr | cut -f2 | xargs -d '\n' du -sh"

Cheers,

jsaunders

using vv|head gives a terminated by signal 13 message.
This seems to take care of that:
```

alias vv="du --max-depth=1 -k | sort -nr | cut -f2 | xargs -d '\n' du -sh 2>/dev/null"

```

I wrote a script before finding this thread to do a similar thing:
```

#!/bin/bash

# du-sort : Provides a sorted du in human readable format

# MAXDEPTH :  set to zero to show all
MAXDIR=1

# SORT ORDER  (true/false)
ASCENDING=true

# DEFAULT ARGUMENTS
ARGS='-xh'

# mktmp file
DATA=$(mktemp)

# ADD MAX-DEPTH ARG
if [ "$MAXDIR" -gt "0" ]
	then
	ARGS="$ARGS --max-depth=$MAXDIR"
fi

# CHECK FOR EXTRA ARGUMENT
if ! [ -z $1 ]
then
	ARGS="$ARGS $1"
fi

# RUN DU
du $ARGS >$DATA 2>/dev/null

# SORT DATA AND OUTPUT
if $ASCENDING
then
	for P in K M G
	do
		grep -e "[0-9]$P" $DATA|sort -n
	done

else
	for P in G M K
	do
		grep -e "[0-9]$P" $DATA|sort -nr
	done
fi

#remove datafile
rm $DATA

```

---

### Post by fusiondog77 on 2009-12-03
These all work but either require running du twice or using a temp file.  Here is a way to do it with neither using perl and a Schwartzian Transform [http://en.wikipedia.org/wiki/Schwartzian_transform](http://en.wikipedia.org/wiki/Schwartzian_transform)

du -shx | perl -e '%byte_order =  ( G => 0, M => 1, K => 2 ); print map { $_->[0] } sort { $byte_order{$a->[1]} <=> $byte_order{$b->[1]} || $b->[2] <=> $a->[2] } map { [ $_, /([MGK])/, /(\d+)/ ] } <>'

---

### Post by jackashe on 2010-06-03
fusiondog77 I was certainly looking for something that doesn't run du twice because I am dealing with > 5 minute times to run du.  Wanted to comment to say thanks!  Also, I use du --si, since the newest ubuntu versions use the si units.  in this case, kilobytes come from du as lowercase k, not uppercase K, so I made the following version of the perl:

perl -e '%byte_order = ( G => 0, M => 1, K => 2, k => 2 ); print map { $_->[0] } sort { $byte_order{$a->[1]} <=> $byte_order{$b->[1]} || $b->[2] <=> $a->[2] } map { [ $_, /([MGKk])/, /(\d+)/ ] } <>'

Another problem I had was zero size files don't have any suffix, and they got put between G and M.  Didn't try to fix this yet though.

---

### Post by lavinog on 2010-06-04
> **jackashe said:**
> fusiondog77 I was certainly looking for something that doesn't run du twice because I am dealing with > 5 minute times to run du.
That shouldn't be an issue because the kernel will buffer the file stats so subsequent du commands shouldn't take very long.

---

### Post by jackashe on 2010-06-04
oh it just dawned on my what to do in the final case!  When du is saying that the size is 0, there is no suffix, so perl is just using 0 as the byte order character.  So I fixed this by changing that part to '%byte_order = ( G => -3, M => -2, K => -1, k => -1);

---

### Post by jackashe on 2010-06-04
> **lavinog said:**
> That shouldn't be an issue because the kernel will buffer the file stats so subsequent du commands shouldn't take very long.

Even for Network attached storage?  I would imagine that by the time the first du finishes, enough time has passed that the first files logically checked might have changed and they would need to be rechecked.  In any case, seems the safest to do the du once -- otherwise you could technically get the result out of order since you are sorting the 2nd du based on the 1st.  not guaranteed to be the same.

---

### Post by marlar on 2010-07-01
It is true that it is faster in the second run, but for a deep directory structure, it is still much slower than using only one run for the du command.

I have used a command similar to #2 for a long time but was bothered about the slow speed.

Well, yesterday I played around with awk which until yesterday has been black magic to me. I have used it several times in snippets found on the net without really understanding what it did, and how. But finally I saw the light!

So I concocted this command which works well for me and only runs du once:

```
du --max-depth=0 -k * | sort -nr | awk '{ if($1>=1024*1024) {size=$1/1024/1024; unit="G"} else if($1>=1024) {size=$1/1024; unit="M"} else {size=$1; unit="K"}; if(size<10) format="%.1f%s"; else format="%.0f%s"; res=sprintf(format,size,unit); printf "%-8s %s\n",res,$2 }'
```It works by NOT having du output data in human readable format, but instead letting awk prettify the output.

Hope someone will find it useful. It took several hours to get it right, but now I master awk :p

---

### Post by jackashe on 2010-07-22
> **jackashe said:**
> oh it just dawned on my what to do in the final case!  When du is saying that the size is 0, there is no suffix, so perl is just using 0 as the byte order character.  So I fixed this by changing that part to '%byte_order = ( G => -3, M => -2, K => -1, k => -1);

The SI output also generates some sizes as decimals, e.g. 7.1MB. The pattern match for the numbers needs to be expanded to include an optional decimal point and more digits.
So my regex there went from /(\d+)/ to /(\d+\.?\d*)/

My final version:

%byte_order = ( G => -3, M => -2, K => -1, k => -1);

# to understand : read from "bottom" to "top"
## print list
## convert list of tuples into list of just zeroth element of tuple
## sort tuple list by byte_order hash of element one sub-sorted by direct compare of element two
## convert list into tuple list consisting of [actual element, match of du size char, match of du size number]
## read list from stdin
print map { $_->[0] }
      sort { $byte_order{$a->[1]} <=> $byte_order{$b->[1]} || $b->[2] <=> $a->[2] }
      map { [ $_, /([MGKk])/, /(\d+\.?\d*)/ ] }
      <>;

---

### Post by sparklyprgs on 2010-12-02
> **marlar said:**
> Well, yesterday I played around with awk which until yesterday has been black magic to me. I have used it several times in snippets found on the net without really understanding what it did, and how. But finally I saw the light!


Nice marlar!! Awk is still black magic for me. Maybe one day I will learn it as well as you. Until then I use this version of the "run du twice" example posted by ghostdog74 which outputs virtually identical info to your awk idea (but not as "neatly"):

```
du -k --max-depth=1 | sort -nr | cut -f2 | xargs -d '\n' du -sh
```

---

### Post by meithan on 2011-06-20
I apologize for reviving an old thread, but this is the first result in a Google search for "du sort human size", so I thought I'd post the answer I found to this problem for any subsequent google searchers:

```
du -hs | sort -h
```

However, this requires GNU coreutils >= 7.5, which should be available in most recent linux distros. It's available in Ubuntu since Maverick.

The sort command now supports sorting "human-readable" size numbers through the -h option.

---

### Post by lavinog on 2011-06-21
Nice.
Thanks for the update.

---

### Post by sarnobat on 2011-09-25
> **meithan said:**
> I apologize for reviving an old thread, but this is the first result in a Google search for "du sort human size", so I thought I'd post the answer I found to this problem for any subsequent google searchers:

```
du -hs | sort -h
```

However, this requires GNU coreutils >= 7.5, which should be available in most recent linux distros. It's available in Ubuntu since Maverick.

The sort command now supports sorting "human-readable" size numbers through the -h option.

Thanks a million. I had no idea. I had coreutils 8.10 (via MacPorts) and it didn't have this in the manpage. The other solutions had problems handling whitespace or execution time.

---

### Post by YordanGeorgiev on 2011-12-22
find $RootDir -exec du -BK --max-depth=0 {} \; | perl -ne 'm/^(\d{0,10})([K|M|G]\s+)(.*?)(StringToStartTheRelativePathsFrom\.)(.*)/g; printf ("%7d %1s %-8s%-120s \n" , $1 , $2  , $4 , $5) ' | sort -nr >> $FileReportRelativePaths

---

### Post by perat on 2012-08-06
Hi all,

In man sort I found this:
> 
       POS  is  F[.C][OPTS],  where F is the field number and C the character position in the field.  OPTS is one or more sin-
       gle-letter ordering options, which override global ordering options for that key.  If no key is given, use  the  entire
       line as the key.

       SIZE  may be followed by the following multiplicative suffixes: % 1% of memory, b 1, K 1024 (default), and so on for M,
       G, T, P, E, Z, Y.
 
How can I use it to sort output of "du -hs ./*" ?
I should set SIZE or POS variables or override global ordering? How I can do this?

---

### Post by SeijiSensei on 2012-08-06
What's wrong with

```
du -s * | sort -n
```

That does a numeric sort of the first field returned, in this case the size field.

---

### Post by trent.josephsen on 2012-08-06
> **perat said:**
> Hi all,

In man sort I found this:
 
How can I use it to sort output of "du -hs ./*" ?
I should set SIZE or POS variables or override global ordering? How I can do this?

This thread is nearly a year old; you should ask your question in a new one if the solutions already proposed don't do what you want.

---

### Post by jackashe on 2012-09-21
final improvement: when sizes are the same, sort by path name.  I needed this to ensure stable sort so I can more easily compare e.g. last week's usage with today's.

```

%byte_order = ( T => 4, G => 3, M => 2, K => 1, k => 1, 0 => 0);
print map { $_->[0] }
      sort { $byte_order{$b->[1]} <=> $byte_order{$a->[1]} || $b->[2] <=> $a->[2] || $b->[0] cmp $a->[0] }
      map { [ $_, /^\d+\.?\d*([TGMKk0])/, /^(\d+\.?\d*)[TGMKk]/ ] }
      <>;

```

---

### Post by garbelini on 2013-03-19
This is my favorite:

[http://packages.ubuntu.com/raring/ncdu](http://packages.ubuntu.com/raring/ncdu)

from this guy:

[https://github.com/yorhel/ncdu](https://github.com/yorhel/ncdu)

---

### Post by Charlietje on 2013-05-15
+1

> **garbelini said:**
> This is my favorite:

[http://packages.ubuntu.com/raring/ncdu](http://packages.ubuntu.com/raring/ncdu)

from this guy:

[https://github.com/yorhel/ncdu](https://github.com/yorhel/ncdu)

---

