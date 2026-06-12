---
title: "[Python -Newbie]  is this correct ?"
date: 2009-11-29
forum: Programming Talk
---

### Post by baskar007 on 2009-11-29
I have a list of part files (that is many parts of single file).

I want to append all parts into a single file to make a full file.

I used this code:

```

import os
l = ["home/baskar/1.part","home/baskar/2.part","home/baskar/3.part"]

source_file ="/home/baskar/source.file"

re_size = 0
buffer = 10*1024   #10 KiB's
for x in range(len(l)):
    target_size = os.path.getsize(l[x])
    part = open(l[x],"r")
    while 1:
        output = part.read(buffer)
        re_size = re_size + len(output)
        F = open(source_file,"ab")
        F.write(output)
        F.close()
        if re_size == target_size:
            break
        else:print "Appending file",l[x]


```

This code works perfectly ,But it takes much long time for appending file, even small file like 5mb file takes 3 min:mad: to complete.

Is there is any way to append file or is there is any wrong with my code ?

if anyone know please tell me.:confused:

---

### Post by benj1 on 2009-11-29
why not this ?
```
l = ["home/baskar/1.part","home/baskar/2.part","home/baskar/3.part"]

for part in l:
    open("/home/baskar/source.file","a").write(open(part).read())
```

you certainly don't need the while loop, and associated checks

---

### Post by snova on 2009-11-29
> **benj1 said:**
> why not this ?
```
l = ["home/baskar/1.part","home/baskar/2.part","home/baskar/3.part"]

for part in l:
    open("/home/baskar/source.file","a").write(open(part).read())
```

you certainly don't need the while loop, and associated checks

I think the point is so as not to read the files all at once.

I'm only guessing at the bottlenecks here, but I suspect a significant problem is that you reopen the output file every time you read a block.

Your for loop can be significantly improved by not iterating over the indexes, but the filenames themselves. You aren't using the index anyway. (see benj1's code for an example of this)

Your method of testing for the end of the file can be simplified. Just compare the length of the string that read() returned to the size you expected, and if it did not return enough, it has met EOF.

In addition, I think 10 KB is a rather small block size.

My version:

[php]
import os.path

Files = ["1.part", "2.part", "3.part"]
OutFile = "source"

ReadSize = 1024 * 1024 # 1 MB

out = open(OutFile, "a")

for filename in Files:
    # Context manager (with statement). Ensures the file is closed, without doing it myself
    with open(filename) as file:
        while True:
            tmp = file.read(ReadSize)
            out.write(tmp)
            if len(tmp) != ReadSize:
                break
[/php]

---

### Post by Can+~ on 2009-11-29
If files are small, you could load them into main memory and write them all at once.

---

### Post by baskar007 on 2009-11-30
while loop
 If the file is too large reading of full file takes large memory ?

---

### Post by baskar007 on 2009-11-30
> **snova said:**
> I think the point is so as not to read the files all at once.

I'm only guessing at the bottlenecks here, but I suspect a significant problem is that you reopen the output file every time you read a block.

Your for loop can be significantly improved by not iterating over the indexes, but the filenames themselves. You aren't using the index anyway. (see benj1's code for an example of this)

Your method of testing for the end of the file can be simplified. Just compare the length of the string that read() returned to the size you expected, and if it did not return enough, it has met EOF.

In addition, I think 10 KB is a rather small block size.

My version:

[php]
import os.path

Files = ["1.part", "2.part", "3.part"]
OutFile = "source"

ReadSize = 1024 * 1024 # 1 MB

out = open(OutFile, "a")

for filename in Files:
    # Context manager (with statement). Ensures the file is closed, without doing it myself
    with open(filename) as file:
        while True:
            tmp = file.read(ReadSize)
            out.write(tmp)
            if len(tmp) != ReadSize:
                break
[/php]
Thank you,
Now i got an idea.

I have one more question :
Is there is any other way to move all files in to a single file?

---

### Post by snova on 2009-11-30
> **baskar007 said:**
> while loop
 If the file is too large reading of full file takes large memory ?

A plain read() call will pull the entire file into memory. Memory is getting cheap and files aren't generally huge, but it's not the best idea.

> **baskar007 said:**
> Thank you,
Now i got an idea.

I have one more question :
Is there is any other way to move all files in to a single file?

How about cat? It just occurred to me:

```
cat 1.part 2.part 3.part > source
# Or even this:
cat *.part > source
```

---

### Post by baskar007 on 2009-12-02
> **snova said:**
> A plain read() call will pull the entire file into memory. Memory is getting cheap and files aren't generally huge, but it's not the best idea.



How about cat? It just occurred to me:

```
cat 1.part 2.part 3.part > source
# Or even this:
cat *.part > source
```
is *cat* is python code?

---

### Post by nvteighen on 2009-12-02
> **baskar007 said:**
> is *cat* is python code?

No, it's a command line utility.

---

### Post by DaithiF on 2009-12-02
> **baskar007 said:**
> is *cat* is python code?
+1 for cat.  if it has to be python, you could cheat by wrapping python around cat :p
```
import subprocess
subprocess.Popen('cat %s > newfile.txt' % ' '.join(files), shell=True)
```though cats don't normally like being wrapped by pythons ;)  melon helmets are fine tho.

---

### Post by fiddler616 on 2009-12-02
> **DaithiF said:**
> though cats don't normally like being wrapped by pythons
Classy.

Does subprocess.Popen(str) arbitarily run str through a bash interpreter? Are there any limits? I feel like this could get out of hand, although I guess bash has:
```
python -c "<insert code here>"
```

---

### Post by DaithiF on 2009-12-03
> **fiddler616 said:**
> Classy.

Does subprocess.Popen(str) arbitarily run str through a bash interpreter? 

no, not unless you pass True for the Shell parameter.

---

