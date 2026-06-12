---
title: "LibreOffice compatibility?"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by mrronoah on 2013-05-31
I have been enjoying using ubuntu for 12 months or so but I have been switching over to Windows to use Microsoft Office (and a few other specialized applications). I use Word, Excel and Powerpoint virtually everyday and I am wondering if the libreOffice are completely compatible. Any incompatibilities in particular that I should know about?
From what I have seen it looks pretty good but I don't want to waste my time making documents that aren't compatible when I email it to someone with office. Is it compatible with all versions of Microsoft Office?
Thanks :)

---

### Post by Impavidus on 2013-05-31
No, it's not completely compatible.
Compatibility with older MS office versions is generally better than with recent versions. Simple things nearly always work, like text in writer/word or numbers in calc/excel, but adding graphics makes things more complicated. Impress/powerpoint often gives trouble. The only way to be sure is testing it.
The reason is that it's pretty hard for the LO people to reverse-engineer MS office file formats, which change with every new version, and at the same time MS doesn't bother supporting LO formats, even though it's an open format. Why provide compatibility with your competitor?

Alternative ways of fixing the problem:
– Run an old MS office in wine. New ones don't work well. You won't be able to open MS office files saved on a recent MS office.
– Export to PDF if you don't need to edit it any more. PDF opens well on all computers.
– Ask the other people to install libreoffice too. It's free and runs on windows machines.

---

### Post by 3rdalbum on 2013-05-31
It's not 100% compatible, but the formatting might sometimes look a little off. You can't expect 100% compatibility with basically a closed file format like Microsoft Office formats.

You could encourage your friends or clients to use Libreoffice, or run Windows and MS Office in a virtual machine, using Ubuntu for everything else. Or dual boot.

---

### Post by MirrorUniverse on 2013-05-31
Maybe OpenOffice could help with this?  [http://www.openoffice.org/](http://www.openoffice.org/)

edit: it says it is not 100% compatible either, but may be worth trying.

---

### Post by mrronoah on 2013-05-31
I hate wine! its so buggy, cant stand it. I think I might try LibreOffice for a while and see how I go. I don't use graphs, charts, smartart or stuff like that too often but if I need to I could just boot into Windows and add it in. Yes, I am dual booting Windows and Ubuntu currently but it is a pain to have to boot back into windows every half an hour just to use office.

I am a student (which is my main use of MSoffice) and my teachers aren't really IT savvy so there is no way they would vm and I doubt they would appreciate having to download software just to read my work. Exporting as pdf is definitely plausible if the document isn't compatible with office.
Anyway thanks for the info guys.

---

### Post by newb85 on 2013-05-31
> **MirrorUniverse said:**
> Maybe OpenOffice could help with this?  [http://www.openoffice.org/](http://www.openoffice.org/)

edit: it says it is not 100% compatible either, but may be worth trying.

I wouldn't expect OpenOffice to be any better.  LibreOffice is (basically) a fork of OpenOffice started by several developers who left OpenOffice when its owner was restraining development.

---

### Post by Mark Phelps on 2013-05-31
The main incompatibilities are going to be with the "new" xml format MS Office documents -- .docx, .xlsx -- which have been the defaults formats since Office 2007 came out.  IF folks interchange those files, there will be problems with compatibility between LO/OO and MS Office.

---

### Post by rvergara on 2013-05-31
Mrroanah,

I use LibreOffice intensively. I just export to PDF  to send documents to others. When receiving documents, I would say i can read above 95% of them using LibreOffice (i just disregard a few format changes), however a few documents are unreadable (5% or less), in those cases I use MS Office on PlayonLinux which is an enhanced version of wine.

Hope it helps

---

