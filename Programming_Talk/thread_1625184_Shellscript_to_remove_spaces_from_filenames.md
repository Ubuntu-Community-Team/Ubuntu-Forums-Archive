---
title: "Shellscript to remove spaces from filenames"
date: 2010-11-18
forum: Programming Talk
---

### Post by thenickdude on 2010-11-18
Hi everyone,

I've ended up with ~100,000 files with a space at the end of their filename that I need to remove (e.g. "192111 "). I did a "ls -1" in that directory and piped it to a file, so I have a list of all the files, some of which need to be renamed.

Probably the best way of doing this would be a bash script, but I'm a bash beginner. Can anyone help me out?

EDIT: I think I have this complete now :)

```
grep -P "^[^ ]+ $" /vol/myfilelist | while read file
do
if [ -f $file ]; then
     echo "${file} already exists?"
else
     mv "${file} " $file
     echo "'${file} ' move to ${file}"
fi
done

```

---

### Post by ziekfiguur on 2010-11-19
I have a python script that i use to automatically remove spaces from filenames, I mostly use it for my music library (I still haven't found cd ripping software that gives uses filenames). It recursively goes through al underlying folders, so it could be a bit dangerous to use it somewhere else, but it works for me. I hope it can be of use for someone here.

```
#!/usr/bin/env python
import os
import re

def rename(path):
    for file in os.listdir(path):
        fname = os.path.join(path, file)
        if os.path.isdir(fname):
            rename(fname)
        renamefile(path, file)

def renamefile(path, file):
    newname = re.sub('[^a-zA-Z0-9._-]+', '_', file)
    newname = re.sub('_-_', '-', newname)
    newname = re.sub('[_-]{2,}', '_', newname)
    newname = re.sub('[_-]+$', '', newname)
    newname = re.sub('^[_-]+', '', newname)
    if newname != file:
        #print os.path.join(path, file), os.path.join(path, newname)
        os.rename(os.path.join(path, file), os.path.join(path, newname))


if __name__ == '__main__':
    rename('.')


```

BTW, it also remover all special characters except underscore `_', dash `-' and dot `.', replaces all repetitions of underscores and dashes by one underscore and removes underscores and dashes from the beginning and end of the filenames.

---

### Post by daniel227 on 2011-11-23
thanx to ziekfiguur!
this did the trick for my music collection. personally i'm not so good with scripts so i'm glad i found it ready-made.
just one thing, mayb you'd like to add that for the future:
the script *removes* weird characters - in some case it would be better to replace them, for example the ä (that is an a with 2 dots) would be better to replace with an a, instead of removing it.
for me it has happened already and i can't bring them back anymore, and it's not a big thing - except mayb if i had all Ärzte-albums and they were all changed to rzte... but i have only 1.
:twisted:
especially the recursive bit is good.
maybe you could answer a related question? i want to remove all m3u playlists from my music folders, i thought ```
rm -r *.m3u
``` would do it, but it seems that the recursiveness (-r) doesn't work???

asks daniel

---

### Post by Lampi on 2011-11-23
using find is one way:
```
find Music/ -type f -name "*.m3u" -exec rm -v {} \;
```
... will browse Music/ and it's subfolders and remove files ending with m3u

if you want a conformation dialog before you delete the file use rm -v[COLOR="Red"]i[/COLOR] {} instead

---

### Post by ziekfiguur on 2011-11-23
The problem with special characters is that there are a LOT of them, and i couldn't (and still can't) be bothered to make all of them work.

But, as per your request, here is a slightly improved version of the script:
```
#!/usr/bin/env python3

import os
import re

def rename(path):
    for file in os.listdir(path):
        fname = os.path.join(path, file)
        if os.path.isdir(fname):
            rename(fname)
        renamefile(path, file)

def make_newname(name):
    newname = re.sub('[äáàâ]', 'a', name)
    newname = re.sub('[ÄÁÀÂ]', 'A', name)
    newname = re.sub('ç', 'c', newname)
    newname = re.sub('Ç', 'C', newname)
    newname = re.sub('[ëéèê]', 'e', newname)
    newname = re.sub('[ËÉÈÊ]', 'E', newname)
    newname = re.sub('[ïíìî]', 'i', newname)
    newname = re.sub('[ÏÍÌÎ]', 'I', newname)
    newname = re.sub('[öóòôø]', 'o', newname)
    newname = re.sub('[ÖÓÒÔØ]', 'O', newname)
    newname = re.sub('[üúùû&#365;]', 'u', newname)
    newname = re.sub('[ÜÚÙÛ&#364;]', 'U', newname)
    newname = re.sub('[ÿý&#7923;&#375;]', 'y', newname)
    newname = re.sub('[&#376;Ý&#7922;&#374;]', 'Y', newname)
    newname = re.sub('æ', 'ae', newname)
    newname = re.sub('Æ', 'AE', newname)
    newname = re.sub('[^a-zA-Z0-9._-]+', '_', newname)
    newname = re.sub('_-_', '-', newname)
    newname = re.sub('[_-]{2,}', '_', newname)
    newname = re.sub('[_-]+$', '', newname)
    newname = re.sub('^[_-]+', '', newname)
    return newname

def renamefile(path, file):
    newname = make_newname(file)
    if newname != file:
        print('{0:s} --> {1:s}\n'.format(os.path.join(path, file), os.path.join(path, newname)))
        os.rename(os.path.join(path, file), os.path.join(path, newname))


if __name__ == '__main__':
    rename('.')

```

Note that this version uses python3, you'll have to install it if you don't have it yet. The reason for that is that python3 has a much better way of handling unicode characters than python2.
You can see i didn't add all possible special characters, but i think i got the most used ones. Anyway the pattern should be clear so you can add more yourself if you need to.

