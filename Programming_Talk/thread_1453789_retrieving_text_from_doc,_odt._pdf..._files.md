---
title: "retrieving text from doc, odt. pdf... files"
date: 2010-04-13
forum: Programming Talk
---

### Post by azzamite on 2010-04-13
Hi forum
Is there an api or something that can extract the text from documents?

Since each document type is handled in a different way, I'd like to be
able to call a function with a filename and receive the plain text, I
don't need format, images, tables... only plain text.

I need it to make an inverted index with the text of all the documents
in home, and I'd like to include fancy formats like docx, but I don't
want to write the decoder for that...

---

### Post by myrtle1908 on 2010-04-13
Aspose.  [http://www.aspose.com/](http://www.aspose.com/).  Paid product but it's the only one I've come across that deals with all the MS formats, together with PDF and a few others.  I can vouch for it being very good.  .NET and Java clients avaialable.

There do exist free parsers for many document formats in various languages but these are disparate and generally poorly supported.

Good Luck.

---

### Post by azzamite on 2010-04-13
Unfortunately, I don't support that kind of software :P

I'll search the individual apis you mention and report how they work
(thou it won't be soon)

---

### Post by myrtle1908 on 2010-04-13
Fair enough.  It's not cheap either.  My firm needed it for server side MS document creation and parsing ... there really is no alternative for multi-user server side MS document automation ... even MS use it themselves.

For the MS formats, you can of course use ActiveX/COM automation to parse the files ... allbeit painfully slow and unreliable.  For PDF you could use iText etc.

---

### Post by azzamite on 2010-04-13
> **myrtle1908 said:**
> For PDF you could use iText etc.

Since I haven't decided whether to use c++, python or java, I'll keep
iText in mind, thou it seems to be only for creating, and I need only
to read them.

tanks

---

### Post by nvteighen on 2010-04-14
Hm... you want an API to make an application you're developing be able to read text from those formats, I guess.

Well, gnuPDF is a C API for that. IIRC, the package is libgnupdf-dev. ODF files should easily have some parsing facility, I see some stuff for Perl, Python and Java in the repos. The problem, as usual, would be MS's formats...

---

