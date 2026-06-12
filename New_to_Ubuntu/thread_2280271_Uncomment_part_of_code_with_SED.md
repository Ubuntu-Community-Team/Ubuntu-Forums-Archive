---
title: "Uncomment part of code with SED"
date: 2015-05-29
forum: New to Ubuntu
---

### Post by CrewDK on 2015-05-29
Well, I hope I can ask this question here. 

I have some text file with many commented and uncommented "sections". I need UNcomment one section with "sed". 
Now i have something like this 

```
sed -i '/# regexp/,/^#fi/ s/^#//g' ./filename.ext
```

Well, this UNcommenting all, that I need. But it also uncommenting 1st line (lets name it "sectio'n name"). 
I mean after run my command i have something like this:
```
 section's name
if .................. ; then
bla-bla-bla...
fi
```

And now I can't understand how can I uncomment all "section" but without 1st line (section's name). Something like this: 
```
# section's name
if .................. ; then
bla-bla-bla...
fi
```

Can somebody help me?

---

### Post by SeijiSensei on 2015-05-29
I don't see any way to do that either unless you edit the file and use "##" at the beginning of each section's name.

---

### Post by steeldriver on 2015-05-29
I can't think of an easy way either: you could maybe do *kind of* what you want with

```

sed '/# *regex*/ { :a; $!N; s/\n#/\n/; ta; }' filename.txt

```

Note: it stops the first time it fails to substitute [FONT=courier new]^#[/FONT], rather than up to and including [FONT=courier new]^#fi[/FONT] specifically

---

### Post by CrewDK on 2015-05-29
> **SeijiSensei said:**
> I don't see any way to do that either unless  you edit the file and use "##" at the beginning of each section's  name.

Well, this way I already found by myself. I just hoped that I missed something in sed. :)

> **steeldriver said:**
> I can't think of an easy way either: you could maybe do *kind of* what you want with

```

sed '/# *regex*/ { :a; $!N; s/\n#/\n/; ta; }' filename.txt

```

Note: it stops the first time it fails to substitute [FONT=courier new]^#[/FONT], rather than up to and including [FONT=courier new]^#fi[/FONT] specifically

Thanx. I'll try this too.

---

