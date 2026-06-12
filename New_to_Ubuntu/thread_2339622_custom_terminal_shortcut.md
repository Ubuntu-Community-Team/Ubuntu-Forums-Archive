---
title: "custom terminal shortcut"
date: 2016-10-10
forum: New to Ubuntu
---

### Post by Pinkie_B on 2016-10-10
Hi All,

I am slowly trying to shift my workflow into the terminal because I'm a speedy typer and also it's fun.

I use sublime text as an editor for LaTeX, but it does not have a settings option (that I know of) to automatically clean up the generated files on each build.

So, what I would like to do is create a custom command in the terminal so that when I'm organizing my workspace I can with one command clean up all these extraneous files. The command I would like to summarize would be something like

```
rm -f *.aux *.fdb_latex *.fls 
```

and I would like to name it something like

```
 cleanlatex 
```

and I would like to be able to run it from anywhere in the file directory.

Except in root or other places where important system files live. But I'm ok if that isn't a safety I can build in. I mostly keep all my LaTeX files in the same collection of folders so it's not a big burden to just be watchful. At the moment I'm just running this script in long form every time I log in.

Another option that I would like to build would be a command with an argument. For example

```
cleanlatex filename
```

and the action being

```
rm -f filename.aux filename.fdb_latex filename.fls filename.log
```

btw, somewhere I modified my ```
rm
``` command to be noisy and prompt me because I was accidentally rm'ing instead of mv'ing because I'm dislexic. That's why I'm speficying the -f option. Also, I did not misspell "specifying" on purpose.

Thanks people!

Pink

PS. I got the inspiration for my question from this answer: [http://unix.stackexchange.com/a/84694](http://unix.stackexchange.com/a/84694) it's pretty close to what I want, but has some language like "path variable" that I don't know.

---

### Post by papibe on 2016-10-10
Hi Pinkie_B.

This should work. Test it, and when you feel it's OK, remove the word 'echo' on the 2 relevant lines:
```
#!/bin/bash

if [ $# -eq 1 ]; then
    echo rm -f "$1.aux" "$1.fdb_latex" "$1.fls" "$1.log"
else
    echo rm -f *.aux *.fdb_latex *.fls
fi

```
save it as 'cleanlatex', then add execute permissions:
```
chmod a+x cleanlatex
```
Then create a bin directory in your home:
```
mkdir ~/bin
```
and finally move your script to that directory
```
mv -iv cleanlatex ~/bin/
```
It should work for all new terminals. No need for mess with PATH (in Ubuntu your ~/bin is added to the path if the directory exists).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Pinkie_B on 2016-10-10
Oooh, I'm excited! I'm going to try this right now! 
(I'm supposed to be "working")

---

### Post by Pinkie_B on 2016-10-11
Ok, so here's what I've got. I start with this pile of files:
```
pset01_2016W.aux          pset01_2016W.synctex.gz   pset02_2016W.log
pset01_2016W.fdb_latexmk  pset01_2016W.tex          pset02_2016W.pdf
pset01_2016W.fls          pset02_2016W.aux          pset02_2016W.synctex.gz
pset01_2016W.log          pset02_2016W.fdb_latexmk  pset02_2016W.tex
pset01_2016W.pdf          pset02_2016W.fls

```

then I tell my terminal

```
cleanlatex pset01_2016W
```

and it tells me

```
rm -f pset01_2016W.aux pset01_2016W.fdb_latex pset01_2016W.fls pset01_2016W.log 1.synctex.gz
```

and that *looks* like it's removing the files I wanted. I did notice a typo which missed a file, but that's not a big deal. The kicker is that when I ls my folder contents, I get back

```
pset01_2016W.aux          pset01_2016W.synctex.gz   pset02_2016W.log
pset01_2016W.fdb_latexmk  pset01_2016W.tex          pset02_2016W.pdf
pset01_2016W.fls          pset02_2016W.aux          pset02_2016W.synctex.gz
pset01_2016W.log          pset02_2016W.fdb_latexmk  pset02_2016W.tex
pset01_2016W.pdf          pset02_2016W.fls
```

again, which I'm pretty sure is the exact set of files I started with. Maybe it's erasing them from a different location? I'm pretty sure I copied the suggest code directly, so I don't think it's a typo in that regard.

Anyway, any debugging advice here would be appreciated.

Best

Pinkie

---

### Post by sudodus on 2016-10-11
Did you remove the word 'echo' from the 2 relevant lines?

The echo is there for testing, that the script finds the files you want, and when it does, make it do the real thing by removing the word 'echo' from the script.

---

