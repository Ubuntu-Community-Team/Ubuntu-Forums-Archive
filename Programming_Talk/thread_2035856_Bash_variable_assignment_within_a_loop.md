---
title: "Bash variable assignment within a loop"
date: 2012-07-31
forum: Programming Talk
---

### Post by cheruvim on 2012-07-31
> **chenel said:**
> Wow.  I can't believe I didn't think of that either.

Well, at least I'm not alone. :)

Good work, volanin.

I'm trying to do the same on bash on a macosx (ok I should go elsewhere, I know) but.. Mac forums are so... unhelpful..

in trying to tar up a bunch of files in directories with spaces I have the following:
```

export FILESTRING=''; 
find All\ 90x135/ All\ 62x75/  -name *.jpg -mtime -4 | \
while read dafile; 
  do export FILESTRING="$FILESTRING \"$dafile\""; 
done; 
tar czvf ~/minors.`date +%Y%m%d`.tgz $FILESTRING

```

However tar complains about an empty file list because although while FILESTRING is being modified in the while loop, it doesn't export it out.

I checked the output of the find command. There is nothing there to indicate that the find output would corrupt the variable and even so, the variable is being preserved from iteration to iteration which is why I think there is a bug in the bash on mac.. but.. unlikely.

---

### Post by Vaphell on 2012-07-31
how about not piping find to while, but using it directly to fuel the loop

```
files=()  # array
while read f; do files+=( "$f" ); done < <( find "All 90x135" "All 62x75" -name *.jpg -mtime -4 ) 

tar czvf ~/minors.$(date +%Y%m%d).tgz "${files[@]}"
```

---

### Post by trent.josephsen on 2012-07-31
```
find All\ 90x135/ All\ 62x75/  -name *.jpg -mtime -4 | \
tar -czvf ~/minors.$(date +%Y%m%d).tgz -T-
```

The -T option tells tar to take the filelist from a file, and - represents standard input. No loop necessary.

---

### Post by sisco311 on 2012-07-31
Please don't bump old threads. The old thread can be found here: [http://ubuntuforums.org/showthread.php?t=708438](http://ubuntuforums.org/showthread.php?t=708438)

---

### Post by sisco311 on 2012-07-31
@OP: Check out BashFAQ 020 and 024 (link in my signature).

Because of the pipeline the while loop runs in a sub-shell. ;)

I'd probably use BSD/find's -exec option:
```
find ... -exec tar ... {} +
``` 

Vaphell's and trent.josephsen code will do the trick in 99% of the cases. :evil: But, not if the files have newlines or other whitespace in their names.

```

unset files index
while read -r -d '' file
do
    files[index++]="$file"
done < find ... -print0
```

```
find ... -print0 | tar ... --null -T -
```

---

### Post by trent.josephsen on 2012-07-31
It will work with other whitespace, just not newlines.

---

