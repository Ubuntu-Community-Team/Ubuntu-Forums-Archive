---
title: "Syntax and gedit for code"
date: 2008-03-09
forum: Programming Talk
---

### Post by DarkW0lf on 2008-03-09
I have been off and on trying to get syntax highlighting for HLA in gedit and to use the plugins for build/make.

But I run into a wrong path or something and the system still wants to tell me the HLA source is C (apparently because I start my files with a // comment).

At this point I just want to start again and try to get syntax and gedit's build plugin working. I am not sure if I am understanding the XML format that the GNOME docs are describing for highlighting (gtksourceview).

Where to get started (again) ?

---

### Post by PaulFr on 2008-03-09
Does this post help ? **[http://ubuntuforums.org/showpost.php?p=4474410&postcount=2](http://ubuntuforums.org/showpost.php?p=4474410&postcount=2)**

---

### Post by DarkW0lf on 2008-03-09
Maybe, does the XML syntax of the attach files look correct ?

If the XML file is correct I can always go back and fix the colors or keyword lists to match HLA.

I am a little wary if I wrote the regex right.

---

### Post by firecrow8 on 2008-03-27
did it work?

your files looked good in gedit accept that I opened the xml in firefox and got a parse error.
```
XML Parsing Error: mismatched tag. Expected: </match>.
Location: file:///home/firecrow/.fr-tEfd2J/hla.lang
Line Number 52, Column 6:   </context>
-----^
```

for what it's worth I've been able to get custom syntax to work and have outlined the structure of the xml here:
[http://ubuntuforums.org/showthread.php?t=736843]("http://ubuntuforums.org/showthread.php?t=736843")

---

### Post by DarkW0lf on 2008-03-30
I haven't tried yet, wnated to make sure XML structure was sound.
That way the only thing wrong would be specific to the programming language.

I did bookmark your other post, thanks.

---

### Post by DarkW0lf on 2008-03-30
No, it doesn't work.

My files get misidentified as C source and when I switch gedit to HLA there is no highlight.
I don't know if this is an issue with mimetypes (the misidentify) or with my regex (no highlight) or both.

---

### Post by firecrow8 on 2008-03-31
wierd... 

so you do see your newly declared filetype in the gedit highlight menu. 
that's one down. bout six more to go.

---

### Post by DarkW0lf on 2008-04-19
Seems I lost all highlighting for all filetypes.

Back to the drawing board.

---

