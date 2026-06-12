---
title: "awk script for school."
date: 2012-05-08
forum: Programming Talk
---

### Post by Alphamonkey on 2012-05-08
I have no idea about how to go about this I made one that was somewhat successful but not what my teacher wants. This is a description of what he wants:

Writing an awk script
(25 points) Using the passwd file for practice, write an awk script called script10.2 that will print
the following report.
1. Print a header telling who prepared the report (you).
2. Print the username, class, and default shell for each record, separated by tabs.
3. Print a summary telling how many records are in the file and how many use each shell.
Your scripts should assume that the files are in the same directory as your script; don't specify files in
your directory.
Your scripts should work even if the files contain different information -- don't write your scripts
specifically for the exact data in these particular files.


Mine was along the lines of:

```

#Script 10.2
BEGIN {FS = " : "} {print "File was prepared by XXXX XXXX."}
{print $1, "\t", $4, "\t", $6}
/\/bin\/bash/ {print $7; count ++}
END {print "there are "NR" records and "count" use bash."}

```but the output i get is 


File was prepared by XXXX XXXX.
1234:x:14661:14661:cnet146:/home/libo:/bin/bash            

File was prepared by XXXX XXXX.
5678:x:14662:14662:cnet146:/home/khsa:/bin/bash            

File was prepared by XXXX XXXX.
9101:x:14663:14663:cnet146:/home/sinv:/bin/bash            

there are 25 records and 25 use bash.


sorry  : x : is showing as :x:


Please help. I think the problem lies with the BEGIN { FS " = " }. Also, I don't know how he expect to make this apply to any file. Thanks for any help.

PS. Sorry if this is messy. I tried to make it somewhat organized.

---

### Post by LemursDontExist on 2012-05-08
Generally homework questions are discouraged here.  That said, I think giving hints is ok?

Anyway, you're definitely on the right track - I would think about what 

```
{ FS = " : "}
```

is actually doing.  It's close, but not quite right.  

Also, what's BEGIN do, and how should that change your code?

---

### Post by Vaphell on 2012-05-08
giving hints is ok, doing someone else's work not so much

```
File was prepared by XXXX XXXX.
1234 	 14661 	 /home/libo
/bin/bash
there are 1 records and 1 use bash.
```
if that's the output you want, your script does that just fine with fixed field separator (certainly it's not SPACE+:+SPACE)

---

### Post by Alphamonkey on 2012-05-08
Thanks for the replies. I was not in anyway asking for my homework to be "done for me" I just was completely stuck and looking for any sort of help. I'll give it another shot and see what the results are. Thanks again.

---

### Post by Alphamonkey on 2012-05-08
Ok. I did this:

#Awk script 
#Script 10.2
BEGIN {FS=":"; print "File was prepared by XXXX XXXX."};
{print $1, "\t", $5, "\t", $7}
/\/bin\/bash/ {print $7; count ++}
END {print "there are "NR" records and "count" use bash."}

and it seems to be working just fine now. Thank you both very much for you help, especially you Vaphell. You helped me out a lot last time I had a question about awk and bash. Thanks guys.[]("http://ubuntuforums.org/member.php?u=347382")

---

### Post by cajual on 2012-05-08
The FS is set wrong, it shouldn't have any spaces.

```
BEGIN { FS = ":" } **;** { print $1 }
```

---

