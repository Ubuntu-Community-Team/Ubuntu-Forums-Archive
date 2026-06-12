---
title: "How can I filter a saved file filename from a link? [shellscript]"
date: 2011-01-23
forum: Programming Talk
---

### Post by kittkatt on 2011-01-23
Hello, I'm trying to make a simple script which downloads a linked media file, then immediately plays it on mplayer.  These are mostly for the podcasts I subscribe to.

> #!/bin/sh

wget -O temp #1
mplayer temp


Instead of temp, I want to be able to preserve the original intended filename.  So [www.podcast.com/hello.mp3](www.podcast.com/hello.mp3) > hello.mp3

I think its some sort of sed/awk type filtering or something, but I'm not sure. Any of you know?

Thanks,

Kitt

---

### Post by Vaphell on 2011-01-23
```

file="a.com/stuff/hello.mp3"
fileshort=${file##*/}
echo $file "=>" $fileshort

```

${VARIABLE##*/}
VARIABLE - variable to cut text from
## - ignore stuff matching the pattern, starting from the left (single # would be non-greedy, ## is greedy and it tries to match as much as it can, there are also % and %% that do similar thing at the end of the string)
*/ - pattern to throw away - in this case any sequence ended with /

#*/ a/**b/c**
##*/ a/b/**c**
%/* **a/b**/c
%%/* **a**/b/c
bolded is the returned value, the rest of the string is thrown away

---

### Post by kittkatt on 2011-01-23
Sweet! Solved it, thanks!

Here's the script

> #!/bin/sh

echo $1
fileTarget=$1
fileshort=${fileTarget##*/}
echo $fileTarget "=>" $fileshort

wget -O $fileshort $fileTarget
mplayer $fileshort

---

