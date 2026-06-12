---
title: "Pythoin list. limit size?"
date: 2006-05-18
forum: Programming Talk
---

### Post by Zizo on 2006-05-18
Hi all,

I am new to python. I have a file with 2 columns of data (around 50000 field in each column). I want to extract the data from the first column and put them in a list or array. I am doing the following:

listVar = []
f = open(fileName, r)

data = [line.split('\t') for line in f]

listVar = ([d[0] for d in data])

#Now when I go through the list index by index
for i in raneg(0, 50000):
   print i, listVar[i]  #for example

This is successful until i = 972  then I get the following message:
 IndexError: list index out of range.

I have tried different ways of allocating the list but I keep getting the limit of 972. In other code I didn't have this problem: the list was ok with huge number of data. Could it be from the way I am extracting the data from the file?

Thank you in advance.

---

### Post by thumper on 2006-05-18
I have used lists with thousands, and at work some other guys have used lists with over half a million items, so no - I don't think you are hitting a limit on the list.

Have you tried printing out the list that you think is over 50000 items long?

Tried a test?
```
if len(listVar) < 50000:
    print listVar
    raise ValueError, "hmm... expected bigger"

```

You do have a pair of redundant braces which made me think "does he want a tuple?"

```
listVar = ([d[0] for d in data])
# same as
listVar = [d[0] for d in data]
```

Try using xrange instead of range.  It won't fix your problem but it will be more efficient (xrange is a generator whereas range creates the whole list first).

Note: use the CODE tags to format your code or you'll loose the indentation.

---

### Post by unbuntu on 2006-05-18
[QUOTE=Zizo]Hi all,

I am new to python. I have a file with 2 columns of data (around 50000 field in each column). I want to extract the data from the first column and put them in a list or array. I am doing the following:

listVar = []
f = open(fileName, r)

data = [line.split('\t') for line in f]

listVar = ([d[0] for d in data])

#Now when I go through the list index by index
for i in raneg(0, 50000):
   print i, listVar[i]  #for example

This is successful until i = 972  then I get the following message:
 IndexError: list index out of range.

I have tried different ways of allocating the list but I keep getting the limit of 972. In other code I didn't have this problem: the list was ok with huge number of data. Could it be from the way I am extracting the data from the file?

Thank you in advance.[/QUOTE]

It can't be the limited size problem.  I've processed a much lengthier list than 972 lines...If you'd like to, you can post the minimal program that demonstrates the exact problem.

---

### Post by Zizo on 2006-05-19
First thank you for your replies. And now I will explain what I am doing in more details.
 
 I have 3 separate files, test1.txt, test2.txt and test3.txt. Each of these files contains 2 columns of 10000 lines of data values
  0.72344            10
  0.75232            2
  etc                    etc
 
 the columns are separated with a '\t' .
 
 I first concatenate these files into a file called **concat.txt**, and then I want to only extract the first column of **[COLOR=Black]concat.txt[/COLOR]** into a list or array so I can make statistical computation of these values. Following is my code:
 
 First this how I execute it: **./concatenate.py 3 test 10000 concat.txt**
 **3** is the number of files I have (test1.txt, test2.txt and test3.txt)
 **test** is the prefix of those files
 **10000** is the number of lines in each file
 **concat.txt** is the resultant concatenated file
 
 import sys, os
 import math, string
 
 
 if (len(sys.argv) < 4):
     print 'usage: ./concatenate.py <number of files to be concatenated>
     <prefix  of files to be concatenated> <number of pings per file> 
     <name of resultant file>'
     sys.exit() 
 else:
     numberOfFiles = int(sys.argv[1])
     originalFiles = sys.argv[2]
     numberOfPingsPerFile = int(sys.argv[3])
     concatFile = sys.argv[4]
 
 buffer = ''
 
 totalNumberOfPings = numberOfFiles * numberOfPingsPerFile
 
 latencyList = []
 
 for i in xrange(1, numberOfFiles + 1):
     readFile = originalFiles+"%d.txt" %i
     file = open(readFile, 'r')
 
     buffer = buffer + file.read()
     file.close()
 
 f = open(concatFile, 'w')
 f.write(buffer)
 f.close()
 
 # here I read the concatenated file and start taking data to latencyList[]
     # I could have used f = open(concatFile, 'w+') above and the seek to its
     # beginning.
 
 fl = open(concatFile, 'r')      
 
 data = [line.split('\t') for line in fl]
 
 fl.close()
 
 latencyList = [d[0] for d in data]
 
 print len(latencyList) # here you can check the limit problem I am having
 
 # here you can see it as well.
 j=0
 while 1: 
     print j, latencyList[j]
     j = j+1
 
 [B]P.S: I tried this prgram on my laptop which has less memory than the
        one I used it before and the result was i = 527 and sometimes 403.

If there is a better way to concatenate and the extract those values in an array or list, that would be better.

[/B]Thank you again.

---

### Post by unbuntu on 2006-05-19
[QUOTE=Zizo]
If there is a better way to concatenate and the extract those values in an array or list, that would be better.

[/B]Thank you again.[/QUOTE]

Well...if you just want to get the job done, UNIX commands would be a lot easier:
```

cat test*.txt | cut -f 1

```

Having inspected your code yet, but processing files with 30000 lines should be peanuts for your computer even with less memory...must have something wrong here:-k

---

### Post by thumper on 2006-05-19
USE CODE BLOCKS!

It prevents us having to guess your indentation.

If the intent of the script is to do everything in one file, why write out the concatenated one?  What is your expected behaviour if there are blank lines in the middle?

Have you tried printing out the lengths of the files you are reading?  Is the reading failing somewhere?  Are there end of file markers in the middle of the file perhaps?

```
out = open('outputfile.txt','w')
for i in (1,2,3):
   f = open('test%d.txt' & i)
   lines = f.readlines()
   print "file %d has %d lines" % (i, len(lines))
   out.writelines(lines)
   f.close()
out.close()

```
What do you get?  Is it what you expect?

---

### Post by Van_Gogh on 2006-05-19
try 
```

print len(listVar)

```
My guess is your list is of length 972. This means as you try to access item 973, you're out of your list's range - just as the error message says...

A way to avoid this type of problem is to do it this way instead:
```

i=0
for item in listVar:
  i = i+1
  print i, listVar[i]

```

---

### Post by Zizo on 2006-05-19
Thank you again for helping me.
 
Actually I found out that there is no problem in the list.  And there is no technical problem as well.  The problem is that I just missed a crucial information which has to do with the amount of data that I really have which turned to be less than I expected and that's why I was having this range limit.
 
The problem is solved.

---

