---
title: "pdf printing without cups-pdf?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by joep-vd on 2008-10-13
Hello! 

Is there an alternative or nice interface to cups-pdf? I want to be prompted for a filename and location when printing to a pdf. Renaming a ******** of separate pdfs that have a job number attached because otherwise the cups-pdf takes the guts of overwriting existing files without asking permissions pisses me off. Tagline: Cups-pdf: Data Destruction by Design! 

There are multiple solutions available for Windows, and I am a bit surprised that this doesn't seem to be available for linux/Ubuntu. I hope someone can point me to what I have missed. 

And no, I am not looking for built in pdf creation within some of the programs. Thanks a lot!

---

### Post by _sAm_ on 2008-10-13
You can change the output, but I don't think you can make it ask for name/output for each print. I agree with you, would bee nice. 

See here;
[http://ubuntuforums.org/showthread.php?t=210761](http://ubuntuforums.org/showthread.php?t=210761)

---

### Post by joep-vd on 2008-10-13
Thanks for your reply, but that doesn't solve my problem. I need more than one location to manage my pdfs. 

I am not a coder, but how complicated could it be to put a "Save as..."-dialogue in? Isn't that a ready-made thing that just needs to be pasted somewhere in this cups-pdf-thing?

---

### Post by _sAm_ on 2008-10-13
"*Any comments, suggestions or bug reports on CUPS-PDF are very welcome!*"

[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/)

Edit;
Check this out; 
[http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/](http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/)
"I use a somewhat different approach. When printing I substitute kprinter for lpr. This pops up the KDE print dialog, which includes an option to produce PDF. It doesn&#8217;t matter that I use GNOME instead of KDE, it still works fine. You need to install the kdeprint package to do this."

---

### Post by joep-vd on 2008-10-14
Thanks a lot! This is a solution! 

I will send an email to the cups-pdf developer to fix this strange data destruction default in this piece of software...

---

