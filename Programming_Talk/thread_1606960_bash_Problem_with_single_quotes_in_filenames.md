---
title: "bash: Problem with single quotes in filenames"
date: 2010-10-27
forum: Programming Talk
---

### Post by KIAaze on 2010-10-27
Hi,

I've been using the following alias for quite some time without problems now:
```
alias ducks='find . -maxdepth 1 -mindepth 1 -print0  | xargs -0 -n1 du -ks | sort -rn | head -16 | cut -f2 | xargs -i du -hs {}'

```
(based on an alias by [ayoli]("http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/"))

It lists the 16 biggest directories and files in the directory it is run from. Sizes are shown in human readable format.

However, it breaks on filenames with single quotes like "foo'bar" saying:
```
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option

```

How could I fix it?
If possible, I'd like to avoid having to write a bash or python script to replace the alias.

---

### Post by slavik on 2010-10-27
try passing the filename through:
```
sed 's/\'/\\\'/'
```

---

### Post by KIAaze on 2010-10-27
This works:
```
find . -maxdepth 1 -mindepth 1 -print0  | xargs -0 -n1 du -ks | sort -rn | head -16 | cut -f2 | sed "s/'/\\\'/" | xargs -i du -hs {}

```
But I can't set the alias because of the single quotes.

---

### Post by DaithiF on 2010-10-27
why not replace the '\n's with null characters using tr, then you're back to using xargs with -0:

```
alias ducks='find . -maxdepth 1 -mindepth 1 -print0  | xargs -0 -n1 du -ks | sort -rn | head -16 | cut -f2 | tr "\n" "\0" | xargs -0 du -hs'
```

---

### Post by KIAaze on 2010-10-27
Thanks, that works. :)

---

