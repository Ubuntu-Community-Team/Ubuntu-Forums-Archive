---
title: "Disappearance of File: * at end of filename"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by AmagicalFishy on 2014-05-23
So, I had several files with different extensions:

cone.py
cone.exo
coen.root

etc.

I wanted to rename all of these cone_analysis instead of just cone. I (erroniously) typed "mv cone* cone_analysis*" into the terminal---and now the cone.py file is gone.

Do any of you folks know where I'd be able to find it, what my command did, exactly, and how I could go about renaming files correctly?

---

### Post by lukeiamyourfather on 2014-05-23
The file is gone. What happened is the first file was renamed and then the second file was renamed to the same thing (overwriting the first file). Hopefully there was a backup of the file.

---

### Post by vanadium on 2014-05-24
I am surprised. The last argument in your command would be cone_analysis*. Either, there is a matching file or directory, or there is none. If there is none, an error message will result. If there is a matching file name (suppose cone_analysis.py), an error "mv: target &#8216;cone_analysis.py&#8217; is not a directory will result. The command will succeed if there is a matching directory as the last argument. In that case, all your files will be in that directory.

---

