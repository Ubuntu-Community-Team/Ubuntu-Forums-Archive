---
title: "script for changing extensions and mkdirs"
date: 2008-02-25
forum: Programming Talk
---

### Post by theodorekon on 2008-02-25
I need a script that can change the extensions of all the files in a folder from .mat to .mtx and then to create a directory for each file named after the file.
For example if the folder contained only two files ( 1.mat and 2.mat) it would be like:

```

mv 1.mat 1.mtx
mv 2.mat 2.mtx
mkdir 1
mkdir 2
mv 1.mtx 1/
mv 2.mtx 2/

```

But what if I have hundreds of files??

---

### Post by lnostdal on 2008-02-25
> I need ...

..and _I_ need a Common Lisp implementation(#1) that scales as well as Erlang when faced with large-scale concurrency.

...I somehow felt a need to shout that out into the ether. Sorry.


#1 ..or library - whatever works. If not a library then preferably in form of a patch to SBCL.

---

### Post by ghostdog74 on 2008-02-25
use loops
```

for files in *.mat
do
  mkdir -p "${files%%.mat}"
  newfile="${files%%.mat}.mtx"
  mv "$files" "${files%%.mat}/$newfile"
done 

```

---

### Post by ghostdog74 on 2008-02-25
> **ghostdog74 said:**
> use loops
```

for files in *.mat
do
  mkdir -p "${files%%.mat}"
  newfile="${files%%.mat}.mtx"
  mv "$files" "${files%%.mat}/$newfile"
done 

```
pls read the bash manual from my sig for more information.

---

### Post by theodorekon on 2008-02-25
It worked fine :):) I'm looking into the manual for more details. 
Thanks a lot ghostdog74!!

---

