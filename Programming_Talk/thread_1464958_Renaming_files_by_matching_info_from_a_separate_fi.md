---
title: "Renaming files by matching info from a separate file"
date: 2010-04-28
forum: Programming Talk
---

### Post by cyberblade3001 on 2010-04-28
Hi All,

I could use a bit of help with this as I'm at a loss. Hope this is the right place.

I have a number of files all named accordingly:

> 032210.mp3
032210.mp4
032210.flv
032310.mp3
032310.mp4
032310.flv
etc.I have a separate text file that is as follows:

> MON    032210    3629
TUE    032310    3658
WED    032410    3616
THU    032510    3651
FRI      032610    3675What I want to do is end up with:

> 032210-003629.mp3
032210-003629.mp4
032210-003629.flv
032310-003658.mp3
032310-003658.mp4
032310-003658.flv
etc.
I don't know how to do this, though I'm certain it can be done, and would rather learn how than do it all manually. If someone could just point me in the right direction or post the basics so that I could have a starting point I'd much appreciate it.

So far all I've managed to do is replace the ^M from the text file with \r so that cat works properly on it.

Thanks.

---

### Post by kaibob on 2010-04-29
I'm still learning, but I came up with the following shell script. I did some limited testing, and it does work properly.

```
#!/bin/bash

while read -r _ num1 num2 ; do
   array1[i++]=$num1
   array2[j++]=$num2
done < /home/kaibob/file

for file in * ; do
   for num in "${!array1[@]}" ; do
      if [[ "${file%.*}" -eq "${array1[num]}" ]] ; then
         cp "$file" "${array1[num]}-00${array2[num]}.${file##*.}"
      fi         
   done
done
```

---

### Post by mo.reina on 2010-04-29
python
```
#!/usr/bin/python

import os
import re


def get_file_name(path):
    filelist = []
    for f in os.listdir(path):
        f[:f.find('.')].isdigit() == True and filelist.append(f)
    return filelist
   
def get_second_column(text):
    identlist = {}
    f1 = open(text)
    for line in f1.readlines():
        key, value = line.split()[1:]
        identlist[key] = value
    return identlist
    
    
filelist = get_file_name('path_of_files_here')
ident = get_second_column('path_of_text_file_here')
for f in filelist:
    num = f[:f.find('.')]
    if num in ident:
        os.rename(f, num + '-' + ident[num] + f[f.rfind('.') + 0:])
```

it's inefficient, still learning python, but i had nothing to do and it seemed like a bit of fun.

any suggestions to improving the code are very welcome

---

### Post by slavik on 2010-04-29
if the external text file is name "file" then:

```
awk '{ printf "s/%d/%d-%06d/\n", $2, $2, $3 }' < file | while read regex; do rename "${regex}" *; done
```

or 

```
awk '{ printf "s/%d/%d-%06d/\n", $2, $2, $3 }' < file | xargs -t -n1 -i{} rename "{}" *
```

also,

```
man dos2unix
```

for all your \r/^M related conversions :)

---

