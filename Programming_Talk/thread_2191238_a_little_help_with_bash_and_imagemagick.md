---
title: "a little help with bash and imagemagick"
date: 2013-12-01
forum: Programming Talk
---

### Post by Stauricus on 2013-12-01
hello everybody
i'm trying to make a simple script to put many images into a single one.
i have about 1000 png files in a folder, named from 0 to 999 (0.png, 1.png, 2.png, [...]).
i want to put them all in a single image, with the 'montage' command from imagemagick. so, it seems that it would be like this:
```
montage 0.png 1.png 2.png 3.png [...] -background none -tile 100x -geometry +0+0 output.png
```

but i'd like to know if is there any better way than writing down the name of all numbers from 0 to 999. i haven't figured how to use a for loop to "create" all these arguments.
any ideas?

thanks in advance!

---

### Post by r-senior on 2013-12-01
Bash brace expansion?

```
montage {0..999}.png -background ...
```

[http://www.gnu.org/software/bash/manual/bashref.html#Brace-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Brace-Expansion)

---

### Post by Stauricus on 2013-12-01
oh, i didn't knew i could use it like that! thanks, that's perfect :)

---

