---
title: "Grep sed or awk??"
date: 2011-10-07
forum: Programming Talk
---

### Post by noob_newbie on 2011-10-07
Hi,
I have one huge file which has a lot of messy data, I have managed to grep them and put all the interesting data in one file. The data now appears like this-

aa
bb
cc
dd
aa
bb
cc
dd

I want to arrange it like this
aa bb cc dd
aa bb cc dd

How do I do this and which is the best tool to do so?? I tried searching for solutions but no luck so far..

Pl help me out :(

I also have some leading blank spaces in some fields, how do I remove them as well?

Thanks in advance..

---

### Post by Vaphell on 2011-10-07
grep and sed won't do much here, grep is for searching, sed is suited for transformations on per-line basis (it can work with multiple lines at once, but it's annoying). Awk, perl, bash, python would be better suited.

removing leading spaces is simple
```
sed -r 's/^\s+//' input.file > output.file
```

awk:
```
$ echo $'a\nb\nc\nd\na\nb\nc\nd'
a
b
c
d
a
b
c
d

$ echo $'a\nb\nc\nd\na\nb\nc\nd' | awk '{if((NR%4)==0) { printf("%s\n",$0)} else { printf("%s ",$0)}}'
a b c d
a b c d

```
awk '<stuff>' input.file > output.file should do

---

### Post by karlson on 2011-10-07
> **noob_newbie said:**
> Hi,
I have one huge file which has a lot of messy data, I have managed to grep them and put all the interesting data in one file. The data now appears like this-

aa
bb
cc
dd
aa
bb
cc
dd

I want to arrange it like this
aa bb cc dd
aa bb cc dd

How do I do this and which is the best tool to do so?? I tried searching for solutions but no luck so far..

Pl help me out :(

I also have some leading blank spaces in some fields, how do I remove them as well?

Thanks in advance..

I would suggest looking into Perl or Python rather then trying to grep, awk and sed your way through reformatting the data to your liking.

---

### Post by noob_newbie on 2011-10-07
Thanks for your response vaphell and karlson :)

i have solved that issue using vaphell's solution. I have run into another now. It is almost similar

I have 5 files each having data like this- 
Files:  1      2      3    4    5
           a1   b1   c1  d1  e1
           a2   b2   c2  d2  e2
           a3   b3   c3  d3  e3
           a 4  b4   c4  d4  e4

Is there a way to put it all in a single file like this

   a1 b1 c1 d1 e1
   a2 b2 c2 d2 e2
   a3 b3 c3 d3 e3
   a4 b4 c4 d4 e4
   a5 b5 c5 d5 e5

Thanks a lot guys!

---

### Post by noob_newbie on 2011-10-07
hi

Managed to do it with this command

paste time.txt mac_src.txt mac_dst.txt ip_src.txt ip_dst.txt | sed -e 's/\t\t\t/\t/g;s// /g;s//\t/g'

Is there a more efficient way??

---

### Post by Arndt on 2011-10-07
> **noob_newbie said:**
> hi

Managed to do it with this command

paste time.txt mac_src.txt mac_dst.txt ip_src.txt ip_dst.txt | sed -e 's/\t\t\t/\t/g;s// /g;s//\t/g'

Is there a more efficient way??

Does this do what you want?

```
cat time.txt mac_src.txt mac_dst.txt ip_src.txt ip_dst.txt
```

---

### Post by noob_newbie on 2011-10-07
Hi Arndt
What you said puts all files in the same column, I want them to be in 5 seperate columns..

Thanks.

---

