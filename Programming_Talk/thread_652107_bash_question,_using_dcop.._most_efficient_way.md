---
title: "bash question, using dcop.. most efficient way?"
date: 2007-12-28
forum: Programming Talk
---

### Post by PetePete on 2007-12-28
```

image x=22 y=5 w=155 h=153 sensor=program program="convert -format PNG -resize 155x153! `dcop amarok player coverImage` /tmp/img.png|echo /tmp/img.png" interval=10000

```

the above is an extract from a superkaramba theme which shows the cd artwork.. 
The theme is all well and fine, but its set to do the following every 10seconds which can eat up alot of unnecessary CPU time by resizing the image every time even if it has not changed.

What im trying to develop is a way to get the image from dcop, then compare the two files (if they are same byte size seems good enough) and if they differ then resize and do cpu intensive activities. .. 

I think this would require 3 files 
file 1 (img.png) is the current (resized) in use file
file 2 img-orig.png being an unresized version of the current artwork
file 3 img-10-seconds.png being the file taken from dcop every 10 seconds which then is compared against file2 

can anyone think of a more efficient way for this to be implemented?

---

### Post by .nedberg on 2007-12-28
Why not just check if
```
`dcop amarok player coverImage`
```
returns the same sting as earlier?

```

OLD=`cat somfile`
NOW=`dcop amarok player coverImage`
IF [ ! $OLD = $NOW ]; then
    do stuff with image
    echo $NOW > somefile
FI


```

You get the idea...

---

