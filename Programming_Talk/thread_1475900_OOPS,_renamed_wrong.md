---
title: "OOPS, renamed wrong"
date: 2010-05-07
forum: Programming Talk
---

### Post by dannyboy79 on 2010-05-07
Hi everyone. I had a bunch of .mpg I converted with ffmpeg (with batch command for file in do; ;done. well they ended up being filename.mpg.mp4. I didn't want that so I was looking for a slution to batch rename them. I couldn't find anything to strip the .mpg out of the filename (i am sure there is something just not smart enough with programming syntax) so I used rename
rename 's/\.mp4$//' *.mp4
then the filenames just ended in .mpg. OOPS, I didn't want that so then I did
rename 's/\.mpg$//' *.mpg
DOUBLE OOPS!!! now my filename have no extension. How in teh world do I ADD an extension to all files within my current directory? Please help. The common thing in the filename with all files is this string
It's Always Sunny in Philadelphia
YES, there are spaces in the filename, that's how they came from mythtv and mythrename. Any help would be appreciated.

While anyone is answering that, I do still have more files named this:
Sons of Anarchy - 2009-09-08, 9-00 PM - Albification.mp4
that I would love to remove the ", 9-00 PM " from teh filename so they end up like this:
Sons of Anarchy - 2009-09-08 - Albification.mp4

again, any help with programming syntax or regex would be great.!

---

### Post by lavinog on 2010-05-07
This would have worked in the first case:
```

IFS='
'
for f in *.mpg.mp4;do mv -v "$f" "${f%.mpg.mp4}.mp4" ;done
unset IFS

```

Since you have no extentions:
```

IFS='
'
for f in *;do mv -v "$f" "${f}.mp4" ;done
unset IFS

```

---

### Post by dannyboy79 on 2010-05-07
> **lavinog said:**
> This would have worked in the first case:
```

IFS='
'
for f in *.mpg.mp4;do mv -v "$f" "${f%.mpg.mp4}.mp4" ;done
unset IFS

```

Since you have no extentions:
```

IFS='
'
for f in *;do mv -v "$f" "${f}.mp4" ;done
unset IFS

```
thanks but i am curious as to what the IFS stuff is? i ran this
```
for f in *;do mv -v "$f" "${f}.mp4" ;done
```
on the command line and it worked a treat!!!!! is the IFS stuff for a bash script?

also, can you answer the question about removing a portion of teh name out of the Sons of Anarchy filenames?

---

### Post by lavinog on 2010-05-07
> **dannyboy79 said:**
> thanks but i am curious as to what the IFS stuff is? i ran this
```
for f in *;do mv -v "$f" "${f}.mp4" ;done
```
on the command line and it worked a treat!!!!! is the IFS stuff for a bash script?

also, can you answer the question about removing a portion of teh name out of the Sons of Anarchy filenames?

The IFS variable tells the for command how to delimit the filenames
By default uses space and newline...but if the filenames have spaces in them, it could cause a problem...so setting IFS to only be a newline can fix that issue.
It probably worked without it because your filenames didn't have spaces in them.

removing the time is more difficult.
a regular expression might be the solution, but I am not good with them myself.
The way I would go about it is to split the name by the comma, the split the second part by the dash.

here is a python script:
```

#! /usr/bin/env python

import os

'''
Sons of Anarchy - 2009-09-08, 9-00 PM - Albification.mp4
that I would love to remove the ", 9-00 PM " from teh filename so they end up like this:
Sons of Anarchy - 2009-09-08 - Albification.mp4
'''


def newname(string):
    part1, part2 = string.split(',')
    part2_parts = part2.split('-')[2:]
    part2 = '-'.join(part2_parts)
    string = '-'.join((part1,part2))
    return string
    

for file in listdir('./'):
    if file.endswith('.mp4'):
        try:
            newfilename = newname(file)
        except:
            print 'Could not rename %s' %file
            continue
        
        os.rename(file,newfilename)


```

copy the code into a file
then execute the code by typing
python scriptname

it will only work in the current folder.
I also have not tested it since I don't have a bunch of file to test it with...so I would copy all your files to another location just in case.

---

