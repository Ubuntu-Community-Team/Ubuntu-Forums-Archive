---
title: "Bash script file renaming (very basic question)"
date: 2009-09-09
forum: Programming Talk
---

### Post by tgeer43 on 2009-09-09
I guess they don't get any more basic than this.
I have a group of mp3's that I need to rename as part of a general conversion script. The file names are of the format:

07.This Song.mp3
6.That Song.mp3
136.Another Song.mp3

All I want to do is strip the leading digits and period so that they come out like this:

This Song.mp3
That Song.mp3
Another Song.mp3

I'd like the operation to overwrite the old file name rather than create a new file and have to delete the old one, if possible.
I've experimented with 'mv', 'rename', 'sed', and even 'awk' but can't seem to get the syntax right.
Would someone care to help a newcomer to bash scripting?

Thanks in advance,

tgeer

---

### Post by unutbu on 2009-09-09
```
rename 's/^\d+\.//' *.mp3
```
In the above command:
"s" tells rename to do a substitution
s/PATTERN/REPLACEMENT/ is the general form of the command
^\d+\. is the regexp PATTERN
nothing is the REPLACEMENT.

In the regexp pattern:
^ means match starting at the beginning of the filename
\d+ means match one-or-more digits [0-9]
\. means match a period

---

### Post by soltanis on 2009-09-09
```

ls -1 | perl -ne 'if (m/\d+\.(.*\.mp3)/) { print "$_ $1"; }' | xargs -n 2 mv

```

Untested, give it a whirl on a test directory.

---

### Post by tgeer43 on 2009-09-09
Unutbu,
Not surprisingly your code works perfectly. And it's nice and concise, too - exactly what I was after. I especially appreciate the detailed explanation.
Give a man an answer and you help him for a day. Explain how you derived it and you help him for a lifetime. Many thanks.

---

Soltanis,
With a sample file named '01.Test Song.mp3', your code produced:
```
tgeer@tgeer:~/Temp$ ls -1 | perl -ne 'if (m/\d+\.(.*\.mp3)/) { print "$_ $1"; }' | xargs -n 2 mv
mv: cannot stat `01.Test': No such file or directory
mv: cannot stat `Test': No such file or directory
```I'm sure it just needs a bit of tweaking. Thanks for your effort.

Anyway, unutbu has got me right where I want to be.

Thanks to both of you,

tgeer

---

