---
title: "can't print from command line"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by rmbp on 2014-03-14
I've recently installed Lubuntu 3.10 on a Dell desktop with a pentium D and 2GB RAM. 

I've installed cups and have configured a network printer (Dell 3100cn) through the browser using localhost:631. I  can print pdf files from Firefox. If I type lpstat -t, I get confirmation that the printer is installed, but if I type lpq -Pnameofprinter it says that the printer is unknown. I sent some files - both plain text and pdf - to the printer using lpr, and they are in the queue, as confirmed by lpq -Pnameofprinter.

Any clues as to how I can solve this?

Thanks!

---

### Post by smuthavarapu on 2014-03-16
i can reproduce your issue. But no luck in resolving the issue.

can you print from file --> menu.

Probebly if you solve that, it automatically solves from command line.

Let me know if you want me to keep looking or you solved the issue.

---

### Post by rmbp on 2014-03-17
[ 						 							]("http://ubuntuforums.org/member.php?u=1208205")[[COLOR=#000000]smuthavarapu[/COLOR]]("http://ubuntuforums.org/member.php?u=1208205"), Thanks for taking the time to help me! 

I've installed cups-bsd and that seems to have solved some of the issues I report above. I've installed other packages in the meanwhile, so I cannot say for sure that this was the one that did it, but I'm pretty sure it was. 

Now the problem that I have is that the pdf files come out of the printer about the size of a stamp. Not if I send them to the printer from Firefox, but it happens if I send them from the command line or from emacs, say. Any remedies for that?

Cheers!

---

### Post by rmbp on 2014-03-17
> **rmbp said:**
> 
Now the problem that I have is that the pdf files come out of the printer about the size of a stamp. Not if I send them to the printer from Firefox, but it happens if I send them from the command line or from emacs, say. Any remedies for that?

Somehow the default number of pages per sheet is set at 16! Typing "gksudosystem-config-printer" allows one to change that (Printer>Properties>Job options)

---

