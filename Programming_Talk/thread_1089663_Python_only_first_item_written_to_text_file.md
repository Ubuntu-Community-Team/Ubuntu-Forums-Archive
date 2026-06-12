---
title: "Python: only first item written to text file"
date: 2009-03-07
forum: Programming Talk
---

### Post by blairm on 2009-03-07
Hi,

Have a script that downloads headlines from a website's rss feed; when it's run with output going to shell it work well, giving all the headlines, links and descriptions. But writing the output to a text file (alert.txt) only gives me the first headline, link and description, not the others.
Had a look at the open section of the python docs and couldn't see what I'm doing wrong, and a google search has left me none the wiser. Here's the code:

Cheers,

Blair

```
import urllib
import sys
import xml.dom.minidom

#The url of the feed
address = 'http://www.stuff.co.nz/rss/'

#Our actual xml document
document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    f = open('alerttest.txt',  'w')
    print>>f,  '''<a href="%s">%s</a> (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))
```

---

### Post by the_unforgiven on 2009-03-07
The way you're opening the file is causing it to be overwritten.
Just move the open() statement outside the loop (i.e. before the loop starts) and it should work fine.

---

### Post by blairm on 2009-03-07
Thanks Unforgiven,

Unfortunately didn't have much luck - tried moving the line 
```
f = open('alerttest.txt',  'w')
```
pretty much everywhere within the script, but I got absolutely no output to alert.text when I did.
Am I missing something else?

Blair

---

### Post by arsenic23 on 2009-03-07
This seems to work:
```
#! /usr/bin/env python

import urllib
import sys
import xml.dom.minidom

#The url of the feed
address = 'http://www.stuff.co.nz/rss/'

#Our actual xml document
f = open('alerttest.txt',  'w')

document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '''<a href="%s">%s</a> (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))

f.close()
```

---

### Post by the_unforgiven on 2009-03-07
> **arsenic23 said:**
> This seems to work:
```
#! /usr/bin/env python

import urllib
import sys
import xml.dom.minidom

#The url of the feed
address = 'http://www.stuff.co.nz/rss/'

#Our actual xml document
f = open('alerttest.txt',  'w')

document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '''<a href="%s">%s</a> (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))

f.close()
```
Aah... Exactly what I had done and it worked for me too :)
Sorry, I should've just posted the code; but, I tend to prefer giving just the hints so as to point the poster in the right direction for the solution.

---

### Post by jimi_hendrix on 2009-03-07
@the_unforgiven

i dub thee unforgiven...

couldnt resist song reference

---

### Post by arsenic23 on 2009-03-07
> **the_unforgiven said:**
> Aah... Exactly what I had done and it worked for me too :)
Sorry, I should've just posted the code; but, I tend to prefer giving just the hints so as to point the poster in the right direction for the solution.

I only posted that since he said he was still having trouble.

---

### Post by blairm on 2009-03-07
Many thanks to all of you - no idea how I missed that. 
Guess it's a pretty good sign that it's time to get some sleep (it's 7.30am here now, and I've been going about 9 hours).
Bloody frustrating, but think I'm hooked now.;)
Cheers,

Blair

---

### Post by Can+~ on 2009-03-07
> **arsenic23 said:**
> This seems to work:
```
f.close()
```

Ah, the gool ol' close problem. Buffer won't be written to disk until file is closed.

---

### Post by jimi_hendrix on 2009-03-07
> **Can+~ said:**
> Ah, the gool ol' close problem. Buffer won't be written to disk until file is closed.

or flushed

---

### Post by Greyed on 2009-03-08
> **Can+~ said:**
> Ah, the gool ol' close problem. Buffer won't be written to disk until file is closed.

Immaterial unless there's a really nasty error in the code.

```

{grey@igbuntu:~/code} vim ham
{grey@igbuntu:~/code} cat ham
f = open('spam','w')
f.write('boo!\n')
{grey@igbuntu:~/code} ls spam
ls: cannot access spam: No such file or directory
{grey@igbuntu:~/code} python ham
{grey@igbuntu:~/code} cat spam
boo!

```Python closes any open file handles at the end of its run.  So unless he was posting just a snippet of code which never exited, he should have had a file with all the elements in it provided the file was opened outside of the loop.

---

### Post by the_unforgiven on 2009-03-08
> **jimi_hendrix said:**
> @the_unforgiven

i dub thee unforgiven...

couldnt resist song reference
Yup, that's where it comes from :)

---

### Post by the_unforgiven on 2009-03-08
> **Greyed said:**
> Python closes any open file handles at the end of its run.  So unless he was posting just a snippet of code which never exited, he should have had a file with all the elements in it provided the file was opened outside of the loop.
It's not only python - instead, it's the OS that closes all the file descriptors upon closing of the program.

---