---

### Post by crdlb on 2011-11-23
> **ziekfiguur said:**
> The problem with special characters is that there are a LOT of them, and i couldn't (and still can't) be bothered to make all of them work.

But, as per your request, here is a slightly improved version of the script:
Another way to do most of that is:```

unicodedata.normalize('NFKD', s).encode('ASCII', 'ignore').decode()

```
That will split and strip most diacritical marks. Of your set, it only seems to fail with 'ø' and 'æ', so those would need to be done beforehand.

---

### Post by daniel227 on 2011-11-23
thanx lampi, that worked!
i wonder why it's so complicated. i don't really understand why rm -r isn't enough...
miraculous linux.

and thanks to ziekfiguur!
that looks like a nice script, i will treasure it. as i said, after running your first script there's no more special characters left to replace, but i will remember it!

d.

---

### Post by crdlb on 2011-11-23
> **daniel227 said:**
> i wonder why it's so complicated. i don't really understand why rm -r isn't enough...


The '*.m3u' is expanded by the shell, so rm only receives a list of files matching that glob (i.e. files in the current directory ending in .m3u).

'rm -r' allows rm to remove entire directories instead of just files, so it doesn't do anything in this case.

---

### Post by daniel227 on 2011-11-28
thanks to all.
i'm putting a bookmark on this. good to learn some shell scripting.

---

### Post by mucho_maze on 2012-07-06
> **ziekfiguur said:**
> I have a python script that i use to automatically remove spaces from filenames, I mostly use it for my music library (I still haven't found cd ripping software that gives uses filenames). It recursively goes through al underlying folders, so it could be a bit dangerous to use it somewhere else, but it works for me. I hope it can be of use for someone here.

```
#!/usr/bin/env python
import os
import re

def rename(path):
    for file in os.listdir(path):
        fname = os.path.join(path, file)
        if os.path.isdir(fname):
            rename(fname)
        renamefile(path, file)

def renamefile(path, file):
    newname = re.sub('[^a-zA-Z0-9._-]+', '_', file)
    newname = re.sub('_-_', '-', newname)
    newname = re.sub('[_-]{2,}', '_', newname)
    newname = re.sub('[_-]+$', '', newname)
    newname = re.sub('^[_-]+', '', newname)
    if newname != file:
        #print os.path.join(path, file), os.path.join(path, newname)
        os.rename(os.path.join(path, file), os.path.join(path, newname))


if __name__ == '__main__':
    rename('.')


```

BTW, it also remover all special characters except underscore `_', dash `-' and dot `.', replaces all repetitions of underscores and dashes by one underscore and removes underscores and dashes from the beginning and end of the filenames.

Thank you very much for this helpful script!

---

### Post by ziekfiguur on 2012-07-08
> **mucho_maze said:**
> Thank you very much for this helpful script!

Thank you.
Here is the latest version of the script, including crdlb's solution for special characters and now also removing trailing underscores at the end of the filename, before the extension.
```
#!/usr/bin/env python3

import os
import re
import unicodedata

def rename(path):
    for file in os.listdir(path):
        fname = os.path.join(path, file)
        if os.path.isdir(fname):
            rename(fname)
        renamefile(path, file)

def remove_accents(s):
    return unicodedata.normalize('NFKD', s).encode('ASCII', 'ignore').decode()

def make_newname(name):
    newname = name.replace('ø', 'o')
    newname = newname.replace('Ø', 'O')
    nawname = newname.replace('æ', 'ae')
    nawname = newname.replace('Æ', 'AE')
    newname = remove_accents(newname)
    newname = re.sub('[^a-zA-Z0-9._-]+', '_', newname)
    newname = re.sub('_-_', '-', newname)
    newname = re.sub('[_-]{2,}', '_', newname)
    newname = re.sub(r'[_-]+(\.[a-zA-Z0-9]+)?$', r'\1', newname)
    newname = re.sub('^[_-]+', '', newname)
    return newname

def renamefile(path, file):
    newname = make_newname(file)
    if newname != file:
        print('{0:s} --> {1:s}\n'.format(os.path.join(path, file), os.path.join(path, newname)))
        os.rename(os.path.join(path, file), os.path.join(path, newname))


if __name__ == '__main__':
    rename('.')

```

Edit: And a version that works with older versions of python
```
#!/usr/bin/env python
#encoding: utf-8
import os
import re
import unicodedata

def rename(path):
    for file in os.listdir(path):
        fname = os.path.join(path, file)
        if os.path.isdir(fname):
            rename(fname)
        renamefile(path, file)

def remove_accents(s):
    return unicodedata.normalize('NFKD', s).encode('ASCII', 'ignore').decode()

def make_newname(name):
    newname = unicode(name).replace(u'ø', 'o')
    newname = newname.replace(u'Ø', 'O')
    nawname = newname.replace(u'æ', 'ae')
    nawname = newname.replace(u'Æ', 'AE')
    newname = remove_accents(newname)
    newname = re.sub('[^a-zA-Z0-9._-]+', '_', newname)
    newname = re.sub('_-_', '-', newname)
    newname = re.sub('[_-]{2,}', '_', newname)
    newname = re.sub(r'[_-]+(\.[a-zA-Z0-9]+)?$', r'\1', newname)
    newname = re.sub('^[_-]+', '', newname)
    return newname

def renamefile(path, file):
    newname = make_newname(file)
    if newname != file:
        #print '{0:s} --> {1:s}\n'.format(os.path.join(path, file), os.path.join(path, newname))
        os.rename(os.path.join(path, file), os.path.join(path, newname))


if __name__ == '__main__':
    rename('.')

```

---

