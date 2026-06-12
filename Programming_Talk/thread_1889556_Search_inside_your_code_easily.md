---
title: "Search inside your code easily"
date: 2011-12-01
forum: Programming Talk
---

### Post by hakermania on 2011-12-01
I know that this is *very* simple, but I was now thinking about how much this simple script has helped me on searching my code for specific words:
```
#!/bin/bash
for i in *; do
   if ! [ -d "$i" ]; then
      if [[ $(cat "$i" | grep "$1") ]]; then
         echo "$i"
      fi
   fi
done
```It searches all the files in the current directory and outputs the ones containing the 1st argument, example usage:
```

alex@MaD-pc:~/Documents/WALLCH$ for_every image
create_html
direct_link
imageshack.py
imgur.py
log.txt
screenshots.html
start
alex@MaD-pc:~/Documents/WALLCH$ all the above files contain the word "image"

```Just sharing....

---

### Post by MadCow108 on 2011-12-01
ever heard of grep -r?

for code searching I'd rather recommend tag based approaches like ctags or cscope

---

### Post by hakermania on 2011-12-02
> **MadCow108 said:**
> ever heard of grep -r?

for code searching I'd rather recommend tag based approaches like ctags or cscope

I never have my code in separate directories, so I don't use this :P

---

### Post by ofnuts on 2011-12-02
> **hakermania said:**
> I never have my code in separate directories, so I don't use this :P
You must be writing small programs. :)

---

