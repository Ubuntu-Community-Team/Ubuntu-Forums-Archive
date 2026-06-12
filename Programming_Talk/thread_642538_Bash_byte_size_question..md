---
title: "Bash byte size question."
date: 2007-12-16
forum: Programming Talk
---

### Post by natehall on 2007-12-16
using Bash I want to input the names of a bunch of files and output the file names sorted by the size of each file. (with the size shown) How would I do that?

---

### Post by geraldm on 2007-12-16
read manpage for ls.  It is easiest to use all files in a directory ".", but you could also use the names of each file.
```

ls -S .

```

Gerald

---

### Post by natehall on 2007-12-17
I thought of that one but when I use it in a pipe it still outputs the usual information on the directories. not the files that I wanted to be fed to it by a  pipe. (I'm trying to list my gif files in order of size to catch the ones with the same size. Those I'm going to check with an image viewer so I can edit out the duplicates.) I'm having a similar problem with the stat command.

---

### Post by tomchuk on 2007-12-17
You could use md5sums like so:
```
find . -iname '*.gif' | xargs md5sum | sort
```

Or a little python script to do find dupes:
```

#!/usr/bin/env python

import os, md5

files = dict()

for file in os.listdir('.'):
  f = open(file, 'r')
  chksum = md5.new(f.read()).hexdigest()
  f.close()
  if chksum not in files:
    files[chksum] = [file]
  else:
    files[chksum].append(file)

for chksum in files:
  if len(files[chksum]) > 1:
    print 'Same files: ', ' '.join(files[chksum])

```

---

### Post by natehall on 2007-12-18
Thanks for the info! Just what is md5sum? I notice that its hex. Is it the first chunk of a binary file?

---

### Post by tomchuk on 2007-12-18
> **natehall said:**
> Thanks for the info! Just what is md5sum? I notice that its hex. Is it the first chunk of a binary file?

It's a cryptographic hash of the contents of the file. It uses the entire contents of the file to create a hash that uniquely identifies that file. md5sums are often used to verify that downloaded files. If you take a look at the [Ubuntu Download Directory](http://cdimage.ubuntu.com/releases/7.10/release/) you'll see an MD5SUMS file that contains the md5sums for the CD images so that you can verify that it was downloaded correctly.

---

### Post by natehall on 2007-12-18
> **tomchuk said:**
> It's a cryptographic hash of the contents of the file. It uses the entire contents of the file to create a hash that uniquely identifies that file. md5sums are often used to verify that downloaded files. If you take a look at the [Ubuntu Download Directory](http://cdimage.ubuntu.com/releases/7.10/release/) you'll see an MD5SUMS file that contains the md5sums for the CD images so that you can verify that it was downloaded correctly. You answered two questions that time. I've seen those before and had no idea. How could Bash make a two column array out of my sort? ( That's the next lesson I've given myself)

---

### Post by tomchuk on 2007-12-18
awk is great at dealing with columnar data. If you take the above piece of shell script and pipe it to awk, you can treat the columns individually. eg:
```
find . -iname '*.gif' | xargs md5sum | sort | awk '{print $1 " - " $2}'
```
the $1 represents the first column, and $2 the second.

As far as bash arrays go -- that's usually where I draw the line with shell scripts and move to a more robust language like python or perl. The [Advanced Bash Scripting Guide chapter on arrays](http://tldp.org/LDP/abs/html/arrays.html) (and the [rest of it](http://tldp.org/LDP/abs/html/)) will answer most of your questions on bash arrays and other Bash topics.

---

