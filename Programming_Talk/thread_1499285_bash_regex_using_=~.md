---
title: "bash regex using =~"
date: 2010-06-01
forum: Programming Talk
---

### Post by pataphysician on 2010-06-01
I'm trying to write a shell script that will pull all of the tags from an xml file. I'm finding that my regular expressions are either too greedy or too lazy. A simple example. Pretend I want to pull all the text that exists between quotes:

```

line='"bob," she said, "i have had enough."'
regexa='\"([^"]+)\"'
regexb='\"(.*)\"'
[[ $line =~ $regexa ]] # or b
i=1
n=${#BASH_REMATCH[*]}
while [[ $i -lt $n ]]
do
    echo ${BASH_REMATCH[$i]}
    let i++
done

```

If i use regexa I only get 'bob,' returned. If I use regexb, I get everything between the first and last quote ('bob," she said, "i have had enough.') as one result. What expression can I use to get "bob," as one part, and, "i have had enough." as another? (Without the quotes.)

---

### Post by geirha on 2010-06-01
You don't need a regex for that, just read with " as field separator.
```

#!/bin/bash
line='"bob," she said, "i have had enough."'
IFS=\" read -r -a words <<< "$line"
n=${#words[@]}

for (( i = 1; i < n; i += 2 )); do
    echo "${words[i]}"
done

```

---

### Post by pataphysician on 2010-06-01
> **geirha said:**
> You don't need a regex for that, just read with " as field separator.
```

#!/bin/bash
line='"bob," she said, "i have had enough."'
IFS=\" read -r -a words <<< "$line"
n=${#words[@]}

for (( i = 1; i < n; i += 2 )); do
    echo "${words[i]}"
done

```

I'm going to have to read up on what all of that means, but for now, it works, so thanks!

Edit: Well, actually, that works in the silly example I gave, but what about in cases where the text I'm looking for isn't encased in the same character on both ends? e.g., if

line="<name>bob</name><age>31</age>"

and i want to parse out the words, "name," and "age?"

---

### Post by geirha on 2010-06-01
The bash manual explains everything of course, though it's very long so it may be a bit hard to find the right parts to read. I recommend reading [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) (it links to relevant parts of the manual as it goes along)

---

