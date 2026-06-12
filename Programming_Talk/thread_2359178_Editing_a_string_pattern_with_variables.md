---
title: "Editing a string pattern with variables"
date: 2017-04-21
forum: Programming Talk
---

### Post by raysa on 2017-04-21
I have a batch of some 2,500 files in a popular music notation format called abc, which is basically just ascii text that subsequently gets converted to printed music. The abc file creation (not by me) must have been faulty because it produced many errors that need correcting before the files can produce useful sheet music.

The errors are mostly consistent and I can batch-correct most of them with sed commands, but there is one recurring fault which is more complex and I'm hoping someone can suggest a solution - either via sed or some other route.

A musical triplet (eg three half-notes in the space of one whole note) is written in abc as (3 followed by the three notes, eg: (3GAB.  The faulty files have (2G(2A(2B for this triplet. 

Is it possible to look through the files for any examples of (2x(2y(2z and replace them with (3xyz ... the xyz being variables that might be different on each occurence? The triplet pattern can occur multiple times in a file but often with different notes. I'm not a programmer (rather a musician trying to make a load of tunes available to others), and maybe this is an unrealistic task, but it feels like the sort of thing a bit computer code could do.

Two very short sample abc files attached. The suffix would normally be .abc but changed here to .txt to upload them: 'abctunebad' has the fault (three occurrences), and 'abctunegood' is the same with the faults hand-corrected to how it should be.

Thanks for any help.

---

### Post by steeldriver on 2017-04-21
```

sed -E 's/\(2([A-G])\(2([A-G])\(2([A-G])/(3\1\2\3/Ig' abctunebad.txt > abctunesed.txt

$ diff -s abctunesed.txt abctunegood.txt
Files abctunesed.txt and abctunegood.txt are identical

```

The `I` (case-insensitive modifier) is a GNU sed extension - if you want to be more portable, remove it and replace the [A-G] character ranges by [A-Ga-g]

(I'm assuming the note range is just A-G)

---

### Post by raysa on 2017-04-21
Fantastic!  steeldriver, if you knew how many hours/days this will save you'd appreciate how delighted I am ... many thanks.
And by running this sed command with an -i at the front and *.abc at the end I do the whole directory batch at once ... just tried it with a directory of a dozen tunes and it did the lot.

---

### Post by raysa on 2017-04-25
This has been working brilliantly with a lot of files, but I've discovered that it doesn't work with some files. The difference is when the triplets contain accidentals (sharps, flats etc). The abc music format uses _ = or ^ before a note to produce the flat, natural or sharp symbols, and these weren't covered in your sed line's character range, steeldriver, because I forgot to mention them when you asked about the range.  So I thought I'd add them, thus:
```
sed -E 's/\(2([A-G_=^])\(2([A-G_=^])\(2([A-G_=^])/(3\1\2\3/Ig' abctest.abc > abctestout.abc
```
This works fine when the accidental is with the last of the three notes in the triplet, but oddly it fails if the accidental is with the first or second note.
For example this faulty abc file:
```
X:1
T:Test abc
M:1/4
L:1/8
K:C
(2B(2c(2^c|
(2c(2^c(2d|
(2^c(2c(2B|
```
is turned into:
```
X:1
T:Test abc
M:1/4
L:1/8
K:C
(3Bc^c|
(2c(2^c(2d|
(2^c(2c(2B|
```
Only the first faulty triplet is corrected - the one with the sharp on the third note. The correction fails when the sharp is with the first or second note.

Any thoughts on how to tackle this? 
Thanks.

---

### Post by steeldriver on 2017-04-25
If I'm reading the format correctly, you want to *prepend *each [A-G] range with an *optional* (i.e. zero or one instances of) accidental (underscore, equals, or caret [_=^] )

```

[_^]?[A-G]

```

(Note that you must place the underscore first since caret will be treated as a negation if you write [^_])

So

```

sed -E 's/\(2([_=^]?[A-G])\(2([_=^]?[A-G])\(2([_=^]?[A-G])/(3\1\2\3/Ig' abctunebad.txt

```

EDIT: if you need to handle double-sharps / double-flats, change the ? to * (or, more pedantically, {0,2})

---

### Post by raysa on 2017-04-26
Many thanks again, steeldriver ... works a treat!
Useful addition, too, about double-sharps and double-flats, although I'll keep this for reference ... the music I deal with hardly ever has these.

---

