---
title: "Does Ubuntu have a tool for doing copy-paste from a PDF?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by swarup on 2008-06-04
I need to copy a bunch of material from PDF files downloaded off the web, and paste it into a text file. But normally one cannot highlight and copy text from a PDF file. Is there some tool in Ubuntu (or in Linux anywhere) which will allow one to do it?

---

### Post by Kevbert on 2008-06-04
Highlight what you want to copy.  Ctrl+C to copy.  Ctrl+V to paste.
Works for many apps.

---

### Post by django0909 on 2008-06-04
As far as I know you can open pdf files in Open Office. I'm not sure if it will let you edit them though. Try it, it might work :)

---

### Post by akudewan on 2008-06-04
You could use the command 'pdftotext'. For this you have to install a package called 'poppler-utils'

```

sudo apt-get install poppler-utils

```

---

### Post by swarup on 2008-06-04
@Kevbert: That doesn't work at all. These PDF files, at least, cannot be highlighted. They seem like they might perhaps be from books whose pages were scanned and put in PDF format. Cannot be highlighted and copied.

@django0909: That didn't work either. Just some unintelligible code comes into the OO document. I should mention that the PDF files I am trying to copy-paste from are largely in Hindi. --But I have Hindi fonts in my computer, and even when I set the OOo document to a Hindi font and then did the "open" command for the PDF file, it did not yield any text.

@akudewan: This method looks promising. The utility was actually already in my computer. When I do "pdftotext", it gives a list of all the available commands for the utility. The following ones looked like the ones I was most likely to need:

```
swarup@swarup-laptop:~$ pdftotext
pdftotext version 3.00
Copyright 1996-2004 Glyph & Cog, LLC
Usage: pdftotext [options] <PDF-file> [<text-file>]
  -f <int>          : first page to convert
  -l <int>          : last page to convert

```

So I tried it, as best I could. But it didn't work:

```
swarup@swarup-laptop:~$ pdftotext [-f <1> -f <3>] </home/swarup/ssk_vairagya.pdf> [</home/swarup/Test>]
bash: syntax error near unexpected token `1'
swarup@swarup-laptop:~$
```

Do I have the format wrong? How is the terminal command supposed to read, in order to give correct output?

---

### Post by avtolle on 2008-06-04
It looks like you type a "one" (1) rather than a lowercase L (l) when typing in the command. Try it again with the letter "l", not the number "1" (without the quotes, of course).

Edit: My error; in the terminal command you posted, the second -f should be -l, followed by the integer page number of the last page. See Mr. Pink's post below, substituting -l for the second -f he shows. Hope this correction helps.

---

### Post by Duck2006 on 2008-06-04
Double click on the pdf file so it opens in a pfd viewer. Then hi light the part that you want, then past it in what ever text file editer you have open, ie open office. Thats the way i do it, there may be an easyer way of doing it.

---

### Post by hal10000 on 2008-06-04
Just open the pdf-file (in kpdf, acrobat or another pdf-viewer), mark the text with the selection-tool (from the toolbar) and paste it with the middle mouse button into your text file

---

### Post by mister_pink on 2008-06-04
If it's scanned in from a book then this isn't going to be possible at all. The text is an image, so you'd need to do optical character recognition, which is hard enough normally, but with hindi? Unlikely.

That command though, you dont want all the funny brackets, they're just in there to show bits you can leave out and bits you need to include (no brackets.) So for example:
```
pdftotext -f 1 -f 3 /home/swarup/ssk_vairagya.pdf /home/swarup/Test
```
Although I'm not sure you can do the -f option twice, that means you have 2 first pages!

---

### Post by avtolle on 2008-06-04
Looks like the "-f 3" should be "-l 3" to create a range of pages 1 through 3.

---

### Post by hal10000 on 2008-06-04
> They seem like they might perhaps be from books whose pages were scanned

If they were scanned and then put into pdf-format, then the text you see is a graphic and can not be marked and pasted, i guess there is nothing you can do except using an ocr-software (maybe).

---

### Post by swarup on 2008-06-04
> **mister_pink said:**
> That command...you dont want all the funny brackets, they're just in there to show bits you can leave out and bits you need to include (no brackets.) So for example:
```
pdftotext -f 1 -f 3 /home/swarup/ssk_vairagya.pdf /home/swarup/Test
```
Although I'm not sure you can do the -f option twice, that means you have 2 first pages!

I do believe you've got it right. I changed the second "f" to an "l", and pasted the above code into a terminal window. And it executed. But the output in the text file is all just unintelligible characters, like this:
> 
&#134; &#137; &#153; &#137; &#147; &#145; &#147; &#145; * &#137; &#147; !gs!!!ugs! ¤!gì 

> **mister_pink said:**
> If it's scanned in from a book then this isn't going to be possible at all. The text is an image, so you'd need to do optical character recognition, which is hard enough normally, but with hindi? Unlikely.

I fear you may be correct. I am not certain what the origin of all this material is (I have around 50 PDF files of such material)-- that is, I am not certain how it was produced by those who made them. But looking at it, it just seems like it is likely from a book. So, I'm not sure what to say about this.

@Duck2006: Your method did not work at all. --This may due to the fact (my impression at least--) that this material is scanned in from a book. But at any rate, the "selection" tool did not work.

---

### Post by kaibob on 2008-06-04
> **swarup said:**
> @Kevbert: That doesn't work at all. These PDF files, at least, cannot be highlighted. They seem like they might perhaps be from books whose pages were scanned and put in PDF format. Cannot be highlighted and copied.<snip>
Some PDF document are secured against copying text or images. I rarely find that this is the case, but you may want to check just to cover all bases. In Evince, look at the document's properties.

---

### Post by t0p on 2008-06-04
Some people have stated in this thread that it's not possible to copy-and-paste text from a .pdf that was scanned from a printed book.  Well, that's certainly the case with *some* scanned .pdfs... but other scanned .pdfs can be copy-and-pasted from just fine.  You just use the mouse to  highlight the required text the same as you would a text file (or open office file).

---

### Post by Calmarius on 2011-01-05
Well I have some pdf's compiled in latex and I'm unable to select any text in them using the built in pdf viewer... Dragging the mouse does not select anything.

While in Windows' Adobe Reader selection works fine.

---

### Post by s1wood on 2011-01-05
FoxitReader - not in Ubuntu but now has a Linux download. You can copy images or text.

---

