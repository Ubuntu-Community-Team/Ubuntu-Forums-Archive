---
title: "[SOLVED] request help w/ bash command and  dash (-)"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by m9ke on 2008-05-26
Hello all,

I have about 4K files, many of which contain <space>-<space> in the file name.  For example:
Alive - The very best of

I have done some searching and found a number of scripts and shell commands that will replace spaces with underscores. If I run those on the above file I get:
Alive_-_The_very_best_of

What I want to end up with is:
Alive_The_very_best_of

Just changing the spaces to underscores is not a problem-I am stuck in how to deal with the dash (-)

I am trying unsuccessfully to modify the following shell command which I found in this forum and which works fine for substituting underscores for spaces.  I haven't been able to get it to work with the dash (-) character.

```
IFS='
'
j=`find $1 -printf "%d\n" | sort -u | tail -n 1` 
echo "Max dir depth:" $j
for (( i=0; i<=j ; i++ ))
do
  for name in `find -mindepth $i -maxdepth $i -iname "* *" -printf "%p\n"`
  do
    newname=`echo "$name" | tr " " "_"`
    echo "$name" "$newname"
    mv "$name" "$newname"
  done
done
```

The only change I have made so far is to line 9:

I changed

```
newname=`echo "$name" | tr " " "_"`
```
to 
```
newname=`echo "$name" | tr " - " "_"`]
```

The command appears to run without errors, but there are no changes made.  

Any thoughts?

Thanks,
m9ke

---

### Post by Monicker on 2008-05-26
I haven't really used tr before, but how about

```
newname=`echo "$name" | sed 's/ - /_/g'`
```

---

### Post by jpeddicord on 2008-05-26
If I'm reading this right, you just want to get rid of a dash in filenames? Then you're making this too difficult. Let rename solve all of your problems:

```
rename 's/\-//' *
```

That will remove all of the dashes. If you want to replace them with an underscore:

```
rename 's/\-/_/' *
```

Want to do it in all subdirectories?

```
find -name "*.mp3" | xargs rename 's/\-/_/' *
```Replace the *.mp3 with whatever mask you want to use.

---

### Post by m9ke on 2008-05-26
Thank you Monicker and jacobmp92.

I substituted the line Monicker suggested for the ninth line in the command I had posted, and tested it.  

The result was that it replaced <space> - <space> with one underscore, recursively.  Success!

Also thanks jacobmp92 for your suggestion to simplify!

Thanks very much for your help!

m9ke

---

