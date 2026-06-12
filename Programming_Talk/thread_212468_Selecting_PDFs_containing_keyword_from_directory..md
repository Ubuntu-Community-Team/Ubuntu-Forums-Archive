---
title: "Selecting PDFs containing keyword from directory."
date: 2006-07-09
forum: Programming Talk
---

### Post by BioGeek on 2006-07-09
Hey Everyone,

I have a directory filled (among others) with PDFs. There are also some subdirectories, some of which also contain PDFs. Now, I'd like to extract all the PDFs in this direcory containing a certain keyword, and move them to a new directory.

I found [pdfsearch]("http://pdfsearch.sourceforge.net/") which seems to do everything what I want, but I couldn't get it to work since it depends on [Lupy]("http://www.divmod.org/projects/lupy") which is no longer maintained.

I could get the keyword out of a single PDF file with the following command:

```
pdftotext my.pdf - | egrep keyword --color=always
```

but I don't know how to proceed further.

Thanks in advance.

---

### Post by cwaldbieser on 2006-07-11
> **BioGeek said:**
> Hey Everyone,

I have a directory filled (among others) with PDFs. There are also some subdirectories, some of which also contain PDFs. Now, I'd like to extract all the PDFs in this direcory containing a certain keyword, and move them to a new directory.

I found [pdfsearch]("http://pdfsearch.sourceforge.net/") which seems to do everything what I want, but I couldn't get it to work since it depends on [Lupy]("http://www.divmod.org/projects/lupy") which is no longer maintained.

I could get the keyword out of a single PDF file with the following command:

```
pdftotext my.pdf - | egrep keyword --color=always
```

but I don't know how to proceed further.

Thanks in advance.

You probably want to use "find" to give you a list of pdf files to search:

```

$ find . -type f -name '*.pdf' -print |
> while read file
> do
>   if [ -n "$(pdftotext $file - | grep $keyword)" ] ; then
>      echo "$file"
>   fi
> done

```

---

