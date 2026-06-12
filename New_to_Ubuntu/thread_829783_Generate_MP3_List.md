---
title: "Generate MP3 List"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-15
I want some way to scan ALL my music and generate an easy to read list (xml, html, or whatever). Is there such a program?

---

### Post by hyper_ch on 2008-06-15
a very simple way:
```

cd /path/to/music/base/directory
ls -R > ~/Desktop/music.txt

```

or use: -alR instead of -R

---

### Post by abhiroopb on 2008-06-15
thats perfect! Ubuntu/Linux ...sigh!

But is there anything which allows me to maybe expand and collapse lists? because now I have a list thats like 30000 lines!

---

### Post by hyper_ch on 2008-06-15
well, it is all buid up the same way...

./path/to/some/folder
CONTENTS

./path/to/some/other/folder
CONTENTS

....
....
....

You could parse it then and create an xml file with it

---

### Post by abhiroopb on 2008-06-15
Is there a howto anywhere to make an xml file?

---

### Post by hyper_ch on 2008-06-15
you have to parse the file and make it xml-conform

---

### Post by abhiroopb on 2008-06-15
How do I "parse" the file? and "xml-conform"? Thanks!

---

### Post by hyper_ch on 2008-06-15
[http://en.wikipedia.org/wiki/Parsing](http://en.wikipedia.org/wiki/Parsing)

---

