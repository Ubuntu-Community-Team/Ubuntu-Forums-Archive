---
title: "Count unique in file, sort and display using gnuplot"
date: 2013-09-06
forum: Programming Talk
---

### Post by warsame on 2013-09-06
Hi

I'm new to python and I'm trying to solve an issue which I'm really stuck on.

I have a script which writes to multiple files one column.

Each file has the following content:
15
17
18
21
14
18
14
13
17
11
11
18
15
15
12
17
9
10
12
17
14
17
13
etc

Ideally I would like to have another file which would look like something like this:

9 2
10 0
11 25
12 50
13 53
14 53
15 63
etc

So that I can plot a graph using gnuplot with the first column as X-axis and second column as Y-axis. Output graphs as .pdf and .png.

I could really use your help on this, sincerely apology if this in the wrong section.

Thanks

---

### Post by steeldriver on 2013-09-06
You could do the counts with something like

```
cat *file* | sort -n | uniq -c
```

(the columns come out reversed i.e. counts to the left of values, but you can just swap them when you plot). If you want to aggregate ALL the files (it's not clear from your explanation) then you can just add them as additional arguments to cat

```
cat *file1* *file2 **file3 *| sort -n | uniq -c
```

or

```
cat *file**| sort -n | uniq -c
```

You can pipe the counts straight into gnuplot using the '-' special file

```
$ cat file1 file2 | sort | uniq -c | gnuplot -p -e "plot '-' using 2:1"
```

I'm sure you can figure out the output formats - you can use the 'set term' command inside interactive gnuplot to list the ones available on your system. For example, this seems to work for me:

```
 $ cat file1 file2 | sort | uniq -c | gnuplot -p -e "set term png; plot '-' using 2:1" > myplot.png
```

Hope this helps

---

### Post by warsame on 2013-09-06
At the moment I have the following script:

```
import os
from collections import Counter


p = './newR'
fd = os.listdir(p)
d = []
D = {}
for f in fd:
    pathN = os.path.join(p, f)
    for w in open(pathN, 'r'):
        if w in D:
            D[w] += 1
        else:
            D[w] = 1
for c, l in D.items():
    print '%s was found %d times' % (c, l)
```

Which produces the following output:
```
59 was found 3 times11 was found 2159 times
10 was found 1895 times
13 was found 4861 times
12 was found 4713 times
15 was found 5355 times
14 was found 5980 times
17 was found 4322 times
16 was found 3425 times
19 was found 1219 times
18 was found 2546 times
31 was found 6 times
30 was found 24 times
51 was found 3 times
50 was found 6 times
53 was found 3 times
52 was found 3 times
33 was found 12 times
55 was found 9 times
32 was found 3 times
```

The second script I have is this:
```
import osfrom collections import Counter


p = './newR'
fd = os.listdir(p)
for f in fd:
    pathN = os.path.join(p, f)
    with open(pathN, 'r') as infile:
                counts = Counter(l.strip() for l in infile)
        for line, count in counts.most_common():
            print line, count
```

Which produces the following output:

```
14 29115 254
12 232
13 226
17 212
16 145
18 127
11 102
10 87
19 64
21 33
20 24
22 15
9 15
23 9
30 6
60 3
55 3
25 3
```

Neither sort them so I can't even think about plotting until I sort these files out. I would greatly appreciate any help.

Also, I could make use of the gnuplot module like:
```
import Gnuplot
```

This is important because the script I will set it up on crontab to run daily which I'm hoping will produce daily graphs.

---

### Post by steeldriver on 2013-09-06
oops sorry I completely missed that you wanted to do this in python - if no-one else chimes in I will have a think about that, but I'm not really fluent in python

---

### Post by warsame on 2013-09-06
No problem, I could really appreciate with any input. At the moment I just want to find the unique and count with sorted numbers. After that I can start thinking of the gnuplot.

Thanks in advance

---

### Post by steeldriver on 2013-09-06
It looks like Collections are the way to go there

```

>>> with open('myfile','r') as f:
>>> . . .  data = f.read()
>>> data
'15\n17\n18\n21\n14\n18\n14\n13\n17\n11\n11\n18\n15\n15\n12\n17\n9\n10\n12\n17\n14\n17\n13\n'
>>> 
>>> import collections
>>> c = collections.Counter()
>>> c.update([int(d) for d in data.split()])
>>> 
>>> c
Counter({17: 5, 14: 3, 15: 3, 18: 3, 11: 2, 12: 2, 13: 2, 9: 1, 10: 1, 21: 1})
>>> 
>>> [(k,v) for k,v in c.items()]
[(9, 1), (10, 1), (11, 2), (12, 2), (13, 2), (14, 3), (15, 3), (17, 5), (18, 3), (21, 1)]
>>> 

```

---

### Post by warsame on 2013-09-07
Perfect, now I'm getting my desired results.

This is what I was doing:
```
 
[COLOR=#000000][FONT=Ubuntu Mono]
 p = './newR'[/FONT][/COLOR]fd = os.listdir(p)
for f in fd:
    pathN = os.path.join(p, f)
    with open(pathN, 'r') as infile:
                counts = Counter(l.strip() for l in infile)
        for line, count in counts[COLOR=#ff0000]**.most_common()**[/COLOR]:
            print line, count
```

I was using ```
most_common()
``` which I was having the most problem with. I have tried ```
.items()
``` once but didn't observe the data before shelving it. Thank you very much.

---

### Post by warsame on 2013-09-07
Actually I have a problem, I have just realised.

This is the script I run to get the unique count:

```

import os
from collections import Counter


def main():
    p = './newR'
    fd = os.listdir(p)
    countUniq(p, fd)


def writeFile(fd, fhp, fcount):
    fo = './nnewR/'+fd+'.txt'
    with open(fo, 'a') as f:    
        r = '%s %s\n' % (fhp, fcount)
        f.write(r)


def countUniq(path, dirs):
    for pfiles in dirs:
        pathN = os.path.join(path, pfiles)
        with open(pathN, 'r') as infile:
#        infile = open(pathN, 'r')
        data = infile.read()
        fileN = os.path.basename(pathN)
        stripFN = os.path.splitext(fileN)[0]
        fDate = stripFN.split('_')[0]
        countr = Counter()
        countr.update([int(d) for d in data.split()])
        for line, count in countr.items():
            writeFile(fDate, line, count)
#                print fDate, line, count
#    infile.close()
main()
```

I get the following files:

```
20130813.txt
20130819.txt
20130825.txt
20130831.txt
etc

```

If I open the first one this is what it looks like:

```
51 4
9 4
10 36
11 48
12 132
13 144
14 148
15 133
16 52
17 105
18 61
19 20
20 12
21 16
22 20
23 8

```

The second file:

```
28 4
9 20
10 122
11 136
12 298
13 302
14 397
15 314
16 218
17 264
18 148
19 93
20 32
21 49
22 16
23 13
24 8
25 4
60 4
```

This is very strange, I don't know why it doesn't start with the smallest count. Any advise, I would really appreciate it. 

I'm suspecting it has to do with the loop I@m doing when I'm reading the file, but because I'm new to python I cannot be sure or try to solve it.

---

### Post by Bucky Ball on 2013-09-07
*Thread moved to **Programming Talk**.*

---

### Post by warsame on 2013-09-07
My sincere apology for posting this in the wrong sub forum.

I could really use some input and advise.

Thanks

---

### Post by Bucky Ball on 2013-09-07
All good. Unfortunately I wouldn't have a clue. Not my area, sorry, but you may have more luck here. :)

---

### Post by warsame on 2013-09-07
I have sorted the issue now

```
for line, count in sorted(countr.items()):
```

I had to sort the keys with sorted().

Anyone who has any future issue with this like me can hopefully see this.

Thanks

---

### Post by warsame on 2013-09-07
> **Bucky Ball said:**
> All good. Unfortunately I wouldn't have a clue. Not my area, sorry, but you may have more luck here. :)

Thank you for your consideration, I have posted a solution now. Hopefully any future n00b like myself can make use of this.

---

### Post by Bucky Ball on 2013-09-07
No probs. Glad you got it fixed and you can help steer others here by marking the thread as solved from 'Thread Tools' at top right. Cheers and good luck with it all. ;)

---

### Post by warsame on 2013-09-07
> **Bucky Ball said:**
> No probs. Glad you got it fixed and you can help steer others here by marking the thread as solved from 'Thread Tools' at top right. Cheers and good luck with it all. ;)

Thank you
I just did that, sorry about that. This has been very informative and helpful forum and I hope somehow me asking these questions somehow contributed ;)

---

