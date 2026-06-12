---
title: "Opening browser window in SciTE"
date: 2007-07-15
forum: Programming Talk
---

### Post by LeeU on 2007-07-15
I have just begun using SciTE as an editor but can't figure out how to open a file (i.e., HTML or PHP) in Firefox to view it as a Web page. Anybody have any suggestions?

---

### Post by pmasiar on 2007-07-16
I am confused: Do you want to open file in SciTE, or in Firefox? Or you want some function in SciTE, which will open current file in FF? SciTE does not have that IFAIK

---

### Post by LeeU on 2007-07-16
If I am editing a file in SciTE, I want to be able to view it in Firefox. Kind of a useless editor (at least for my purposes) if I can't open a file directly from it.

---

### Post by talowe on 2007-07-16
> **LeeU said:**
> I have just begun using SciTE as an editor but can't figure out how to open a file (i.e., HTML or PHP) in Firefox to view it as a Web page. Anybody have any suggestions?

go to Options->Open User Options File

Add:
```

# file extensions to open with browser - Semi-colon separated list
file.patterns.html=*.html;*.php

command.go.$(file.patterns.html)=firefox $(FilePath)

```

When you have a file of type listed in $(file.patterns.html) open Tools->Go or F5 will open the file in firefox.  Read the help file to see how to add your own commands to the tools menu.

---

### Post by LeeU on 2007-07-16
Thanks, talowe. That worked.

Now I just have a problem with Firefox continuously reloading files with .php extensions.

---

### Post by talowe on 2007-07-17
> **LeeU said:**
> Thanks, talowe. That worked.

Now I just have a problem with Firefox continuously reloading files with .php extensions.

I don't know much about web programming, can't help with that.  Might try a new thread with a subject that will catch the eye of those that do.

---

