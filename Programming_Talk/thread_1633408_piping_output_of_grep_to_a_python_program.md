---
title: "piping output of grep to a python program"
date: 2010-11-29
forum: Programming Talk
---

### Post by debsankha on 2010-11-29
I am facing this queer problem with input redirection to a python program:

I want to redirect the output of this command to a python program:
```

rsync -r --progress source_dir/ dest_dir/ | grep -E -o "to-check=[0-9]+/[0-9]+" | ./percent.py

```
The output is generally something like this:
```

to-check=315/317
to-check=314/317
to-check=313/317
....

```
The python program is supposed to convert the x/y ratios to percentages, which I want to pipe to a zenity command in order to show a progressbar.

But the problem is that the python program is not spewing out the outputs until grep has finished, therefore ruining the whole functionality of the progressbar. My python code is:
```

#!/usr/bin/python
#percent.py

import re
s=raw_input()
while s.strip()!='':
        nums=re.findall("([0-9]+)/([0-9]+)",s)[0]
        print (float(nums[1])-float(nums[0]))*100/float(nums[1])
        try:
                s=raw_input()
        except:
                exit()  


```
Can somebody please help?

---

### Post by Arndt on 2010-11-29
> **debsankha said:**
> I am facing this queer problem with input redirection to a python program:

I want to redirect the output of this command to a python program:
```

rsync -r --progress source_dir/ dest_dir/ | grep -E -o "to-check=[0-9]+/[0-9]+" | ./percent.py

```
The output is generally something like this:
```

to-check=315/317
to-check=314/317
to-check=313/317
....

```
The python program is supposed to convert the x/y ratios to percentages, which I want to pipe to a zenity command in order to show a progressbar.

But the problem is that the python program is not spewing out the outputs until grep has finished, therefore ruining the whole functionality of the progressbar. My python code is:
```

#!/usr/bin/python
#percent.py

import re
s=raw_input()
while s.strip()!='':
        nums=re.findall("([0-9]+)/([0-9]+)",s)[0]
        print (float(nums[1])-float(nums[0]))*100/float(nums[1])
        try:
                s=raw_input()
        except:
                exit()  


```
Can somebody please help?

This page may be useful: [http://algorithmicallyrandom.blogspot.com/2009/10/python-tips-and-tricks-flushing-stdout.html](http://algorithmicallyrandom.blogspot.com/2009/10/python-tips-and-tricks-flushing-stdout.html).

---

### Post by debsankha on 2010-11-29
Thanks for your reply. I tried the method mentioned there, i.e.:
```

s=raw_input()
sys.stdin = os.fdopen(sys.stdin.fileno(), 'r', 0)

```
But now I'm getting only the first line of the output from grep.

---

### Post by Arndt on 2010-11-29
> **debsankha said:**
> Thanks for your reply. I tried the method mentioned there, i.e.:
```

s=raw_input()
sys.stdin = os.fdopen(sys.stdin.fileno(), 'r', 0)

```
But now I'm getting only the first line of the output from grep.

That page had stdout, not stdin. Did you try stdout?

If that doesn't work, just doing a flush after each print ought to work.

---

### Post by debsankha on 2010-11-29
Well, the problem has been solved. It was happening because grep doesn't produce line buffered output by default. Fortunately it can be told to do so by adding --line-buffered flag. The correct command is:
```

rsync -r --progress src/ dest/ | grep --line-buffered -E -o "to-check=([0-9]+)/([0-9]+)" | ./percent.py | zenity --progress --auto-close --percentage=0

```

BTW, I had to add sys.stdout.flush() after each print statements in percent.py for the progressbar to work. Thanks Arndt!:D

---

