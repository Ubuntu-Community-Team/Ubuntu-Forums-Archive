---
title: "ebook-convert xargs error"
date: 2011-01-21
forum: Programming Talk
---

### Post by TheOneBlackMage on 2011-01-21
I'm trying to convert all of the ebooks in a directory from PDF to MOBI to work on my Kindle3 using ebook-convert.  I think I've got the find statement working properly, as it outputs the list of filenames with the .pdf extension dropped off, then I would normally call:

```
ebook-convert "file.pdf" "file.mobi"
```

I've tried this:

```
find . -name '*.pdf' -exec basename \{\} .pdf \; | xargs -0 -I ebook-convert "{}.pdf" "{}.mobi"
```

What I think is happening is it is passing the entire list to xargs as one filename, calling ebook-convert and then segfaulting.  I need it to do conversion one filename at a time.  I tried calling a shell via xargs, but I couldn't get that to work either.

I'm working off some of the examples in [THIS](http://ubuntuforums.org/showthread.php?t=1436654) thread, but I can't figure out what I'm doing wrong.  I'd appreciate a little help :)

---

### Post by TheOneBlackMage on 2011-01-21
Got it (I think).  Waiting to see how the conversion process goes.

-edit- Nope... still trying.

---

### Post by TheOneBlackMage on 2011-01-21
Gave up on a one-liner and tried writing a bash script:

```

#!/bin/bash

DIR="./"
SUFFIX="pdf"

for i in "$DIR"/*.$SUFFIX
do
   INPUTFILE=`echo $i | sed 's#^.*/##'`
   OUTPUTFILE=`echo ${i%%.$SUFFIX} |sed 's#^.*/##'`.mobi
   ebook-convert \"$INPUTFILE\" \"$OUTPUTFILE\"
done

```

This gives me the proper syntax for each ebook-convert command (tested with echo), but I start getting these errors:

```

Cannot read from /home/user/eBookConvert/"Lastname,
Segmentation fault
Cannot read from /home/user/eBookConvert/"Lastname,
Segmentation fault
Cannot read from /home/user/eBookConvert/"Lastname,
Segmentation fault
Cannot read from /home/user/eBookConvert/"Lastname,

```

So the filenames have spaces in them, and apparently the ebook-convert has a problem with this.  I don't get it, because when I run this manually on one ebook, with the spaces, it works.  I enclosed the input and output files in "quotations" so I'm not sure what the difference is.

---

### Post by gmargo on 2011-01-21
I think it's the way you quoted the ebook-convert line.  Plus you seem to be doing too much substitution.  This seems to work for me:

```

#!/bin/sh

DIR="."
SUFFIX="pdf"

for i in "$DIR"/*.$SUFFIX
do
        out=${i%.$SUFFIX}.mobi
        ebook-convert "$i" "$out"
done

```

Here's a shell function called 'printargs'.  Use this instead of echo to determine if your arguments are correct.  That's how I tested the above.
```

printargs()
{
        #echo "$0"
        echo "arguments: $#"
        while test $# -gt 0
        do
                echo "$1"
                shift
        done
}

```

---

### Post by TheOneBlackMage on 2011-01-21
Thanks, that worked great!  I think it was that I was using \" to make the quotation literal.  I'll look into the difference for my own understanding.

I created a simplified script using the proper quotations that seems to work as well:

```

#!/bin/bash

for filename in *.pdf
do
  ebook-convert "$filename" "${filename%.pdf}.mobi"
done

```

---

