---
title: "Is there a way to use html2text for a directory with subfolders?"
date: 2010-03-30
forum: Programming Talk
---

### Post by bradley002 on 2010-03-30
Last time I used html2text for a directory I used ls >> filename.txt to obtain a list, and then used that list in a loop to convert all of the files using html2text. However, I am looking at a directory now that has about 100 subfolders. When looking through "ls" options I found one thing that let you list contents of subdirectories, but it didn't format them in a way that would be easily used with a simple loop. So in response to "ls -(something) ./Documents", it was like:

purple.txt
friend.txt
joe.txt
./folder2:
bread.txt
mouse.txt
pinch.txt
./folder3:
beard.txt


Where folder2, folder3, etc. are subdirectories. So because the full path of each file is not listed on each line, I don't know how I would specifiy them with the html2text command. Any ideas for converting all of those subdirectories filled with html to text? Thanks.

---

### Post by geirha on 2010-03-31
With bash4 (echo $BASH_VERSION):
```
#!/bin/bash
shopt -s globstar

for f in ./**/*.html; do
  html2text "$f" -o "${f%.*}.txt"
done

```

Otherwise you can use find
```
find . -type f -name "*.html" -exec sh -c 'for f; do html2text "$f" -o "${f%.*}.txt"' _ {} +
```

See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073) and [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by bradley002 on 2010-04-03
Oh cool, I didn't think I got any replies to this. Thanks; I haven't tried it yet, but now  I know what to do.

---

