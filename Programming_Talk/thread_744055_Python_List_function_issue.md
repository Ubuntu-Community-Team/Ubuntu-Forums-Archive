---
title: "Python: List function issue"
date: 2008-04-03
forum: Programming Talk
---

### Post by regomodo on 2008-04-03
`

---

### Post by ghostdog74 on 2008-04-03
> **regomodo said:**
> Hi,
I can't get my head around why i can't get import data from a file and put the into an array for further manipulation.

My data that is going to be read in is this

```
140,385,384,384
141,385,383,383
142,386,383,383
143,385,383,383
144,385,383,383
145,385,383,383
146,385,383,383
147,385,383,383
148,385,383,383
149,387,385,385
150,385,384,384
151,385,382,382
152,385,383,383
153,386,384,384
154,386,384,384
```

My python code (just initial stuff) is this:
```
f=open("log.txt", "r")
x=[]
for line in f:
	line = line.rstrip('\n' +'\r' + "'")
	x=[line]
	print(x[0])
f.close()
```
That prints out the above input file.

However, if i change it to print(x[1]) i get an error saying that it doesn't exist which means my array is rather useless.

Am i importing the input file to the array wrong?

```

for line in open("log.txt"):
    line = line.strip()
    print line[0]

```

---

### Post by regomodo on 2008-04-03
`

---

### Post by ghostdog74 on 2008-04-03
> **regomodo said:**
> Thanks but i had tried that previously. It prints a "1" on each line
Cheers for the "open("log.txt"):" i forgot to use "open" and set "f" as the file instead

```
jon@debpad:~/python/testing$ python test
1
1
1
1
1
1
1
1
1
1
1
1
1
1
1
```
you got to split it

```

for line in open("file.txt"):
    line = line.strip().split(",")
    print line[0]

```

please go through Python documentation (see my sig) before posting.

---

### Post by regomodo on 2008-04-03
`

---

