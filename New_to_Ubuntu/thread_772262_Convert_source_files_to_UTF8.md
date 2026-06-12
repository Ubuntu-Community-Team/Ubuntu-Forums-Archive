---
title: "Convert source files to UTF8"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by teHIngo on 2008-04-28
Hi everybody!

I am experiencing some problems with text files, such as LaTeX source files. Since I migrated from Windows to Ubuntu, all the files have an encoding that does not correctly work with Kile. It compiles the source files to PDF nevertheless, but gibes me a lot of errors about different characters and it does not really look good to have question marks all over your document! Plus, in the output file, a lot of characters are missing, for instance in this word: "Mrzrevolution (1848)" which should acutally also contain an "Ä".

**Long story, short question:**
*How can I convert files with the Windows encoding to UTF-8?*

Thanks :-)
Ingo

---

### Post by hyper_ch on 2008-04-28
have a look at:  iconv

But not sure if that works for the files you want to have.

---

### Post by Hospadar on 2008-04-28
Depending on how many files you have (i.e. if you have relatively few) you could probably just open them in kate or gedit and do a "save as"

If you have a lot though, and want to automate it on the command line, iconv is probably the choice.

---

### Post by teHIngo on 2008-04-28
It worked, thank you :-)

---

