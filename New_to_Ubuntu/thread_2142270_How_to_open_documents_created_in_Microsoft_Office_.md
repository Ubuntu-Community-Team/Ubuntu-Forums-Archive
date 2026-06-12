---
title: "How to open documents created in Microsoft Office 2010 ?"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by Majkos on 2013-05-05
Hello ,

How can I open documents from Microsoft Office 2010 such as PowerPoint or Word in ubuntu ? I know I can save it in compatible format which is 2007 and open it in LibreOffice but that method with multiple files becomes pointless. Is there any way I can open documents straight away without saving it in compatible format ? I tried to open it in LibreOffice but I think that program don't support documents from office 2010. 

Thanks
Every help is appreciated

---

### Post by Shadius on 2013-05-05
I've had no problems opening up MS Office documents in LibreOffice. What format was the document you tried to open in? I believe the document will open just fine in LibreOffice Writer if the format is *.doc* and/or *.docx* for MS Word and *.ppt*, *.pps*, and *.pptx* formats will open in LibreOffice Impress for MS PowerPoint.

---

### Post by fantab on 2013-05-05
You can use Microsof account if you have one or create one to access SKYDRIVE, which offers Word and Powerpoint online versions and also a free 20GB space. 

If you want to use those documents in Libreoffice then I don't think you have an alternative but to save those in a 'compatible format' for use in Libreoffice. .docx will have formatiing errors in Libreoffice, but you can open those.

---

### Post by Majkos on 2013-05-05
That is strange because I tried to open .docx or XML documents which is new format in office 2010 I think and it's don't allow me saying that the format it's not appropriate. What version of LibreOffice you guys use ?

P.S Very fast reply xD

---

### Post by fantab on 2013-05-05
I don't use MS office anymore All the old docments I had, I gradually converted them to .odt. If i have to share my documents with MS office users then I use Skydrive. By the way, I am using Libreoffice 4. Yes there is problem with newer .docx files they sometimes open but sometimes they don't. Forget Libreoffice older MS versions have problems opening newer .docx files with correct formattig and all.

If you have only read those documents then consider converting them to .pdf.

---

### Post by Majkos on 2013-05-05
In the mean time I was thinking is there any online service which convert many files in one go from .docx to .doc ? Previously about few months ago I tried few but they failed , I have like 30 documents which I need to open and edit and they are saved in MS Office 2010. Currently I don't have access to machine with Office :/ so I think I'm in black hole ...

---

### Post by MrSteve on 2013-05-05
open the properties of a document and ensure that the .doc is at the end of the line
'document name'.doc
save in a different location and then try opening in libre ...

---

### Post by fantab on 2013-05-05
> **Majkos said:**
> In the mean time I was thinking is there any online service which convert many files in one go from .docx to .doc ? Previously about few months ago I tried few but they failed , I have like 30 documents which I need to open and edit and they are saved in MS Office 2010. Currently I don't have access to machine with Office :/ so I think I'm in black hole ...

Use microsoft online apps like Word, Powerpoint etc, with Skydrive.

---

### Post by atm123 on 2013-05-05
why dont you try running msoffice with WINE.. that might help.

---

### Post by dave2001 on 2013-05-05
I've not had any problems with compatibility and Libre Office 4, however, I'm still basing that off of MS Office 2007 & 2003 documents, as I don't have (and will not be using if I can help it) MS Office 2010.

My suggestion would be to give the latest version of Open Office a try, it's a very similar program from which Libre Office forked, but it is still kept up-to-date and may not have the same issues. Here's a link for the Deb install file [http://www.openoffice.org/download/](http://www.openoffice.org/download/)  it should auto-detect your system and give you the right version.
 
Let us know what ends up working for you, compatibilty with MS is a question that comes up a lot.

---

### Post by HermanAB on 2013-05-05
The best solution is Codeweavers Crossover and Ms Office 2010. I use it every day at work.

---

### Post by Majkos on 2013-05-11
I just install wine and trial version of Office 2010 and it's working perfectly for me.

Thanks for help
Majkos

---

### Post by nsync on 2013-05-11
cant you try renaming the extension of the file to make the file supported by ubuntu?

---

### Post by llamabr on 2013-05-11
> **atm123 said:**
> why dont you try running msoffice with WINE.. that might help.

Wine is very rarely the correct solution.  In addition, the OP would need to own a copy of MS Office to do so.

---

### Post by Mark Phelps on 2013-05-11
> **nsync said:**
> cant you try renaming the extension of the file to make the file supported by ubuntu?

NO -- the .docx extension is a different FORMAT than the old .doc extension. It MIGHT work, but most likely, it will not.

---

