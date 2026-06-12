---
title: "[SOLVED] Editing pdf file: how to add pages after scanning?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by LastWho on 2008-10-16
Hi
i used Xsane to scan a document of 4 pages and i put each one in a pdf file; now i like to ve them all in one pdf, so i installed PDFedit, but don't know how to do it??

Is it possible to scan the 4 pages in one pdf file?

thanks

---

### Post by tacutu on 2008-10-16
pdftk lets you merge, split and do many more operations with pdf files. Try it, it's in the repos.

---

### Post by LastWho on 2008-10-16
hi
thank you for your answer
i ve installed it using apt-get but i don't know how to open it :p
can u tell me plz: Alt F2 then i type???

---

### Post by stumbleUpon on 2008-10-16
You could use pdfjoin to join multiple pdf files.

Install using 

sudo apt-get pdfjam

Then in a terminal do 

pdfjoin --outfile output_file_name.pdf file1.pdf file2.pdf file3.pdf

where output_file_name.pdf is the name of the concatenated pdf file

---

### Post by LastWho on 2008-10-16
thats what i found on the"pdftk --help" 
"""Join two files, one of which requires the password 'foopass'. The  out-
       put is not encrypted.
	 pdftk A=secured.pdf 2.pdf input_pw A=foopass cat output 3.pdf"""

can i use pdftk on the graphic world instead??
thx

---

### Post by tacutu on 2008-10-16
pdftk doesn't have a graphic interface. It might be a bit difficult to use the terminal, but if you get used to it it's very powerful tool.

from pdftk --help : 
```
 Join in1.pdf and in2.pdf into a new PDF, out1.pdf
	 pdftk in1.pdf in2.pdf cat output out1.pdf
	 or (using handles):
	 pdftk A=in1.pdf B=in2.pdf cat A B output out1.pdf
	 or (using wildcards):
	 pdftk *.pdf cat output combined.pdf

```

hope that helps.

---

### Post by hyper_ch on 2008-10-16
Cabaret Solutions is also quite nice... it's based on java but it will let you save filled-out pdf forms (couldn't find that in anythign else):

[http://www.cabaret-solutions.com/en/downloads/linux](http://www.cabaret-solutions.com/en/downloads/linux)

---

### Post by LastWho on 2008-10-16
very easy indeed! thank you so much guys ;)

---

### Post by beermotor on 2011-04-19
I know it's threadzombification but that Cabaret Solutions link is dead. I'm currently installing the pdftk/pdfjam stuff above, to see how it works. OpenOffice needs this ability natively!

---

### Post by chrisod on 2011-10-02
The downloads are still there. Just go to the homepage for the program and click to the downloads page.

---

