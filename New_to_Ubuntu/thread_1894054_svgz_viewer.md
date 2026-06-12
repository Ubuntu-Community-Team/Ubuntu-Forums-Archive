---
title: "svgz viewer"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by arzali on 2011-12-11
Hi there,
is there a way to view svgz files in ubuntu?
Im using Ubuntu 10.10 and tried some image viewers like eog gthumb feh etc. and not one can open it.
the only way for now is to open them with inkscape but it takes too long to load one file.

---

### Post by mutley89 on 2011-12-11
They are supposed to be gzipped svg files which most image viewers should open without issue.  Could you try:
```
display image.svgz
```or
```
zcat image.svgz | display
```If that fails what is the output of:
```
file image.svgz
```

---

### Post by llamabr on 2011-12-11
Or you could just un gzip it.

try feh.  very lightweight, reasonably configurable, and opens mine fine.

---

### Post by arzali on 2011-12-12
> **mutley89 said:**
> They are supposed to be gzipped svg files which most image viewers should open without issue.  Could you try:
```
display image.svgz
```or
```
zcat image.svgz | display
```If that fails what is the output of:
```
file image.svgz
```

that works but i still cant open it with eog or other viewers

```
$ file arrows.svgz 
arrows.svgz: gzip compressed data, from FAT filesystem (MS-DOS, OS/2, NT)
```> **llamabr said:**
> Or you could just un gzip it.

try feh.  very lightweight, reasonably configurable, and opens mine fine.

yes but thats uncomfortable with many files.

---

### Post by Lars Noodén on 2011-12-12
You should be able to open compressed SVG (.svgz) using Inkscape.

---

