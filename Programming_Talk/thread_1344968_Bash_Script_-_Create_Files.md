---
title: "Bash Script - Create Files"
date: 2009-12-03
forum: Programming Talk
---

### Post by GiantCrab on 2009-12-03
So I have a text file in the format of:

>filename
contents of file
>filename2
contents, etc.

I'd like to create multiple files with the filenames listed in the text file, the contents of which are below it. How would I do this?

---

### Post by falconindy on 2009-12-03
This'll do:

```
#!/bin/bash
sourcefile=/path/to/source

while read line; do
        [[ ${line:0:1} = ">" ]] && outFile=${line:1} || echo $line >> $outFile
done < $sourcefile
```

---

### Post by GiantCrab on 2009-12-03
Thanks for the help! I implemented the code, but it keeps spitting out: 

$outfile: ambiguous redirect

What exactly is wrong?

---

### Post by falconindy on 2009-12-03
Post your source file. If I had to guess, I'd say that the first line isn't formatted as ">Filename".

---

### Post by zman121 on 2009-12-03
Watch the case.   The script used camelCase, your error message indicates all lower-case.

---

### Post by GiantCrab on 2009-12-03
Whoops, I think it was the case. It works now. The only problem I have now is that the entries have spaces before and after the line that I'd like to retain, and this script gets rid of those spaces. Any way I could retain those spaces?

>testfile
   there are spaces before and after this
>testfile 2
 more spaces

---

### Post by falconindy on 2009-12-03
> **GiantCrab said:**
> Whoops, I think it was the case. It works now. The only problem I have now is that the entries have spaces before and after the line that I'd like to retain, and this script gets rid of those spaces. Any way I could retain those spaces?

>testfile
   there are spaces before and after this
>testfile 2
 more spaces

Leading and trailing whitespace, you say? Guess I could show off my noobish Python skills:
```
#!/usr/bin/env python

source = './sourceFile'

out = open(source) #filthy hack

for line in open(source).read().split('\n'):
        if line.startswith('>'):
                out.close()
                outFile = line[1:]
                out = open(outFile, 'w')
        else:
                out.write(line + '\n')
```
Change the source variable to point to your file and you're good to go.

---

### Post by GiantCrab on 2009-12-03
Thanks alot falcon, works dandy. I'll have to spend some time looking at a good python book.

---

### Post by ghostdog74 on 2009-12-04
here's your bash script
```

while read -r line
do
    case "$line" in
        ">"* ) 
            filename=${line#*>};;
        * ) 
            echo "$line" >> $filename ;;
    esac
done < "file"

```

---

