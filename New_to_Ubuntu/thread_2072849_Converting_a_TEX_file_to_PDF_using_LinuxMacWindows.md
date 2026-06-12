---
title: "Converting a TEX file to PDF using Linux/Mac/Windows?"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by honeybear on 2012-10-18
Hi,

I have a friend that gaves me a *.tex file to further work on it. Report for school. 

However, what is the most compatible way to convert it to PDF?

What's the best of the best (small size to install)?

Thanks

---

### Post by Dave_L on 2012-10-18
Is that LaTeX?

LibreOffice apparently can import it: [http://extensions.libreoffice.org/extension-center/texmaths-1](http://extensions.libreoffice.org/extension-center/texmaths-1)

And LibreOffice can export to .pdf.

---

### Post by honeybear on 2012-10-18
> **Dave_L said:**
> Is that LaTeX?

LibreOffice apparently can import it: [http://extensions.libreoffice.org/extension-center/texmaths-1](http://extensions.libreoffice.org/extension-center/texmaths-1)

And LibreOffice can export to .pdf.

libreoffice is 700 mb installl ... pff

---

### Post by audiomick on 2012-10-18
What OS do you have on your computer, and what are you looking at the file with?

If you are looking at the file on an Ubuntu machine with a program that can print, you can go that way. Tell it to print, and in the print dialogue choose "print to file" instead of a printer. You can choose pdf there as the file format.

---

### Post by honeybear on 2012-10-18
> **audiomick said:**
> What OS do you have on your computer, and what are you looking at the file with?

If you are looking at the file on an Ubuntu machine with a program that can print, you can go that way. Tell it to print, and in the print dialogue choose "print to file" instead of a printer. You can choose pdf there as the file format.

I am using daily window and ubuntu.

---

### Post by audiomick on 2012-10-19
I couldn't find any info about daily window. What is that?

Whatever, if it is a program that can print in Ubuntu, then try what I suggested, or did you already?

---

### Post by LiamOS on 2012-10-19
In Ubuntu, if you're a tiny bit familiar using the terminal, install texlive:
```
$ sudo apt-get install texlive 
```and then you can run:
```
$ pdflatex myfilename.tex 
```to create your pdf output. 
This would likely be the most efficient way to do it. 
Mac would be the same, but with a different install command. I never managed to get latex to work with Windows(The straw that made me install Ubuntu), so i can't comment on that.

Otherwise, you can install something like texmaker from the software centre which is a nice editor which does the compiling for you(uses texlive).

---

### Post by lhb1142 on 2012-10-19
> **honeybear said:**
> Hi,

I have a friend that gaves me a *.tex file to further work on it. Report for school. 

However, what is the most compatible way to convert it to PDF?

What's the best of the best (small size to install)?

Thanks

**If** you are able to open and read this .tex file, I think that the easiest thing to do would be to _copy_ it and _paste_ it into the Abiword program. Abiword is a very small download from the repository and works as well as LibreOffice Writer.

Then, from the document in Abiword, merely Print (to File). This will create your .pdf document.

I hope that helps you.

---

