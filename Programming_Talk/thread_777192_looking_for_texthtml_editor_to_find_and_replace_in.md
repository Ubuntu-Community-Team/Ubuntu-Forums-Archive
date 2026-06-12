---
title: "looking for text/html editor to find and replace in multiple files"
date: 2008-05-01
forum: Programming Talk
---

### Post by adohall on 2008-05-01
I like Bluefish. But what I need from time to time is the ability to:

a) search and replace within a project or folder without opening those files;
b) replace 'all' instances of a text pattern found without having to click 'continue' or 'replace next' each time.

Is there software available for Ubuntu which will do those 2 things?

---

### Post by WW on 2008-05-01
> **adohall said:**
> I like Bluefish. But what I need from time to time is the ability to:

a) search and replace within a project or folder without opening those files;
b) replace 'all' instances of a text pattern found without having to click 'continue' or 'replace next' each time.

Is there software available for Ubuntu which will do those 2 things?

If you don't mind using the command line, there are many ways to do this.  For example, you can use **sed**.  This command will replace all occurrences of "old_string" with "new_string" in all the files ending with .html in the current directory:
```

$ sed -i~ 's/old_string/new_string/g' *.html

```
Backup copies of the original files will be saved with the extension "~".

---

### Post by WorldTripping on 2008-05-01
You can also use rpl, as I found out yesterday:
[http://ubuntuforums.org/showthread.php?t=775817]("http://ubuntuforums.org/showthread.php?t=775817")

This will Find & Replace a text string within a document (text, html, whatever), recursively through a directory structure.

Took me about 1.5 seconds to replace '/blah/index.html' with '/blah/index.php' over 450+ files in many sub directories of a web project

I found out about it here:
[http://crunchbang.org/archives/2008/04/20/rpl-a-find-and-replace-terminal-tool/]("http://crunchbang.org/archives/2008/04/20/rpl-a-find-and-replace-terminal-tool/")

---

### Post by WW on 2008-05-01
> **WorldTripping said:**
> You can also use rpl ...
Cool, thanks for the tip.  I especially like the **--dry-run** option.

---

