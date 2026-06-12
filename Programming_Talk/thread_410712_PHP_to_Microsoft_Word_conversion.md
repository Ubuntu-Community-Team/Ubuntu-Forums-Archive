---
title: "PHP to Microsoft Word conversion"
date: 2007-04-16
forum: Programming Talk
---

### Post by Bagboy23 on 2007-04-16
Hi guys,

I just installed Apache and PHP on my Ubuntu and I'm trying to convert the PHP page into a word doc. Basically it is an invoicing system where the user gets to print of the invoice done in PHP and save it to their local machine as a .doc file. Is there a way?

---

### Post by pmasiar on 2007-04-16
I do not think it will be easy to generate all tricky MS WORD document from PHP - I am not PHP expert but my gut feeling is: generating MS WORD document structure is way beyond run-of-the-mill web-app libraries. You may have better chance using less web oriented language (like Perl or Python) and maybe openOffice document format. I recall Perl library to generate Excel files, check CPAN.

---

### Post by kostkon on 2007-04-16
I suppose you can do it by creating a *macro* in **Openoffice** that opens a HTML file and then converts it to **MS  Word** document. You'll need to say to PHP to save the HTML document somewhere first and then from PHP, again, call openoffice from the command line telling it to run the macro.

I hope I gave you some ideas...

---

### Post by pmasiar on 2007-04-16
maybe better way is create PDF - PDF is *much* more open format than evil MS WORD. Here is [PDF in Python](http://www.devshed.com/c/a/Python/Python-for-PDF-Generation/) - look at your favorite PHP library resources for something like that.

---

### Post by Mirrorball on 2007-04-16
I also think that PDF would be the best format, but RTF is also an option. MS Word and Wordpad are able to open RTF files, as well as OpenOffice.

---

