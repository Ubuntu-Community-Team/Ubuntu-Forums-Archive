---
title: "&quot;Find in files&quot; + &quot;find in files &amp; replace&quot;  editor"
date: 2006-11-15
forum: Programming Talk
---

### Post by Mis_Uszatek on 2006-11-15
I am using Kate for programming actually.
It is quite good editor, but I miss two things:
"Find in files" and "Find in files & replace"

Is there any good editor for C++ programming with these options?
Or just an editor with these options(I can stand that I will have to use second editor just for this :) .

Or maybe some of you know some good work-around for this problem?
When I am in directory and type
"cat * | grep pattern" I will have all lines with this pattern, but I really miss filenames also(line position would be nice, but it is not necessary)

---

### Post by -Rick- on 2006-11-15
Kate can "Find in files" (just click on the bottom left tab...). KDevelop can do both find and replace in files.

---

### Post by koenn on 2006-11-15
sed

kinda difficult (uses regexp and very compact commands) but can do, among a lot of other things, 'find and replace' on one or multiple files.

see [http://www.student.northpark.edu/pemente/sed/sed1line.txt](http://www.student.northpark.edu/pemente/sed/sed1line.txt) for a first impression

also : awk
[http://www.student.northpark.edu/pemente/awk/awk1line.txt](http://www.student.northpark.edu/pemente/awk/awk1line.txt)

---

### Post by Ramses de Norre on 2006-11-15
> **Mis_Uszatek said:**
> "cat * | grep pattern"

Nice example of erroneous cat usage, this will do too: ```
grep pattern *
```

---

### Post by shining on 2006-11-15
> **Ramses de Norre said:**
> Nice example of erroneous cat usage, this will do too: ```
grep pattern *
```

This erroneous usage also prevents filename from being displayed.
So using cat and piping it to grep isn't only useless, it's much worse :)

Personally, I like vim as an editor, because it's the only one where I know how to do search and replace.
/foo for searching
s/foo/bar/ for replacing the first occurence of foo by bar on the current line
s/foo/bar/g for replacing every occurence of foo by bar on the current line
%s/foo/bar/ for replacing the first occurence of foo by bar on every line
%s/foo/bar/g for replacing every occurence of foo by bar

---

### Post by Mis_Uszatek on 2006-11-15
> grep pattern *

Great trick, thanks.

And yes, Kate has find&replace, I have been using it(Kate( for more than week.
I really don't know how it was possible that I hadn't noticed this option earlier :D
This button is not 1x1 pixels size ;-)

Thanks for help, life is more easier now.

ADDED:
btw, I have founded one-liner how to find&replace in all (in this example) cpp files in dir
perl -pi -e 's/FIND/REPLACE/' *.cpp

more in :
[http://www.debian-administration.org/articles/298]("http://www.debian-administration.org/articles/298")

---

### Post by cwaldbieser on 2006-11-15
> **Mis_Uszatek said:**
> I am using Kate for programming actually.
It is quite good editor, but I miss two things:
"Find in files" and "Find in files & replace"

Is there any good editor for C++ programming with these options?
Or just an editor with these options(I can stand that I will have to use second editor just for this :) .

Or maybe some of you know some good work-around for this problem?
When I am in directory and type
"cat * | grep pattern" I will have all lines with this pattern, but I really miss filenames also(line position would be nice, but it is not necessary)

```

$ grep -n pattern files

```
shows the files and line numbers.

---

### Post by Ramses de Norre on 2006-11-16
> **shining said:**
> 
/foo for searching
s/foo/bar/ for replacing the first occurence of foo by bar on the current line
s/foo/bar/g for replacing every occurence of foo by bar on the current line
%s/foo/bar/ for replacing the first occurence of foo by bar on every line
%s/foo/bar/g for replacing every occurence of foo by bar

Typing "/" again will search for the next occurrence of the word, "?" searches backwards.

---

