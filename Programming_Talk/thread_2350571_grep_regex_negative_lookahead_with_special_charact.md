---
title: "grep regex negative lookahead with special character"
date: 2017-01-25
forum: Programming Talk
---

### Post by alv-0500 on 2017-01-25
I'm trying to get all it's package dependencies, including recommends and suggests from ```
apt-cache depends
``` using grep.
When I run this code:
```
apt-cache depends gdebi | grep -Po '(?!Depends: \b)\b.+'
```
the colon after Depends doesn't match in that group.
why is this happen and how to get package dependencies name only?

Thank you

---

### Post by &amp;KyT$0P# on 2017-01-25
Here's the output from my system -
```
$ apt-cache depends gdebi
gdebi
  Depends: <python3:any>
    python3:i386
    python3
  Depends: gdebi-core
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-vte-2.90
  Depends: python3-gi
  Depends: gksu
  Depends: gnome-icon-theme
  Recommends: libgtk2-perl
  Recommends: shared-mime-info
    shared-mime-info:i386

```

Negative lookaheads are a tricky concept.  Let's go through your regex piece by piece.

First up -
```
(?!Depends: \b)
```
Since you started your regex with this, it means "match something that is not followed by [FONT=Courier New]Depends: \b[/FONT]".

Next, it looks for
```
\b.+
```
... which you already understand.

So, where is the first word boundary that occurs after something not followed by [FONT=Courier New]Depends: \b[/FONT]?

**Answer:** Immediately before the colon.

Does this explanation help?

> **alv-0500 said:**
> how to get package dependencies name only?
Sorry, I don't completely understand this part.  From my example output above, what is the desired result?

---

### Post by alv-0500 on 2017-01-25
thank you halogen2
the result i'm looking is like this:
```

<python3:any>
python3:i386
python3
gdebi-core
gir1.2-gtk-3.0
gir1.2-vte-2.91
python3-gi
gksu
gnome-icon-theme
libgtk2-perl
shared-mime-info
shared-mime-info:i386
lintian
```

but the reality I got this:
```
gdebi
Depends: <python3:any>
python3:i386
python3
: gdebi-core
: gir1.2-gtk-3.0
: gir1.2-vte-2.91
: python3-gi
: gksu
: gnome-icon-theme
Recommends: libgtk2-perl
Recommends: shared-mime-info
shared-mime-info:i386
Recommends: lintian

```

I tried use this regex from this [http://stackoverflow.com/questions/2107989/matching-all-words-except-one](http://stackoverflow.com/questions/2107989/matching-all-words-except-one), but the colon ":" bugs me.
I just want to remove "Depends:", "Recommends:", and "Suggests:" output by *apt-cache depends, *but when I use my regex, I only can remove "Depends", "Recommends", and "Suggests" without the colon ":". The colon is my problem here.
In this case I want remove the "Depends:" first. The rest "Recommends:" and "Suggests:" may be I can try it by myself.

---

### Post by papibe on 2017-01-25
Hi alv-0500.

I think **awk** help you with that:
```
apt-cache depends gdebi | awk '{if ($0 ~ /Depends:|Recommends:/) print $2; else print $1}'
```
or this one if you don't want the first line:
```
apt-cache depends gdebi | tail -n +2 | awk '{if ($0 ~ /Depends:|Recommends:/) print $2; else print $1}'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by alv-0500 on 2017-01-26
> **papibe said:**
> Hi alv-0500.

I think **awk** help you with that:
```
apt-cache depends gdebi | awk '{if ($0 ~ /Depends:|Recommends:/) print $2; else print $1}'
```
or this one if you don't want the first line:
```
apt-cache depends gdebi | tail -n +2 | awk '{if ($0 ~ /Depends:|Recommends:/) print $2; else print $1}'
```
Hope it helps. Let us know how it goes.
Regards.

Thank you papibe, it works.

---

