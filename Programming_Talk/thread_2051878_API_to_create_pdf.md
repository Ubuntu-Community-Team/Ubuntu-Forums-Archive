---
title: "API to create pdf"
date: 2012-09-02
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-02
Hi,
Is there any API in linux to convert a text document to a pdf.
I was looking for something like
CreatePdf(DestinationPath, SourcePathOfTextDocument);

Thanks.

---

### Post by ofnuts on 2012-09-03
> **IAMTubby said:**
> Hi,
Is there any API in linux to convert a text document to a pdf.
I was looking for something like
CreatePdf(DestinationPath, SourcePathOfTextDocument);

Thanks.They way you define it (Input file->output file) what you are looking for isn't really an API but some format conversion command. 

The format of the "text document" should be defined? Is that just a flat file?

Ghostscript can convert Postscript to PDF, and flat text can be wrapped in some base postscript..

---

### Post by conradin on 2012-09-06
You could print a text file to pdf. Formatting options is what i assume you want. in which case I would do text -> postscript -> pdf.
where in postscript you could do all sorts of formatting, and have it convert easily to pdf.
heres a nice pdf on PS formatting
[http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&ved=0CDYQFjAD&url=http%3A%2F%2Fpartners.adobe.com%2Fpublic%2Fdeveloper%2Fen%2Fps%2F5003.PPD_Spec_v4.3.pdf&ei=aWJJUI7eLYTc0QHKn4DwBQ&usg=AFQjCNFDvhk_1iVUaBJY50lYqaVVT1-F-A&cad=rja](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&ved=0CDYQFjAD&url=http%3A%2F%2Fpartners.adobe.com%2Fpublic%2Fdeveloper%2Fen%2Fps%2F5003.PPD_Spec_v4.3.pdf&ei=aWJJUI7eLYTc0QHKn4DwBQ&usg=AFQjCNFDvhk_1iVUaBJY50lYqaVVT1-F-A&cad=rja)

---

### Post by kalaharix on 2012-09-07
I have used a combination of htmldoc and psutils to do this to create a clickbook type utility in Gambas.

htmldoc is designed to turn html into ps or pdf but I had quality problems with the pdf so I used htmldoc to turn the text files into postscript and then ps2pdf to turn to pdf. Other psutils utilities paged it, turned it sideways and collated it like clickbook. The quality is very good: probably better than clickbook.

---

### Post by IAMTubby on 2012-09-07
ofnuts, conradin, kalaharix.
Thanks a lot for your replies.

I'm currently stuck up with something. Can I try out the things you mentioned and get back to you tomorrow.

Thanks once again,
Truly appreciate.
Shall get back tomorrow.

---

