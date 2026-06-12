---
title: "Maximum number of arguments in CSH"
date: 2006-07-03
forum: Programming Talk
---

### Post by Chua-Chua on 2006-07-03
Hello,

What is the maximum number of items in CSH lists before the "Too many arguments" is invoked?

I am trying to copy all of my MP3 files from a library to a folder, but i keep getting the "Too many arguments" error.

I have about 490 MP3 files in the folder i want to copy from.


here is a sample script...I am just trying to print out the filenames.

#!/bin/csh

set file = `find . -name "*.mp3"`

echo $file

---

### Post by scxtt on 2006-07-03
i think your problem is the fact that you're trying to set a (non array) variable to something that will contain multiple values (i.e. an entry for each of your 490 mp3s) ... why not have find do the move also? -- no script necessary ...
[indent]find . -name "*.mp3" -exec mv {} /home/chua-chua/mp3s \;[/indent]

---

