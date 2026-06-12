---
title: "Help with awk+ &quot;while read&quot;"
date: 2009-06-06
forum: Programming Talk
---

### Post by snori74 on 2009-06-06
Can anyone explain my odd results with awk+read line?

I have a stream of lines coming out of a mail.log grep which I want to process using awk. Doesn't seems to be working, so I created this wee test script to try to understand things:

**[FONT=&quot]#!/bin/bash[/FONT]**
 **[FONT=&quot]# echo "">t.txt[/FONT]**
 **[FONT=&quot]echo "1 able" > t.txt[/FONT]**
 **[FONT=&quot]echo "2 baker" >>t.txt[/FONT]**
 **[FONT=&quot]echo "3 charlie" >>t.txt[/FONT]**
 **[FONT=&quot]echo " - "[/FONT]**
 **[FONT=&quot]cat t.txt[/FONT]**
 **[FONT=&quot]echo " - "[/FONT]**
 **[FONT=&quot]while read LINE[/FONT]**
 **[FONT=&quot]do[/FONT]**
 **[FONT=&quot]# echo $LINE;[/FONT]**
 **[FONT=&quot] awk '{print $1, "-", $2}' ;[/FONT]**
 **[FONT=&quot]done <t.txt[/FONT]**
  
I would expect this to produce three lines, with each input line modifieed with a "-".
BUT, only the 2nd and 3rd lines appear. 

Why?

---

### Post by lloyd_b on 2009-06-06
> **snori74 said:**
> Can anyone explain my odd results with awk+read line?

I have a stream of lines coming out of a mail.log grep which I want to process using awk. Doesn't seems to be working, so I created this wee test script to try to understand things:

**[FONT=&quot]#!/bin/bash[/FONT]**
 **[FONT=&quot]# echo "">t.txt[/FONT]**
 **[FONT=&quot]echo "1 able" > t.txt[/FONT]**
 **[FONT=&quot]echo "2 baker" >>t.txt[/FONT]**
 **[FONT=&quot]echo "3 charlie" >>t.txt[/FONT]**
 **[FONT=&quot]echo " - "[/FONT]**
 **[FONT=&quot]cat t.txt[/FONT]**
 **[FONT=&quot]echo " - "[/FONT]**
 **[FONT=&quot]while read LINE[/FONT]**
 **[FONT=&quot]do[/FONT]**
 **[FONT=&quot]# echo $LINE;[/FONT]**
 **[FONT=&quot] awk '{print $1, "-", $2}' ;[/FONT]**
 **[FONT=&quot]done <t.txt[/FONT]**
  
I would expect this to produce three lines, with each input line modifieed with a "-".
BUT, only the 2nd and 3rd lines appear. 

Why?

Actually, I'm a bit surprised it works as well as it does.  The "read" and "awk" are both reading from the same input stream. The "read" gets the first line, while "awk" is getting the next two.

To illustrate this, run this script:```
#!/bin/bash
cat t.txt
echo " - "
while read LINE; do
   echo "Read ->"$LINE 
   echo -n "Awk ->"
   awk '{print $1, "-", $2}'
done < t.txt
```You'll clearly see that the read is consuming the first line of the file (storing it in $LINE), while the awk is consuming the other two lines.  The loop never actually loops.

You can get the results you want by letting awk handle the reading itself```
#!/bin/bash
cat t.txt
echo " - "
awk '{print $1, "-", $2}' t.txt
```

Alternately, if you *really* want that read loop, you need to call awk passing it $LINE on each pass```
#!/bin/bash
cat t.txt
echo " - "
while read LINE; do
    echo $LINE | awk '{print $1, "-", $2}'
done < t.txt
```

Lloyd B.

---

### Post by rjack on 2009-06-06
Here's the problem: the ```
read LINE
``` command, reads the first line of the file and puts it into $LINE.

But you **are not using** the $LINE variable inside the while loop :D
Instead, you call awk without specifying a file name, so that it defaults to standard input. But wait, the first line of stdin has already been read and standard input now starts with the second line of t.txt!

So awk receives from the second line to the end of t.txt

Here's the fixed version of your script:

```
#!/bin/bash
# echo "">t.txt
echo "1 able" > t.txt
echo "2 baker" >>t.txt
echo "3 charlie" >>t.txt
echo " - "
cat t.txt
echo " - "
while read LINE
do
echo $LINE | awk '{print $1, "-", $2}'
# echo $LINE;
# awk '{print $1, "-", $2}' ;
done <t.txt
```

Note that the problem you found shows that you don't need to loop the read command to feed awk.

Just do ```
awk '{print $1, "-", $2}' t.txt
``` and you'll be fine.

edit: lloyd_b has been faster :D

---

### Post by ghostdog74 on 2009-06-06
> **lloyd_b said:**
> 

Alternately, if you *really* want that read loop, you need to call awk passing it $LINE on each pass```
#!/bin/bash
cat t.txt
echo " - "
while read LINE; do
    echo $LINE | awk '{print $1, "-", $2}'
done < t.txt
```

Lloyd B.
this method is redundant and slow. Use only awk for file looping, no need while loop. Alternatively, if really want to use bash, then don't use awk. Use bash's own IFS, or string manipulation methods. Its faster this way.

---

### Post by snori74 on 2009-06-07
[SIZE=2]Thanks lloyd_b, rjack, and ghostdog74![/SIZE]

---

