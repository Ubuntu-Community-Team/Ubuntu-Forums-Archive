---
title: "What the &quot;awk&quot; is wrong with this?"
date: 2009-03-10
forum: Programming Talk
---

### Post by manwithaplan on 2009-03-10
I've been diving into the realm of awk. Problem is.. I find it quite difficult being that I am only using the ABS guide and couple others. So grasping the concept is rather hard. I'm writing several scripts using dialog to show progress. I have successfully "with help" accomplished alot of answers into different usages of dialog.

My problem is with printing out the correct percentage of my tar extraction. I have successfully done this, except the progress bar goes off the chart.... e.g. 300% more or less.

So I am assuming that this has to do with the file size of the tar file. Do I need to count the contents of the file before I can extract? If so, how would I start with this? As you can see my awk is limited to the division of 240 (or any other definitive number). The thing is, this is fixed. And the a tar file can change file size.

Any suggestions?

```
 tarfile1='*.tar.bz2' 
   
    tar -xvjpf $tarfile1 2>&1 |
    awk '{ print (Total+=1)/240,"=>",$0}' |
    dialog --clear --gauge "Extracting Stage3...."  7 70
```

---

### Post by Martin Witte on 2009-03-10
> **manwithaplan said:**
> I've been diving into the realm of awk. Problem is.. I find it quite difficult being that I am only using the ABS guide and couple others. So grasping the concept is rather hard. I'm writing several scripts using dialog to show progress. I have successfully "with help" accomplished alot of answers into different usages of dialog.

My problem is with printing out the correct percentage of my tar extraction. I have successfully done this, except the progress bar goes off the chart.... e.g. 300% more or less.

So I am assuming that this has to do with the file size of the tar file. Do I need to count the contents of the file before I can extract? If so, how would I start with this? As you can see my awk is limited to the division of 240 (or any other definitive number). The thing is, this is fixed. And the a tar file can change file size.

Any suggestions?

```
 tarfile1='*.tar.bz2' 
   
    tar -xvjpf $tarfile1 2>&1 |
    awk '{ print (Total+=1)/240,"=>",$0}' |
    dialog --clear --gauge "Extracting Stage3...."  7 70
```

the dialog --gauge expects a percentage, if you do feed the dialog with something like below you feed it with percentages (number between 0 and 100) and not with a fraction between 0 and 1
```
martin@toshibap200:~$ tar cvf test.tar test.c test.cpp test.pl test.py test.sh test.ksh
test.c
test.cpp
test.pl
test.py
test.sh
test.ksh
martin@toshibap200:~$ nr=$(tar tvf test.tar 2>&1|wc -l)
martin@toshibap200:~$ echo $nr
6
martin@toshibap200:~$ tar xvf test.tar 2>&1|awk '{ print (Total+=1)/'$nr'*100,"=>",$0}' 
16.6667 => test.c
33.3333 => test.cpp
50 => test.pl
66.6667 => test.py
83.3333 => test.sh
100 => test.ksh

```

---

### Post by manwithaplan on 2009-03-10
Thank You Martin,

  It seemed that I wasn't clear with the percentage output. My math was all wrong. Though the output still exceeds to 111%. So I have I am assuming that I could change ```
Total=+1 to Total-=1
``` Would this have any merit. 
  Thank you for the clarification on the awk output.

EDIT: That didn't work... so I need to find out why I am off 1.1%... the extracted file has about 38900 files in it. There seems to be a math droop. Files that are smaller, seem absolutely perfect.

---

### Post by Martin Witte on 2009-03-11
when i execute this script, which prints all numbers between 0 and 38900, and then feeds the output to the awk script
```
martin@toshibap200:~$ cat test.bash 
#!/bin/bash
i=0
while [[ $i -lt 38901 ]]; do
	echo $i
	i=$(($i+1))
done|awk '{ print (Total+=1)/'38901'*100,"=>",$0}' 

```
the last lines are 
```
99.9794 => 38892
99.982 => 38893
99.9846 => 38894
99.9871 => 38895
99.9897 => 38896
99.9923 => 38897
99.9949 => 38898
99.9974 => 38899
100 => 38900
martin@toshibap200:~$ 

```
so my guess is something else is causing the 111%

---

### Post by geirha on 2009-03-11
You are redirecting stderr to stdout, so tar is probably printing some warnings in there, increasing the number of lines it prints to above the 38901. Try redirecting stderr to /dev/null or a file instead.

```
tar xvpf tarfile.tar 2>/dev/null | awk ...
```

---

### Post by manwithaplan on 2009-03-11
Thanks for the great responses... Actually I have experimented with several ways. I have used the 2>/dev/null with the same results. I open the file with archive manager and it is reporting 37000+. There must be some phantom lines "wc" is counting or its the file its self. I have re-written this many times. Just wish the file was .gz so I could list the contents before extraction, vs testing the file, with a fake extraction. Martin's example of the count is correct. And I have tested with a string, and a loop. 

I also have a large .git file I need extracting. It seems that "wc -l" does not count the line of hidden files. This has presented a strange problem. I would use zenity... or DCOP, but I want my scripts to be ran from any tty, and not X dependent. 

Here is my example as so far.
```

   tr=$(tar -tvf *tar.bz2 2>&1|wc -l)
   tar -xvf *tar.bz2 2>&1 |
  awk '{ print (Total+=1)*100/'$tr',"=>",$0}' |
   dialog --gauge "Extracting...."  7 70

```

And I have tried this:

```

tr=$(tar -tvf *tar.bz2 2>/dev/null | wc -l)
tar -xvjpf *tar.bz2 2>&1 |
  awk -v Total=$tr '{ print NR/Total*100,"=>",$0}' |
  dialog  --gauge "Extracting...."  7 70 

```

Both with the same results... Though maybe a rounding error... Though Martin has disproved this theory. There is an inaccuracy I cannot seem to find. 

Limitations that have baffled me since beginning this simple problem.

---

### Post by geirha on 2009-03-11
> **manwithaplan said:**
> 
tr=$(tar -tvf *tar.bz2 2>/dev/null | wc -l)
[COLOR="Red"]tar -xvjpf *tar.bz2 2>&1[/COLOR] |
  awk -v Total=$tr '{ print NR/Total*100,"=>",$0}' |
  dialog  --gauge "Extracting...."  7 70 
[/CODE]


The tar extracting (marked red) is the one you'll want to redirect stderr differently on ... Send stderr to a file and see how many lines there are (and what they are, if any).
```
tar -xvjpf filename.tar.bz2 2>/tmp/untar-errors.log | awk ...
```

BTW. the -f option of tar only takes one argument, so using the pattern "*tar.bz2" will fail if there is more than one archive that matches that pattern.

---

### Post by manwithaplan on 2009-03-12
Thanks for the advice... The output refers to permissions. And I was running this script as a user. I switched to root, and it WORKED!... it seems it was counting the error lines. Thanks for the help

---

