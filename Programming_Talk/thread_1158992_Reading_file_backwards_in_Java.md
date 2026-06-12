---
title: "Reading file backwards in Java"
date: 2009-05-14
forum: Programming Talk
---

### Post by MeLight on 2009-05-14
Hi,
I'm looking to make a simple text files reader, a program which will show a portion of text file (x lines per page) and will have Fwd and Bwd buttons. Now how to read the next lines I know, is it possible to run backwards on a file?

---

### Post by kjohansen on 2009-05-14
why not just read the whole text file into an array of lines or some other container and then you can easily go back in forth in an array or a vector or whatever...

---

### Post by iiska on 2009-05-14
It's possible to access data from the end of the file without reading the whole file, by using seek() -method of the java.io.RandomAccessFile class.

More info at here: [http://www.docjar.org/docs/api/java/io/RandomAccessFile.html#seek(long)](http://www.docjar.org/docs/api/java/io/RandomAccessFile.html#seek(long))

---

### Post by HavocXphere on 2009-05-14
Sure...but it will be slooooow. Mainly because you can't read it in blocks. (Or rather you can but it will add a lot of complexity).

Also, it will help to know how big the file is. If its small then you can just load it into an array. If its 1 gig+ then the PC will have a heartattack if you try to load that into a structure.

---

### Post by MeLight on 2009-05-14
[quote=iiska]it's possible to access data from the end of the file without reading the whole file, by using seek() -method of the java.io.randomaccessfile class.
[/quote]

That's probably what I'm gonna use unless there's a way to read lines backwards? 
The file sizes we're speaking of are 1g and up, that's why I need a "paged" browser

---

### Post by DocForbin on 2009-05-14
Not following the read backwards point. If forward and back move a page (e.g. 100 lines) at a time, just keep track of the first byte of each page. When you go to the next page, make back seek to that byte. You could add page numbers using a similar approach by generating a collection of byte offsets for each x lines when first opening the file.

---

### Post by MeLight on 2009-05-15
[QUOTE="DocForbin"]Not following the read backwards point. If forward and back move a page (e.g. 100 lines) at a time, just keep track of the first byte of each page. When you go to the next page, make back seek to that byte. You could add page numbers using a similar approach by generating a collection of byte offsets for each x lines when first opening the file.[/QUOTE]

That would be perfect, unless you want to enable dynamic page size, ie changing the page size in real time

---

