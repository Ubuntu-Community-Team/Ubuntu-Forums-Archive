---
title: "Ubuntu in mainstream -"
date: 2012-02-04
forum: Recurring Discussions
---

### Post by landersohn on 2012-02-04
The last thread I found about ubuntu going mainstream is a bit old, so I thought I post some thoughts.
I have been using ubuntu running my business for 18 months now. I think it's far better than anything else out there especially Windows. Having said that, I think there are a couple of barriers which prevent ubuntu from getting broader acceptance in a professional environment. I know some readers will not like to hear this, but windows is a fact of life right now and if we as ubuntu community desire to become more used, we need to fix intraoperability issues with Windows. Overall it's kind of OK (if you are willing to spend a few hours to make it work) but three real show stoppers for use in a professional setting exist:
1) windows DOC, PPT and XLS compatibility is weak. There are lots of glitches (disappearing references, Windows users can not edit header/footer unless the TOC in openoffice is made editable, automatic row height in spreadsheet doesn't work after saving and loading a DOC file, stuff like that). Of course there are workarounds (like PDF) but those are not always acceptable by the other people one has to deal with professionally
2) the LDIF support in evolution - to use a nice phrase - sucks. It can not read ANY of the exported LDIF files I tried, especially not Outlook. Addresses and phone numbers get garbled. This is a major hurdle for any professional to switch to ubuntu. I solved it by editing the LDIF file and renaming fields to what evolution expects, not something an ordinary user is likely to wanting to do.
3) the support reading DOCX, XLSX and PPTX is poor: a lot is ill formatted and writing these formats is even worse. I am sure there are good technical reasons for it, but from a user perspective it's a bug problem.

There's a few more (like no good equivalent to MS Project, one of the programs Microsoft actually got right).

When posting some of this as problem, I got replies like "too bad if Microsoft can't read OpenOffice exported DOC files". While I certainly understand the sentiment, this attitude is not going to help getting more people to use ubuntu. If we as a community want to stay a small exclusive club, that's OK.
I would like to see it used more (if nothing else to take Microsoft's market share), so I was disappointed about this attitude. I don't like it but the fact is, we need to cater to Windows users to ever have a chance to grow our user base.

---

### Post by 3Miro on 2012-02-04
Try moving documents between MS Office for Mac and MS Office for Windows to see how compatible those are. MS is unable to make software compatible with their own software, it is a miracle that Libre Office works as good as it does.

It is one thing to have support for open formats (see .pdf support which is excelent under Ubuntu), it is another thing to try and reverse engineer MS closed proprietary formats when MS themselves don't want you to do that. The problem here is not with the Linux community or lack of willingness and effort.

Think of it this way: When you save a file under a proprietary format (i.e. docx), then every time you want to open the file, you need to get permission from MS. For all practical purposes, they own your files and your data. This is the real problem.

---

### Post by JayKay3OOO on 2012-02-04
I recently fixed a clients document problems using Libreoffice. MS office turned all the files into garbage (they were doc/docx files) but libreoffice saved my *** and their butt (on windows 7) and displayed the files perfectly. They were planning on throwing away their printer that they thought was broken! Not to mention that years of work were un-readable. Crisis.

Another win for the open community then.

Meh, .odt and libreoffice on everything it'll run on for near seamless interaction between systems and .pdf if you want to share in the most universal way. MS office slightly better overall, but not better enough to justify the price.

Bleh am I paying for that. .odt is pretty well recognised. I know several programs that can read it where I used to run into soo many problems when sharing doc and docx.  

My compromise is to use Windows 7 on my laptop and use all OSS on it. I'm not paying for software when OSS meets my needs and I'm not illegally downloading closed software because if I need it, then the price is justifiable. Too many people think they need MS office, but I think too many people are throwing their money out the window.

Ubuntu fine for tasks like e-mail, basic photo ed, basic video ed, listening to music (amarok is as a player nicer than wmp), browsing the net, watching HD video streaming or TV catchup. Most school and uni work, programming, editing audio and browsing the web.

---

### Post by loell on 2012-02-04
> **landersohn said:**
>  While I certainly understand the sentiment, this attitude is not going to help getting more people to use ubuntu. 

There's no amount of healthy positive attitude can ever make those closed proprietary formats play nice.

this is same old same old, so I have move this thread to Recurring discussions.

---

### Post by Copper Bezel on 2012-02-04
[QUOTE=3Miro]Think of it this way: When you save a file under a proprietary format (i.e. docx), then every time you want to open the file, you need to get permission from MS. For all practical purposes, they own your files and your data. This is the real problem.[/QUOTE]
I don't understand how this applies to .docx, so maybe you can clarify this for me. The Office XML formats are ISO-published standards and established under the patent equivalent of copyleft. They were a response to Open Office's similar standards published a year before (on IBM's rather than MS's coin) and they work the same way: a .zip archive full of XML data. They differ in terms of security provisions and comment markup, but they're not fundamentally different approaches to the problem, and they're both designed to prevent the problems of the closed, binary .doc, .xls, and .ppt that they replaced.

So what's the difference between IBM's and MS's ISO-published, XML-based office-document format families?

---

