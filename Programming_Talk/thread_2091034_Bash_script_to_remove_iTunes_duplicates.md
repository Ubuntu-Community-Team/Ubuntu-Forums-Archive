---
title: "Bash script to remove iTunes duplicates"
date: 2012-12-04
forum: Programming Talk
---

### Post by ianhaycox on 2012-12-04
Hi,

I'm trying to remove duplicate MP3 files from a iTunes library of around 15,000 tracks with about 10,000 duplicates.

The duplicates all have the suffix ' 1.mp3', e.g.

Music/artist/album/tracka.mp3

but there also exists

Music/artist/album/tracka 1.mp3

I'd like to remove all the files with the suffix ' 1.mp3' iff the file without the ' 1' suffix exists in the same directory.

I've tried various combinations of find, sed, xargs etc. but my bash knowledge/syntax is limited.

E.g.

```
$ find Music -type f -name '* 1.mp3' | xargs -0 sed 's: 1.mp3:.mp3:' -exec [ -f ?? ] echo rm ?

```

I know the above find command is nonsense, but maybe it shows what I'm trying to do.

Any help really appreciated.

---

### Post by Vaphell on 2012-12-04
try this
```
while IFS= read -rd $'\0' f
do
  [ -f "${f% 1.mp3}.mp3" ] && echo rm "$f"
done < <( find Music -iname '* 1.mp3' -type f -print0 )
```

---

### Post by ianhaycox on 2012-12-04
Thank you. Works perfectly.

I never knew about f%

---

