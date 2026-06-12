---
title: "[SOLVED] Howto add a list of numbers (or find how much space *.mp4 takes)"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by timandjulz on 2008-10-20
I am trying to determine how much space all the mp4 files take up on my system.

Is there a command that takes a list of numbers and automatically adds them?

In lieu of that, I am using this command:

```
find . -iname '*.mp3' -printf "%k\n" | awk -- '{t+=$1} END {printf "%dKB\n", a}'

```

So basically I am looking for the most efficient method to accomplish totaling disk space used by *.mp3.

---

### Post by PointyWombat on 2008-10-21
Other than what you're already doing, I don't know how else to accomplish that via cli. I will recommend to you however this free little java app which does a great job of identifying and quantifying contents of a file system. I've been using this little app for years on Solaris and Linux.

It's called "JDiskReport" and you can get it from [http://www.jgoodies.com/freeware/jdiskreport/index.html](http://www.jgoodies.com/freeware/jdiskreport/index.html)

```

user@box:~/Desktop$ unzip jdiskreport-1_3_1.zip
Archive:  jdiskreport-1_3_1.zip
   creating: jdiskreport-1.3.1/
  inflating: jdiskreport-1.3.1/LICENSE.txt  
  inflating: jdiskreport-1.3.1/README.txt  
  inflating: jdiskreport-1.3.1/RELEASE-NOTES.txt  
  inflating: jdiskreport-1.3.1/jdiskreport-1.3.1.jar  
user@box:~/Desktop$ cd jdiskreport-1.3.1/
user@box:~/Desktop/jdiskreport-1.3.1$ ls
jdiskreport-1.3.1.jar  LICENSE.txt  README.txt  RELEASE-NOTES.txt
user@box:~/Desktop/jdiskreport-1.3.1$ java -jar jdiskreport-1.3.1.jar 

```

This brings up a graphical java app which allows you to mine your data and classifies it by extension, size, date, etc etc.. try it out and see if you like it. It's very fast and 10-fold better than Ubuntu's crappy 'Disk Usage Analyzer'. It will be able to tell you how big your mp3 collections are.

---

### Post by acidsolution on 2008-10-21
try this this must work 

```

 find . -name "*.mp3" -exec ls -lh {} \; | awk '{count=count+1;tot=tot+$5;printf "total count=%s   total size = %s mb \n ",count,tot}' | tail -2


```

this gives total size of the mp3 and total count 

hope this help you 
:):)

---

### Post by timandjulz on 2008-10-21
Thanks to both of you.

<rant> Linux is very powerful but it requires knowledge of so many commands to get some basic functionality.  It makes no sense that I can't use "ls" to list all mp3's in sub directories.  Nor does it make sense that "cp" can't copy all the mp3's in sub folders.  You have to string the commands together with "find", "awk", etc. </rant>

At least the GUI apps are getting much better for the average user.

Thanks again,
Tim

---

### Post by timandjulz on 2008-10-21
This adds the numbers with a running total:

```
find . -iname '*.mp3' -printf '%s + p ' | dc

```
dc is a calculator.  It places each number in a stack.  The "+" command tells it to add the number to the stack.  The "p" command tells it to print the results.

So if you have 3 files that are 10, 20 and 30 bytes respectively then dc will get this as input:
```
10 + p
20 + p
30 + p

```And the output will be a running total:
```
10
30
60

```

To see only the total (last number), use tail like so:
```
find . -iname '*.mp3' -printf '%s + p ' | dc | tail -1

```

---

