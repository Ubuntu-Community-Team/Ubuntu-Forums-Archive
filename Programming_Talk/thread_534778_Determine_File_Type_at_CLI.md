---
title: "Determine File Type at CLI"
date: 2007-08-25
forum: Programming Talk
---

### Post by DagMan on 2007-08-25
How would I go about determining the type of file something is at the command line the way nautilus is able to display it as, for example, an image, a video, a music file, a document, etc.

For example if I wanted to move all music files from folder1 to folder2, what tool would I use to determine which files were the music files if I didnt initially use file extentions to keep track of it?

---

### Post by jordanmthomas on 2007-08-25
use the command file:
```
file filename
```
example:
```
[jordan@ttyfscker ~]$ file test.jpg
test.jpg: JPEG image data, JFIF standard 1.01

```

```
[jordan@ttyfscker 8stops7]$ file Fate 
Fate: Audio file with ID3 version 24.0 tag, MP3 encoding

```

---

### Post by DagMan on 2007-08-25
Thanks for that.  It was much easier than I expected.

---

