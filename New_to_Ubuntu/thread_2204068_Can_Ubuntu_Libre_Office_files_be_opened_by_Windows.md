---
title: "Can Ubuntu Libre Office files be opened by Windows?"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-02-06
[SIZE=3]I have just started using Ubuntu and I like it. I have a concern, however, that has caused me to consider trying to dual boot Ubuntu and Windows. 

THE CONCERN: I used a form of Linux (Fedora 14) for almost three years and some Windows users that I sent  Open Office (odt) files to (attached to email) could not open the files. Even if I converted the Open Office files to MS Word files people often still could not open the files. 

QUESTION: Can Ubuntu Libre Office files (Writer, Calc, Impress) be opened by Windows users?

Is this a problem that I should be concerned about?

Thanks,

R.
[/SIZE]

---

### Post by monkeybrain20122 on 2014-02-06
Recent versions of MSO are supposed to be able to open odt. Tell your contacts to 1) upgrade their MSO or 2) File a bug against MSO, or 3) Install LibreOffice.

This is a bit facetious, LO is supposed to be able to save to MS formats, but  reversed engineering against a moving target is never going to be a 100% reliable. So, seriously, the only sure fire way to fix this compatibility problem is to stop using MS's closed formats.

---

### Post by tripp98 on 2014-02-06
you have 2 options.  Libreoffice runs on windows as well.  They can open od files direction.  you can change how you save the files.  save as a .doc or xls file will work great.  the newer format .docx or xlsx format is not so friendly.

---

### Post by AbleTassie on 2014-02-06
I think it was docx files that they could not open.

Thanks,

R.

---

### Post by Vladlenin5000 on 2014-02-06
> **RMcGinnis said:**
> I think it was docx files that they could not open.


Therefore they probably have an old version of Microsoft Word... Just save as .doc and it should be fine. However, I must insist on what other already commented: The best way to avoid compatibilty issues with proprietary formats is NOT using them. Period.

---

### Post by monkeybrain20122 on 2014-02-06
> **RMcGinnis said:**
> I think it was docx files that they could not open.

Thanks,

R.

Sure it can, unless the file has very complicated formatting with a lot of embedded contents. If it is a simple document in .docx LibreOffice can certainly open it and save to it. But I would avoid using MS's closed formats as much as possible.

---

### Post by AbleTassie on 2014-02-06
[SIZE=3]Thanks to everybody --- of course most people with whom I associate will be using MS Word, Excel, & Powerpoint into the near future. So it's important to know if they will be able to open files I generate using Ubuntu's Libre Office. Nobody specifically mentioned Libre Office Impress, which is the counterpart for MS Powerpoint. I notice that Libre Office Impress documents can be saved as MS Powerpoint files. 

QUESTION: Does the saving of Libre Office Impress documents as MS Powerpoint files allow Windows users to open/use these Impress/Powerpoint files? Or are there some problems with this as well?

I looked up "closed formats" and I understand the problems with them & MS, reverse engineering and compatibility. 

Thanks,

R.
[/SIZE]

---

### Post by Vladlenin5000 on 2014-02-06
Yes, of course.

---

### Post by Mark Phelps on 2014-02-06
All this evangelizing about opens-source is entertaining -- but doesn't answer your question > Is this a problem that I should be concerned about?

And unfortunately, the answer is YES.  

The one product that works reliably with MS Office files is -- MS Office -- and that's not going to get better anytime soon.

Even if you do save your documents as '.doc' files, presuming the other folks are using an Office version of 2007 or newer, as soon as they open your file and save it, it gets converted to a "docx" file -- and you're back where you started.

I can still remember working at places where we used WordPerfect for documents, Lotus 1-2-3 for spreadsheets, and CC:mail for email -- but that was before MS took over nearly all of the general office infrastructures to replace those products with Word, Excel, and Outlook. Lots of our folks complained bitterly when the products we used were taken out and MS Office was brought it.

The unfortunate fact of working with a group is that, if compatibility is an issue, then you're obligated to use the same tools as the rest of the group.  They're not going to switch over to using something else simply because YOU don't want to use the same tool they're using.

---

### Post by oldrocker99 on 2014-02-06
My brother in law, a Windows user, complained that he'd been sent an .odt file which Office wouldn't open. I said to him that the problem was not with the program that **created** the file, but with the expensive program (which can open WordPerfect files, for crying out loud) that **refuses** to open the file. I also said that it would do his PC no harm to install LibreOffice...

---

