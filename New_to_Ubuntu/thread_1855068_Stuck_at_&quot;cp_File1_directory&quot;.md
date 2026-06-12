---
title: "Stuck at &quot;cp File1 directory&quot;"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by drofart on 2011-10-05
```
kitten@mistress-s-kitten:/media/9450402750401302/document/EBOOKS$ cp palm*.pdf viirus
cp: target `viirus' is not a directory
kitten@mistress-s-kitten:/media/9450402750401302/document/EBOOKS$ cp palm*.pdf msc
cp: target `msc' is not a directory
kitten@mistress-s-kitten:/media/9450402750401302/document/EBOOKS$ cp palm*.pdf misc
cp: target `misc' is not a directory
kitten@mistress-s-kitten:/media/9450402750401302/document/EBOOKS$ cp palm*.pdf /misc
cp: target `/misc' is not a directory
kitten@mistress-s-kitten:/media/9450402750401302/document/EBOOKS$ 
```


[B]I want a lil help here. Any one plz help me out ! where is the problem?
[/B]

---

### Post by nothingspecial on 2011-10-05
The attachment is difficult to read but it doesn't look like thr subdirectories you are trying to move your files into exist.

---

### Post by nothingspecial on 2011-10-05
From what I can tell your viirus directory is 2 levels up in the tree, so

```
cp palm*.pdf ../../viirus
```

---

### Post by drofart on 2011-10-05
> **nothingspecial said:**
> The attachment is difficult to read but it doesn't look like thr subdirectories you are trying to move your files into exist.
thank u dear for reply . I m not sure how cp command act on which directory i hav to put command at destination dir. or source dir. or from root i thought from root i can't plz tell me where i shoud i give cp command . & if i can only cp my files to a sub dir.  ?

---

### Post by nothingspecial on 2011-10-05
Try the command above

---

### Post by drofart on 2011-10-05
> **nothingspecial said:**
> From what I can tell your viirus directory is 2 levels up in the tree, so

```
cp palm*.pdf ../../viirus
```
Thank u i got it a lil. would u plz tellme where can i ger more described documentation abt it?

---

### Post by nothingspecial on 2011-10-05
Well it's not the cp command so much as bash and the directory structure. 

Try

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by drofart on 2011-10-05
> **nothingspecial said:**
> Try the command above
Thank u again it works .ok if "../" is for up the tree what for down the tree? please this last one.

---

### Post by nothingspecial on 2011-10-05
It's not as simple as that because there can be only one parent directory but many child directories.

---

### Post by drofart on 2011-10-05
> **nothingspecial said:**
> Well it's not the cp command so much as bash and the directory structure. 

Try

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
thank u for ur help  & valuable time.

---

### Post by drofart on 2011-10-05
> **nothingspecial said:**
> It's not as simple as that because there can be only one parent directory but many child directories.
ya i m now on "learning shell" by William Shotts , Just tring to migrate to linux.

---

