---
title: "printing in PHP (server side not client)"
date: 2010-07-21
forum: Programming Talk
---

### Post by ernest_francis on 2010-07-21
It's been a long time since I created printer friendly files so I need some help as I've never done this in Ubuntu.

I have a PHP script that will create (not written yet) a print file, this file *may* include an image to print as well as a logo.

I will create the file in either 1 or 2 directories that the php script will have access to. 

1 directory per printer. 

What I need to know is:

is there a utility to automatically print files from a given directory and then erase the files or how do i set up some sort of job to do this and ?

what sort of formatting can i do ? would it be easier to create pdf's ? 

i haven't accessed a printer in about 15 years lol so i am a bit out of touch with all this.

thanks for your help

---

### Post by nebu on 2010-07-22
there is a command line utility called lpr.... which intfaces with CUPS.... so if you store the data you need in a file called file1 and then run the command
```
shell_exec("lpr -P <printer> file1");
```
it should print this out the the selected printer.... lpr has a lot more options probably you can check its manual page for more information

if you want to create pdfs with content and images on the fly.... just parse your data into a latex file.... run pdflatex.... and then lpr it out...

---

