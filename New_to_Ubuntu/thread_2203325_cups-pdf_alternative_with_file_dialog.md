---
title: "cups-pdf alternative with file dialog?"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by bbroderma on 2014-02-02
Cups-pdf is great with the in-print-menu selection of PDF, but it silently generates the PDF to the ~/PDF directory, which is not ideal.  Is there any other software that will print to PDF and instead pop up a dialog box to let you select the name and location of the PDF you are creating?

---

### Post by sudodus on 2014-02-03
Welcome to the Ubuntu Forums :-)

You can use ***libreoffice***. See ```
man libreoffice
```

If you run the following script from a terminal window, it will create the pdf file in the current directory

```
soffice --headless --convert-to pdf filename
```

Example for a single file

```
soffice --headless --convert-to pdf hello-world.odt
```

Example for all doc files and docx files in the directory

```
soffice --headless --convert-to pdf *.doc*
```

I have made an ***alias*** (that is defined by the following line in [FONT=courier new]**~/.bashrc**[/FONT]

```
alias 2pdf='soffice --headless --convert-to pdf'
```

so that I can simply type

```
2pdf hello-world.odt
``` to create the pdf file [FONT=courier new]**hello-world.pdf**[/FONT]

---

### Post by tgalati4 on 2014-02-03
Some applications have a way to change the directory.  For instance, if you open a PDF with *evince* and you want to print it using "Print to File" it defaults to ~/output.pdf, but there is a button with the directory that allows you to select any directory.  I don't know how to change the default directory for "Print to File".  There must be a way, I just don't know it.  I couldn't find it in gconf settings.

---

### Post by iaselle on 2014-07-10
Very upset with the drawbacks of CUPS-PDF, I have developed a PDF printer that produces smaller PDF files with a "save as" dialog.

[http://forums.linuxmint.com/viewtopic.php?f=47&t=172796](http://forums.linuxmint.com/viewtopic.php?f=47&t=172796)

If someone wants to "industrialize" this and create an Ubuntu package based on this, please do it :)

---

