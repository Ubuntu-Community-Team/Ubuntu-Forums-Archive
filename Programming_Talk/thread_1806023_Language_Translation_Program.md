---
title: "Language Translation Program"
date: 2011-07-17
forum: Programming Talk
---

### Post by GarlicBread on 2011-07-17
Hello!

I'm working on a piece of literature that, while vastly different in plot and theme, is much like *A Clockwork Orange* in the sense that it takes place in the future, and is filled with contrived slang (a "ring" for a telephone, a "mallie" for a transvestite prostitute, etc).

While I am compiling a document of words and meanings, I feel it would be easier if I had a program where I could enter "mallie" and have "transvestite prostitute" come up - needing this, of course, for the ease of keeping track of the accurate usage of fictional slang.

Now, I'm ENTIRELY and COMPLETELY illiterate when it comes to even basic programming, is there any way I could moderately easily program a translator - one that I could continue to add to - that I could use? (Maybe modify one that's open source that may exist, changing/adding my own language to it)  This would make it far easier, I feel.  I use Xubuntu 11.04 if that makes any difference.

Thanks!

---

### Post by ziekfiguur on 2011-07-17
if you have a dictionary file like this:
```
ring - telephone
mallie - transvestite prostitute
...
```
so, word[space][dash][space]translation with one word per line
you can use this program:
[PHP]#!/usr/bin/env python

import sys
import os.path
from optparse import OptionParser

def rundict(dictfile):
    if not os.path.exists(dictfile):
        print 'Error, dictionary file not found'
        return
    words = dict([l.split(' - ')
                  for l in open(dictfile, 'r').readlines()
                  if l.strip() != ''])
    while True:
        print '>',
        line = sys.stdin.readline()
        if len(line) == 0:
            break
        line = line.strip()
        if line not in words:
            print 'Error, word not in dictionary'
            continue
        print '=>', words[line].strip()

def main():
    parser = OptionParser()
    parser.add_option('-d', '--dictionary', dest='dict',
            help='use FILE as dictionary',
            metavar='FILE', default='dictionary')
    options, args = parser.parse_args(sys.argv)
    rundict(options.dict)

if __name__ == '__main__':
    main()

[/PHP]
you have to run it from the terminal, by default it searches for a file called dictionary but with the -d option you can use another file.

---

### Post by nvteighen on 2011-07-17
> **GarlicBread said:**
> Hello!

I'm working on a piece of literature that, while vastly different in plot and theme, is much like *A Clockwork Orange* in the sense that it takes place in the future, and is filled with contrived slang (a "ring" for a telephone, a "mallie" for a transvestite prostitute, etc).

While I am compiling a document of words and meanings, I feel it would be easier if I had a program where I could enter "mallie" and have "transvestite prostitute" come up - needing this, of course, for the ease of keeping track of the accurate usage of fictional slang.

Now, I'm ENTIRELY and COMPLETELY illiterate when it comes to even basic programming, is there any way I could moderately easily program a translator - one that I could continue to add to - that I could use? (Maybe modify one that's open source that may exist, changing/adding my own language to it)  This would make it far easier, I feel.  I use Xubuntu 11.04 if that makes any difference.

Thanks!

Uh... I don't want to run into a "mallie"... :P

Ok, here enters the resident linguist. Mind that ziekfiguur's solution would only work if your slang doesn't imply any morphological deviation from standard English and if you also explicitly add each morphological form's equivalency in English. Otherwise, "mallies" (which I'd suspect is the plural) wouldn't be replaced into "transvestite prostitutes". There are ways to make a program aware of plurals and even inflection, but that's much harder and will always have some limitations. 

The limitations are basically Linguistics' "fault", not Computer Science's. Our theoretical understanding about how the morphological component interacts with syntax is still scarce.

---

### Post by GarlicBread on 2011-07-17
I apologize for the ignorance, but I'm not sure what to do with the PHP Code or where to place the txt file I create.

---