### Post by monkeybrain20122 on 2014-02-06
Well why don't you start using it first and see if it meets your needs if you already have Ubuntu? (LO can be installed in Windows as well)

 I have never had problem opening .docx, .pptx, .xslx etc with LO, but then I have never had to deal with very complex documents (and most people don't) It is hard to give generic answer not knowing the kind of documents you handle but my general answer is that "normally" LO is just fine, but if your documents are not so conventional then you may encounter some problems. 

I say just do it (never mind the nay sayers, they may be dealing with technicolour documents in .docx with little people dancing with rainbow coloured unicorns and run into problems but chances are you're not :)) If it doesn't work post a new thread for installing MSO in wine or something.

---

### Post by AbleTassie on 2014-02-07
[SIZE=3]Sometimes I resend an Open Office (odt) file that cannot be opened as a pdf document. Occasionally I want to encrypt an odt file and I have had the recipient complain they cannot open it in MS Word. And I don't have the software to encrypt a pdf document. So I have to forget the encryption in that case. 

So if I do want to send encrypted files, unless somebody knows of a work around in Ubuntu, I guess I'll have to dual boot. The only other alternative is to ask people to install Libre Office--which is not a bad alternative.

Any more comments would be welcomed.

Thanks,

R.  
[/SIZE]

---

### Post by spjackson on 2014-02-07
> **RMcGinnis said:**
> [SIZE=3]Sometimes I resend an Open Office (odt) file that cannot be opened as a pdf document. Occasionally I want to encrypt an odt file and I have had the recipient complain they cannot open it in MS Word. And I don't have the software to encrypt a pdf document. So I have to forget the encryption in that case. 

So if I do want to send encrypted files, unless somebody knows of a work around in Ubuntu, I guess I'll have to dual boot. The only other alternative is to ask people to install Libre Office--which is not a bad alternative.

Any more comments would be welcomed.

Thanks,

R.  
[/SIZE]
I use Libre Office (and formerly Open Office). If I only expect the recipient to read or print the document, then I always send as PDF. I have never had a case where the PDF could not be read. Perhaps your recipients are using a very old PDF reader?

I have used both [PDFBox]("http://pdfbox.apache.org/") and [PDFtk]("http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/") on Linux to take an unencrypted PDF and encrypt it, although I have only used them a little and for testing purposes.

When I'm collaborating with someone else, I will save as .doc (not .docx) and send that. I haven't had a problem with the .doc being unreadable, although appearance can be an issue (especially frames and custom bullets).

---

### Post by Gaweph on 2014-02-07
I have some recent experience with this, an the answer is "yes and no".  I was working on a document that needed images adding by another member of the team.  So I did my sections and then put it into our shared dropbox folder (file at this point was saved as **odt** via libreoffice).

He then added his sections (images and soem text) and told me it was done.

When I went to open it all seems ok, until I looked closelly.  Some of the formatting to the H1,H2,H3 was different, and there were slight variances from the way it was originally saved.

So I would say, it should open fine with newer versions of office, however it may not look exactly the way you saved it to the other users (if this is a problem then saving to **pdf** is your best option.

---

### Post by rsgangr on 2014-02-07
I have found that sometimes MS Word will not open a *.doc created in LO but it will open the same document cleanly if it is saved as *.rtf, i.e. Rich Text Format. Perhaps this might resolve your Word issue? Unfortunately I cannot comment on the issue of presentations.

---

### Post by AbleTassie on 2014-02-07
[QUOTE=spjackson;12922271]I use Libre Office (and formerly Open Office). If I only expect the recipient to read or print the document, then I always send as PDF. I have never had a case where the PDF could not be read. Perhaps your recipients are using a very old PDF reader?

SPJackson,
[SIZE=3]
My first sentence in the post you responded to can be interpreted in two ways and  you did not interpret it in the way I intended. Actually what I mean to  say is that I do the same as you do: I send documents as PDF if the  recipient is having trouble opening an odt file. But I cannot encrypt a pdf file with the software I have; and sometimes I want to encrypt the file. [/SIZE]
[SIZE=3]
There is free software that can be used to create pdf files with passwords. But the version I found does not work with Linux.[/SIZE][SIZE=3]

QUESTION: Does anybody know of a pdf file creator freeware that works with Linux that can password protect the pdf?

Thanks,

R.[/SIZE]

---

### Post by AbleTassie on 2014-02-07
[SIZE=3]QUESTION: Does anybody know of a pdf file creator freeware that works with Linux that can password protect the pdf?

Thanks,

R.[/SIZE][/QUOTE]
[SIZE=4][COLOR=#0000ff]
**I answered my own question. The pdf export function in Ubuntu allows password encryption of pdfs. **[/COLOR][B]:)[COLOR=#0000ff]

Thanks,

R.[/COLOR][/B][/SIZE]

---

### Post by AbleTassie on 2014-02-07
A great big thank you to everybody for their responses. I have saved the responses for future reference as well.

R.

---

### Post by kurt18947 on 2014-02-07
This is hearsay - I have no first-hand experience so take this for what it costs you:p.  I've read that upon receiving a MS document, open it then save it as an .odt file.  Edit as required, save then save in MSO format and send.  Supposedly this does a better job of  maintaining format than editing the 'native' MSO document.  On a somewhat related note, I read where the UK gov't is trying to encourage the use of open document file formats in lieu of MSO file formats.  If there were pressure on Microsoft to support rather than sabotage Open Document standards, it might help matters.  I suspect it might be easier to convince a Tiger to become a vegetarian though.

---

### Post by AbleTassie on 2014-02-10
Thanks Kurt.

RM

---

