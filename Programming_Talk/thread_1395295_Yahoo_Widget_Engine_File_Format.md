---
title: "Yahoo Widget Engine File Format"
date: 2010-01-31
forum: Programming Talk
---

### Post by PCZahra on 2010-01-31
Download any Yahoo! Widget and open it in Okteta to try this out. I had a couple of hours to myself today and this is what I turned out.

```
"wdgt"
int32: 0 (space for "wdgt" to be int64?)
int64: unknown (version?)
int64: unknown (build number?)
int64: location of first file block
int64: -1 (value to indicate no previous file?)
int64: -1 (value to indicate no next file?)
int64: location of file locator block
int64: location of file names block
int64: the number 0
block = {
 int32: length of block
 int32: location of filename (-1 for file locator block, -2 for filename string)
 int32: X (length of content)
 int32: the number 1 (enable?)
 int64: location of previous file (-1 for no file, unknown for system blocks)
 int64: location of next file (-1 for no file, unknown for system blocks)
 byte[X]: content
}
{blocks for files}
block: file locator: content{
 int64: location of filename in names string
 int64: location of file
}
block: file names: content{
 string: names {<filename>\0}
}
signature{
 "ngis": (magicstring ("sign" backwards) or must == second "ngis" as int32)
 data
 int32: X (where first location of "ngis" = filesize-X)
 "ngis": (magicstring or must == first "ngis" as int32)
}
```

---

