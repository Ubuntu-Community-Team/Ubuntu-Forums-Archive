---
title: "Regular expressions: Extract several items from a line of text"
date: 2014-01-23
forum: Programming Talk
---

### Post by texpat on 2014-01-23
Hi there,

this is probably trivial to most of you, but I just can't wrap my brain around this.

I have a line of text that reads.
```
Image Size   : 800x600
```

I want to extract the 800 and the 600 using Perl regular expressions (which I admittedly have little clue of).

```
$line =~ /\:\s*(.*)x/;
```

nicely gets me the first bit in $1, but I'm having trouble getting the second part into $2.

I'm thankful for any pointers.
Tx

---

### Post by steeldriver on 2014-01-23
How about using lookahead / lookbehind to find sequences of digits before and after the x character?

```

$ echo 'Image Size   : 800x600' | perl -ne 'print "$1\n" if /(\d+)(?=x)/'
800

$ echo 'Image Size   : 800x600' | perl -ne 'print "$1\n" if /(?<=x)(\d+)/'
600

```

- see [http://www.regular-expressions.info/lookaround.html](http://www.regular-expressions.info/lookaround.html) for a tutorial

---

### Post by tgalati4 on 2014-01-23
If this is EXIF data from a camera file, then there are several tools to extract the resolution:

Open a terminal:

```
apt-cache search exif
```

*exif* and *metacam* are a couple.

---

### Post by ofnuts on 2014-01-23
Use "\d" to specify you want digits

```

$line=~/:\s*(\d+)x(\d+)/;

```
or even
```

$line=~/(\d+)x(\d+)/;

```

---

### Post by texpat on 2014-01-23
Thanks to all of you who read and contributed.

@ofnuts: that was exactly what I was after. Cheers a million. Your solution is simple and elegant, but for some reason it eluded me.

---

### Post by ofnuts on 2014-01-24
Fairly basic stuff though :)

---

### Post by texpat on 2014-01-28
@ofnuts: yeah, i *knew* it had to be, but my skills in this area are very limited. And regular expressions, however trivial they may be, give me the shivers every time ;-)

Thanks to the likes of you and many others on these forums I learn bit by bit.

---

### Post by ofnuts on 2014-01-28
Like many people around here I owe everything I know about regexps to [this book]("http://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124/"). Purchase || Borrow || Steal(*) || Put on your Xmas list...

The copy I read was found abandoned in a cupboard when moving offices, together with "Clapton Unplugged". It was a great day :)

---

### Post by kurum! on 2014-01-30
Just use split on ":" and get the 2nd item. Simple, and doesn't take days to solve

---

