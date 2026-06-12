---
title: "read from pdf to script"
date: 2011-11-11
forum: Programming Talk
---

### Post by conradin on 2011-11-11
Hi all,
I am using pdf creator, to print files that would otherwise be printed. I know pdf Creator has the option to print to text, but when I do the data comes out screwy, or in weird inconsistent places. The PDF printing works very well though, its consistent, and looks how I would expect. 

What I need to do how ever is process the data in each pdf, into a script or something that can enter the data into a database. Can anyone give me some advice on how to read data from a pdf, and utilize it in a bash script?

I need some way to read the pdf, select certain values, and save them to a seprate file that can be fed into a database. Im looking for any ideas.

---

### Post by ballantony on 2011-11-12
Just to clarify, the data you want is already in pdf form, you're just using pdf creator as a way of getting at it?

---

### Post by conradin on 2011-11-12
The data is in pdf form, and I need to get it into a bunch of script variables.

---

### Post by ballantony on 2011-11-13
Great... I'd like to know how to do this too.  Anyone?

---

### Post by Zugzwang on 2011-11-15
There is no simple solution to your problem (text could also be in bitmap form in the Pdf, text could be rotated, characters can be arranged along a line in the Pdf, letting every character stand along from a logical point of view, etc.).

You could however try "converting" the pdf file to a text file by running "pdftotext". Another possiblity is to render your pdf to image files and running "gocr"/"jocr" to recognize the text.

---

### Post by conradin on 2011-11-17
Hi Zugwang, 
I did end up using pdftotext which works ok. 
I cam across an Adobe SDK that helps programmers work around pdfs,
but it a windows thing, and I haven't a bit of time to get into it yet.

---

### Post by ballantony on 2011-11-17
> **conradin said:**
> Hi Zugwang, 
I did end up using pdftotext which works ok. 
I cam across an Adobe SDK that helps programmers work around pdfs,
but it a windows thing, and I haven't a bit of time to get into it yet.
 
 
Just had a look at it.  Not bad, and its cheaper the Adobe pro.  Not perfect, but a step in the right direction.
 
Thanks, conradin.

---

