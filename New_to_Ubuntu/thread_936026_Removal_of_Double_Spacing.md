---
title: "Removal of Double Spacing"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by jchappel on 2008-10-02
I currently have a file that is double spaced and I need to remove the double spacing and was wondering if there is a way to do this on the UNIX file system.  

I believe I'm looking for a way to either remove the CRLF mark or some other way to remove the extra line in the file.

Thanks in advance...

---

### Post by Therion on 2008-10-02
What kind of file is it?

---

### Post by jchappel on 2008-10-02
It is a straight .txt file.

---

### Post by Therion on 2008-10-02
I would think AbiWord or Writer (from Open Office) would be able to open the file and then, you'd select the contents (Ctrl+A) and reset the spacing to whatever you want, like single space or double space.

---

### Post by Bachstelze on 2008-10-02
*EDIT: I'm not sure I understand what you mean here. Define "double-spaced", please.*

Command-line :

```
sed -i.backup 's/  / /g' foo.txt
```

Will do the replacements, and save a copy of the original file as foo.txt.backup, in case something goes wrong:

```
firas@iori ~ % cat foo
foo  bar baz
foo bar  baz
firas@iori ~ % sed -i.backup 's/  / /g' foo
firas@iori ~ % cat foo
foo bar baz
foo bar baz
firas@iori ~ % cat foo.backup
foo  bar baz
foo bar  baz

```

---

### Post by Therion on 2008-10-03
> **HymnToLife said:**
> I'm not sure I understand what you mean here. Define "double-spaced", please.
**Single Spaced:**

Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Quisque aliquet quam. Vivamus nec lorem interdum velit facilisis hendrerit. Nulla ut tellus. Aenean vulputate mattis tellus. Integer tempus velit. Etiam non odio et enim sollicitudin accumsan. Duis dignissim ante eu nibh. Aenean lectus. In id nibh vel justo tristique pretium.

[B]
Double Spaced:[/B]

Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Quisque 

aliquet quam. Vivamus nec lorem interdum velit facilisis hendrerit. 

Nulla ut tellus. Aenean vulputate mattis tellus. Integer tempus 

velit. Etiam non odio et enim sollicitudin accumsan. Duis dignissim 

ante eu nibh. Aenean lectus. In id nibh vel justo tristique pretium.

---

