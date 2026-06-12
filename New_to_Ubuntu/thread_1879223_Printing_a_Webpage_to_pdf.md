---
title: "Printing a Webpage to pdf"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by meadhikari on 2011-11-11
If I need to print a webpage what i do now is this
1. Visit the webpage in chromium
2. Right Click and Select Print
3. Then select 'print to file'
4. Then give the filename for the pdf file and the location to save.
5. Then I click the print button

How Would I do exactly the same thing from the command line?
The pdf file printed would use the print.css if available

Thanks in advance.

---

### Post by Mark_in_Hollywood on 2011-11-12
I find this may be what you are seeking:

[http://www.linuxquestions.org/questions/linux-software-2/print-files-in-pdf-or-html-format-from-the-linux-command-line-204012/]("http://www.linuxquestions.org/questions/linux-software-2/print-files-in-pdf-or-html-format-from-the-linux-command-line-204012/")


lpr -P "printerName" document.pdf

---

