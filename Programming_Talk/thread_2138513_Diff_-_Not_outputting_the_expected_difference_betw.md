---
title: "Diff - Not outputting the expected difference between two text files"
date: 2013-04-24
forum: Programming Talk
---

### Post by _user on 2013-04-24
Below is a script which compares the daily top 1m URL list from Alexa to a master file.  It runs daily and outputs any new URLs which are added to the top 1m list by Alexa and aren't in the master list.

Problem: The diff line isn't producing the intended outcome.  I want diff to output any lines that exist in top-1m-formatted1.csv but don't exist in master1.csv.

[https://dl.dropboxusercontent.com/u/8528853/diff_23_04_2013](https://dl.dropboxusercontent.com/u/8528853/diff_23_04_2013)
[https://dl.dropboxusercontent.com/u/8528853/diff_24_04_2013](https://dl.dropboxusercontent.com/u/8528853/diff_24_04_2013)

These two links show the outputted URLs from the last 2 days.  As you can see from the list there are lots of duplicates in there.  Where am I going wrong?

```
#!/bin/sh

cd $Alexa-1m
rm -rf top-1m.csv.zip
rm -rf top-1m.csv
rm -rf top-1m-formatted.csv
rm -rf top-1m-formatted1.csv
rm -rf difference
rm -rf master1.csv
wget http://s3.amazonaws.com/alexa-static/top-1m.csv.zip
unzip top-1m.csv.zip
sed -ne "s/^[^,]\+,//p" top-1m.csv > top-1m-formatted.csv
awk '{print length, $0}' master.csv | sort -n | awk '{$1=""; print $0 }' > master1.csv
awk '{print length, $0}' top-1m-formatted.csv | sort -n | awk '{$1=""; print $0 }' > top-1m-formatted1.csv
diff master1.csv top-1m-formatted1.csv |grep "^>" > difference
now=$(date +"%d_%m_%Y")
sed -ne "s/^[^ ]\+ //p" difference > diff_$now
cat diff_$now >> master.csv
cp diff_$now $Public

```

The awk and sed lines are used for formatting purposes to sanitized the file/s to just give the domain name and nothing else.

---

### Post by MadCow108 on 2013-04-24
so you want the complement of the two files? that can be done with sort and uniq:
# lines in a but not in b
sort b b a | uniq -u

---

### Post by schragge on 2013-04-24
+1
Or use [combine]("http://manpages.ubuntu.com/manpages/raring/en/man1/combine.1.html") from package moreutils:
```
combine a not b
```
On large files like these, it should perform better.

If both files are already sorted then ```
comm -23 a b
``` will also do the trick.

---

### Post by MadCow108 on 2013-04-24
this is still quite fast without needing an extra package
```
sort -u b > tmpb; sort -u a | sort -m tmpb tmpb - | uniq -u > out
```
it might outperform combine if you have enough cpu cores and a large dataset as sort is multithreaded.

---

### Post by _user on 2013-04-24
Thanks for the input - I used sort on this occasion which did the trick.

Can you tell me why diff didn't work in my example?

---

