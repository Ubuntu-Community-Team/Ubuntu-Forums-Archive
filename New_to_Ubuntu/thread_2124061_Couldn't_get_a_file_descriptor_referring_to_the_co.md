---
title: "Couldn't get a file descriptor referring to the console"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-03-09
I want to open a file from within the console. I want the console to figure out my preferred program for opening the file. When I tell it "open file.pdf" I get the error "Couldn't get a file descriptor referring to the console".

Is there a way around this? I'd like the system to recognise my preferred programs for each type of file.

---

### Post by schragge on 2013-03-09
The command you want is called [see]("http://manpages.ubuntu.com/manpages/precise/en/man1/see.1.html") on Debian-based systems. *open* aka [openvt]("http://manpages.ubuntu.com/manpages/precise/en/man1/openvt.1.html") does something completely different: starts a program on another virtual terminal.

---

### Post by Kevin McCready on 2013-03-09
Thanks. But I think I need to tweak my system further. I got this error:
Error: no "view" mailcap rules found for type "application/pdf"

---

### Post by Cheesemill on 2013-03-09
You can used the command xdg-open to open a file with its associated application, for example...
```
xdg-open file.pdf
```
will open file.pdf with Evince (or whatever application you have associated with pdfs).

---

### Post by Kevin McCready on 2013-03-09
Cool! Thanks! It worked!

---

