---
title: "Adding notes to files with a shell script"
date: 2007-01-15
forum: Programming Talk
---

### Post by stabacco on 2007-01-15
Hi all,
i'd like to add some notes in batch mode on my files to be able to do some processing on them. i think that could be a pretty convenient way to add some personal information on files( like the URL from which i have downloaded it , a keyword to help me search with a grep call .
Do you know if and how the notes part is scriptable ??
Thanks
STefano

---

### Post by phossal on 2007-01-15
You use the echo command to print into a file from a bash script.
```
echo "This is a note" > ~/Desktop/file.txt
```

[EDIT] This might not be the answer to your question. If not, please change your question. ;)

---

### Post by thomasaaron on 2007-01-16
to append a note to the end of an existing file, try:

echo note >> filepath

the two >> mean "append"

---

### Post by stabacco on 2007-01-16
I may have been unclear on what i meant, sorry. 
I know how to append text on an ascii file.
 I meant adding a nautilus note on any type of file by right click - Property- Notes. Can i do that with a shell command?

Thanks again, 
STefano

---

### Post by duff on 2007-01-16
It's a little tricky for a shell script, Python or Perl may be more apt for this.

1) Get the full path the file (/path/to/my file)
2) Convert the path to the directory to a URI string, with the protocol part encoded as well (file:%2F%2F%2Fpath%2Fto)
3) Open ~/.nautilus/metafiles/${URI}.xml
4) Find the <file> tag with the attribute "name" being just the filename you're interested in (my%20file).
5) Modify the "annotation" attribute with your note (in XML markup..ie, no line breaks, use &#10; instead).

"grep" around the ~/.nautilus/metafiles directory for known notes to get an idea of what's going on, if you're confused.

---

