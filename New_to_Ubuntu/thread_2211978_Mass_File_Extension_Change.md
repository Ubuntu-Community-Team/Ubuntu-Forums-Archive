---
title: "Mass File Extension Change"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by matthew31 on 2014-03-18
Here's what I want to do: I want to change all of my .ogg music into .oga. These are the same type of file just with a different extension so no conversion is needed. I do have some random mp3 files mixed in to my music folder and I want to leave those untouched. How can I do this through the terminal?

---

### Post by qyot27 on 2014-03-18
With a for-loop:
```
for n in *.ogg ; do
mv "$n" "${n%.*}.oga"
done
```

${n%.*}.oga accomplishes this, by trimming off the .ogg extension (controlled by the for n in *.ogg line, exposed through "$n") and replacing it with .oga.

---

