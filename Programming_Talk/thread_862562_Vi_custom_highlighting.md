---
title: "Vi custom highlighting"
date: 2008-07-17
forum: Programming Talk
---

### Post by DBQ on 2008-07-17
Hi everybody.  I was just wondering how to create my own highlighting files for vi the easy way.  Thank You all.

---

### Post by Kadrus on 2008-07-20
This isn't really hard,supposing you have the ~/.vim dir and that you have ftdetect dir inside it,create a .vim file which contains something like this
```
au BufNewFile,BufRead *.extension set filetype=language
```
I think it should work this way

---

