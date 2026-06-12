---
title: "Simple Bash problem"
date: 2006-08-29
forum: Programming Talk
---

### Post by Roque on 2006-08-29
Hello. 

I wrote a small Bash script that downloads a file from a given place and saves it under certain folder. Currently a new downloaded file overwrites the older (because both have the same name); instead I want files to be named incrementally in order to keep a record, eg:
file_1.xml
file_2.xml
file_3.xml
...

I cannot use an internal counter variable because the script could be run several times a day. It should find the largest numbered file under the folder, (eg. file_345.xml) and increment that number to create a new file name (eg. file_346.xml)

How can I do this in Bash? Thanks in advance.

---

### Post by nagilum on 2006-08-30
A simple loop will do the trick, something like this:
```

cnt=1
while [ -f "file_${cnt}.xml" ]; do
    cnt=$(($cnt+1))
done

```
When the loop is finished $cnt contains the next unused number in your filename pattern, e.g. 4 in your example. Note that a "gap" in your file numbers will yield this gap and not the highest number + 1.

---

### Post by yaaarrrgg on 2006-08-30
also, you might count the matching files, perhaps like:

```

#backticks execute a shell command, pipe ls output into wc
cnt=`ls file_*.xml | wc -l`

```

---

### Post by Roque on 2006-09-01
Ok, problem solved. Thanks!

---

### Post by ifokkema on 2006-09-01
Both these suggestions fail, as mentioned, if there's a gap in the file sequence. What about running ls, sorting on modification time, taking the top hit and using grep to fetch the number...?

---

### Post by JonahRowley on 2006-09-02
You could do it like this:

```

$ ls
file_1.xml  file_2.xml  file_3.xml  file_7.xml  max_num.sh

$ cat max_num.sh
#!/bin/bash

max=0
for f in file_*.xml; do
  t=${f##*_}
  t=${t%%.*}
  if [ $t > $max ]; then max="$t"; fi
done
(( max += 1 ))

echo "file_$max.xml"

$ ./max_num.sh
file_8.xml

```

Handles gaps and stuff.  Doesn't rely on sorting which, with unpadded strings, might not be correct.

---

### Post by ifokkema on 2006-09-02
Cool. I've seen you spit out code in 7 languages or so in some other thread to solve a problem. You really know your languages. Did you specifically try to learn as many different languages as possible, or are you just programming for so long that you happen to run in to these languages after time because of all the different project that you did?

---

### Post by JonahRowley on 2006-09-02
> **ifokkema said:**
> Cool. I've seen you spit out code in 7 languages or so in some other thread to solve a problem. You really know your languages. Did you specifically try to learn as many different languages as possible, or are you just programming for so long that you happen to run in to these languages after time because of all the different project that you did?

I've been coding since before I could read (no, really, I would copy the programs out of my Commodore 64 instruction booklet and change them around), so I can pick up languages very quickly.  I like learning new ones to see what they're really like, and not what people say they're like, so I have at least a working knowledge of most the popular languages around.

A few years ago, I picked up this rather obscure language from Japan.  I was going to learn smalltalk, but I learned this newer, supposedly better language called Ruby.  Then Rails came along and my favorite language is now very useful, and tons of cool code is being written in it every day :P

---

