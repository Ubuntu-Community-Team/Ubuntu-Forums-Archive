---
title: "CLI bash question"
date: 2010-05-25
forum: Programming Talk
---

### Post by AstroLlama on 2010-05-25
I've been trying to learn more about command line scripting, and i'm being put to the test now for a simple picture file resize and rename. this is what I have so far:

```
for i in 'ls'; do convert -resize 100x100 $i $i_th; done
```

This will take each item in ls and resize it to 100 px then append _th to the name. 

I'd also like to append consecutive numbers to the file names, any ideas on how to go about it?

---

### Post by BoneKracker on 2010-05-25
I haven't tested this.```
for file in $(ls); do
    convert -resize 100x100 "$file" "${file}_$((++i))"
done
```

---

### Post by geirha on 2010-05-25
```
i=0
for f in ./*.png; do 
  convert -resize 100x100 "$f" "${f%.png}_th$((i++)).png"
done
```

[http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030)
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by BoneKracker on 2010-05-25
I misunderstood "_th"; I thought that was a placeholder for the index number.  Nicely done.

Okay, now make it work the subdirectories as well, renaming only writable image files, but not attempting to rename non-writable files, non-image files, or directories.

I think we'll be back to using find. :P

---

### Post by geirha on 2010-05-25
Not necessarily. Bash 4 (Ubuntu 9.10 and newer ships bash 4) has globstar.

```
shopt -s globstar
for f in ./**/*.png; do ...

```

---

### Post by BoneKracker on 2010-05-25
> **geirha said:**
> Not necessarily. Bash 4 (Ubuntu 9.10 and newer ships bash 4) has globstar.

```
shopt -s globstar
for f in ./**/*.png; do ...

```

That's a great feature, and I'm a believer in always preferring shell features and builtins if they can do the job.  But what about "...renaming only writable image files, but not attempting to rename non-writable files, non-image files, or directories."

I don't believe that expression prevents the renaming of directories, attempts to rename non-writable files, or images of types other than png.

---

### Post by geirha on 2010-05-26
> **BoneKracker said:**
> That's a great feature, and I'm a believer in always preferring shell features and builtins if they can do the job.  But what about "...renaming only writable image files, but not attempting to rename non-writable files, non-image files, or directories."


You can rename the file regardless of whether it is writable or not. It only depends on whether the directory containing the file is writable, and of course, in the case of convert, it needs to be readable. You'll just get an error message about such files though, and nothing will happen to them. The loop will continue to the next files.

non-image-files. If you have a file with a .png extension that is not a png image, does it matter?  convert will just error out on that one file, and the loop continues on to the next.

> **BoneKracker said:**
> 
I don't believe that expression prevents the renaming of directories, attempts to rename non-writable files, or images of types other than png.

If you have a directory with a .png extension, it will be matched too. But again, convert will just error out and the loop continues to the next one. Alternatively you can add a
```
[[ -f $f ]] || continue
``` at the start of the loop to skip non-regular files.

By my experience you usually have one type of image you'll want to do this with, but you can always add more extensions. extglob helps with that

```
shopt -s extglob globstar
i=0
for f in ./**/*.@(png|jpg|jpeg|gif); do
  [[ -f $f ]] || continue
  ext=${f##*.}
  convert ... "$f" "${f%.$ext}_th$((i++)).$ext"
done

```

---

### Post by BoneKracker on 2010-05-26
> **geirha said:**
> ```
shopt -s extglob globstar
i=0
for f in ./**/*.@(png|jpg|jpeg|gif); do
  [[ -f $f ]] || continue
  ext=${f##*.}
  convert ... "$f" "${f%.$ext}_th$((i++)).$ext"
done

```
I think we may have a final product! :)

No, no... wait.  It should not assume the files are in $PWD.  It should take the directory as an argument.

Btw: I'm glad you demonstrated extglob.  I have had bash-4 on several of my systems for quite a while now, but I've not really investigated many of the new features.

---

### Post by geirha on 2010-05-26
Actually, extglob has been around since bash2, globstar is pretty new though.

[http://mywiki.wooledge.org/BashFAQ/061](http://mywiki.wooledge.org/BashFAQ/061)
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

---

### Post by BoneKracker on 2010-05-26
Thanks for the tips.

---

