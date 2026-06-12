---
title: "Syntax wildcard extension, command line."
date: 2013-10-11
forum: Programming Talk
---

### Post by XQbABnY on 2013-10-11
Hi All,

I am very new to this forum, so please feel free to let me know if I am just being a bit thick. Also, I apologise if this has already been answered in another thread, I did look. 


The problem:
I have a directory with many files in it, pics, and somewhere along the way I have accidentally doubled these files (in windows) so this is what it looks like (snippet):

DSC00142 (2).JPG  DSC00152.JPG      DSC00163 (2).JPG  DSC00173.JPG      DSC00184 (2).JPG  DSC00194.JPG      DSC00205 (2).JPG  DSC00215.JPG      DSC00226 (2).JPG
DSC00142.JPG      DSC00153 (2).JPG  DSC00163.JPG      DSC00174 (2).JPG  DSC00184.JPG      DSC00195 (2).JPG  DSC00205.JPG      DSC00216 (2).JPG  DSC00226.JPG
DSC00143 (2).JPG  DSC00153.JPG      DSC00164 (2).JPG  DSC00174.JPG      DSC00185 (2).JPG  DSC00195.JPG      DSC00206 (2).JPG  DSC00216.JPG      DSC00227 (2).JPG
DSC00143.JPG      DSC00154 (2).JPG  DSC00164.JPG      DSC00175 (2).JPG  DSC00185.JPG      DSC00196 (2).JPG  DSC00206.JPG      DSC00217 (2).JPG  DSC00227.JPG
DSC00144 (2).JPG  DSC00154.JPG  

So you can see what windows has done, in it's genius, it has created duplicates with the addition of '(2)' to the name. I would like to delete these with a single command - bare in mind the above files are just a few of them - there are some 15000 images to delete...

I would use the rm command to do this, however as I am still in the learning stage of command structure I will substitute with ls in order to view the damage before I commit to it. 

Here are the commands I have tried, please will someone tell me what the hell I am doing wrong :-) 

ls *['(2)']*
ls *["(2)"]*
ls *[2]*
ls *[' (2)']*
ls *[" (2)']*
ls *[' \(2\)]*
ls *[" \(2\)]*

All of the above commands produce a list of all files with a 2 in them. But what I need is a list of all files with (2) in them... It's driving me crazy :-( 

System Details:
Ubuntu 13.04 
Operated over Putty via SSH (no other form possible)

Please Help! 

Tim

---

### Post by drmrgd on 2013-10-11
I think you can just simply deleted these as normal (i.e. with the rm command), but escaping the parenthesis and space with a '\' character:

```

$ ls
file10 (2).txt  file1.txt      file3 (2).txt  file4.txt      file6 (2).txt  file7.txt      file9 (2).txt
file10.txt      file2 (2).txt  file3.txt      file5 (2).txt  file6.txt      file8 (2).txt  file9.txt
file1 (2).txt   file2.txt      file4 (2).txt  file5.txt      file7 (2).txt  file8.txt

$ rm file*\ \(2\).txt

$ ls
file10.txt  file1.txt  file2.txt  file3.txt  file4.txt  file5.txt  file6.txt  file7.txt  file8.txt  file9.txt



```

---

### Post by alan9800 on 2013-10-11
> **drmrgd said:**
> I think you can just simply deleted these as normal (i.e. with the rm command), but escaping the parenthesis and space with a '\' character:

```

$ ls
file10 (2).txt  file1.txt      file3 (2).txt  file4.txt      file6 (2).txt  file7.txt      file9 (2).txt
file10.txt      file2 (2).txt  file3.txt      file5 (2).txt  file6.txt      file8 (2).txt  file9.txt
file1 (2).txt   file2.txt      file4 (2).txt  file5.txt      file7 (2).txt  file8.txt

$ rm file*\ \(2\).txt

$ ls
file10.txt  file1.txt  file2.txt  file3.txt  file4.txt  file5.txt  file6.txt  file7.txt  file8.txt  file9.txt



```assuming that you have a lot of duplicated files with different names and extensions, wouldn't it be preferable the following command:```
find . -iname *(2).* -exec rm {} \;
```:?:

---

### Post by Vaphell on 2013-10-11
```
ls *['(2)']*
ls *["(2)"]*
ls *[2]*
ls *[' (2)']*
ls *[" (2)']*
ls *[' \(2\)]*
ls *[" \(2\)]*
```
you misunderstand the meaning of []. In shell globs and in regular expressions they describe classes of characters. [abc] = 1 ('a' OR 'b' OR 'c'), [0-9] = 1 digit, etc. In other words you tried to match **1 char** from the set of ( **'(' or '2' or ')'** ). Obviously 2 alone fulfills these criteria.

---

### Post by drmrgd on 2013-10-13
Yeah, you could certainly do it that way.  This way would especially be helpful if you have a directory tree to parse rather than just one directory to work in so you don't have all that shell globbing and recursion to think about.  However, for simple cases I think 'rm' has much less overhead than 'find' and would work more quickly and just as effciently:

```

$ time rm file*\ \(2\).txt


real    0m0.003s
user    0m0.000s
sys     0m0.000s

$ time find . -iname "*(2).*" -exec rm {} \;


real    0m0.033s
user    0m0.000s
sys     0m0.004s

```

Quite a bit more overhead as you can see, which for a small job isn't bad, but for a big one can really add up.

---

### Post by XQbABnY on 2013-10-23
Hey Thanks everyone! I didn't see these responses until now, - for some reason Ubuntu forum did not email me to let me know there was an update on the thread... Anyway, I actually found the answer along the way, - respect to Linux Forum on LinkedIn:

ls -l *\ \(2\).JPG 


then: 
rm -f *\ \(2\).JPG

- My real problem was ( as spotted by Vaphell ) getting confused between "[" and "(" in the syntax... I was studying bash scripting at the same time, and was just learning about the 'test' syntax, [ expression ] - :-( got confused... 
Anyways, thanks for the support!

---

