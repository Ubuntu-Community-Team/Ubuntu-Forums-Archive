---
title: "sed: regular expressions optional patterns"
date: 2011-05-03
forum: Programming Talk
---

### Post by AbsolutIggy on 2011-05-03
EDIT: I realised the second } caused some problems, because it appended an extra \r to the output. I've added a backslash before the ending } which I want as a literal
------------
EDIT 2: adding an extra .bib in the bibliography command does not cause latex to look for the same file as without, but it works anyway?
------------

I'm trying to read a filename, with or without a filename from within a latex command in a file, such as:

```

\bibliography{/home/user/references}

```
or
```

\bibliography{/home/user/references.bib}

```
(the first command causes Latex to look for exactly the same file as the second)

I want to extract the filename part with the extension, result I want:
```

/home/user/references.bib

```

I'm trying to use sed for this, but it doesn't quite work. What I have so far:
```
sed -n 's:\\bibliography{\(.*\)\(\.bib\)?}:\1.bib:p' latexfile.tex
```
returns nothing, regardless of extension in the latex file. (+ instead of ? gives the same result)

```
sed -n 's:\\bibliography{\(.*\)\(\.bib\)\{1\}}:\1.bib:p' latexfile.tex
```
gives my expected result if I write the whole filename (including .bib) in the latex file, but returns nothing if I exclude .bib in the latex file.

```
sed -n 's:\\bibliography{\(.*\)\(\.bib\)\{0,1\}}:\1.bib:p' latexfile.tex
```
adds an extra .bib if the .bib extension is already in the tex file. I assume the first pattern covers everything in this case, and the {0} is used to get rid of that pattern.

How do I get sed to match a .bib if it is there, and ignore if it is missing? I've tried with various uses of g, but does not quite seem to work..

Thanks!

---

### Post by Arndt on 2011-05-03
> **AbsolutIggy said:**
> I'm trying to read a filename, with or without a filename from within a latex command in a file, such as:

```

\bibliography{/home/user/references}

```
or
```

\bibliography{/home/user/references.bib}

```
(the first command causes Latex to look for exactly the same file as the second)

I want to extract the filename part with the extension, result I want:
```

/home/user/references.bib

```

I'm trying to use sed for this, but it doesn't quite work. What I have so far:
```
sed -n 's:\\bibliography{\(.*\)\(\.bib\)?}:\1.bib:p' latexfile.tex
```
returns nothing, regardless of extension in the latex file. (+ instead of ? gives the same result)

```
sed -n 's:\\bibliography{\(.*\)\(\.bib\)\{1\}}:\1.bib:p' latexfile.tex
```
gives my expected result if I write the whole filename (including .bib) in the latex file, but returns nothing if I exclude .bib in the latex file.

```
sed -n 's:\\bibliography{\(.*\)\(\.bib\)\{0,1\}}:\1.bib:p' latexfile.tex
```
adds an extra .bib if the .bib extension is already in the tex file. I assume the first pattern covers everything in this case, and the {0} is used to get rid of that pattern.

How do I get sed to match a .bib if it is there, and ignore if it is missing? I've tried with various uses of g, but does not quite seem to work..

Thanks!

Maybe you can extract the whole name, add .bib and then replace .bib.bib with .bib.

---

### Post by AbsolutIggy on 2011-05-03
*Looks like I was wrong about latex, but the result is the same..*

Your suggestion works if I do it like this:
```

sed -n 's:\\bibliography{\(.*\)\}.*:\1.bib:p' "latexfile.tex" | sed 's:\.bib\.bib:.bib:'

```

Is it possible to combine this into one sed command?

---

### Post by DaithiF on 2011-05-03
Hi, the problem is that sed doesn't have a 'non-greedy' mode, so your first \(.*\) will consume all the string regardless of whether there is a .bib at the end or not.

do it in two passes (this can be 2 expressions within a single sed command using the -e parameter).

e.g.:
```
$ echo "\bibliography{/home/user/references.bib}" | sed -e 's:\\bibliography{\(.*\)}:\1:' -e 's:\(\.bib\)\?$:.bib:'
/home/user/references.bib

$ echo "\bibliography{/home/user/references}" | sed -e 's:\\bibliography{\(.*\)}:\1:' -e 's:\(\.bib\)\?$:.bib:'
/home/user/references.bib

```

---

### Post by Vaphell on 2011-05-03
```
$ echo $'b{/x/y/z/wtf.bib}\nb{/x/y/z/wtf}' | sed -r 's:b[{]([/a-z]*).*[}]:\1.bib:' 
/x/y/z/wtf.bib
/x/y/z/wtf.bib

```

if you are sure there are no dots in the name you can limit name section to [a-z] or whatever range of chars you wish

---

### Post by AbsolutIggy on 2011-05-03
Thanks for the answers guys.

Your version works great, DaithiF. Vaphell: Thanks for the suggestion, but I want to keep it as general as possible, and it's easy to miss some characters by defining more limited ranges!

---

