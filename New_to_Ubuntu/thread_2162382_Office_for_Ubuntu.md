---
title: "Office for Ubuntu"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by Williamwilson on 2013-07-14
Hi

I am a Microsoft user particulary I use Microsoft Word. I would like to change to Ubuntu since I am tired to pay for the license of Microsoft. 

I have two main problems:

1) I write often in semitic languages from right to left. Does the Ubuntu Office support this?

2) Is Ubuntu Office able to convert file from word to pdf?

3) Suppose I write a file in Ubuntu's Office and transform it into a *pdf file to send it to a Microsoft user. Are the Microsoft word user able to read it or the file may be corrupted? 

These are my main problems to decide whether to install Ubunt.

Thanks anyone who could help me.

Regards

WW

---

### Post by grahammechanical on 2013-07-14
We do not have a Ubuntu Office. We have LibreOffice and that has several components, Writer (word processor), Calc (speadsheet), Impress (presentations), Base, (database). LibreOffice is much more compatible with Microsoft Office, than the other way around.

May I make a suggestion? You can go here

[http://www.libreoffice.org/download/?nodetect](http://www.libreoffice.org/download/?nodetect)

and download a Windows version of LibreOffice and run these experiments yourself.

I have found that LibreOffice will open Microsoft doc files. I have also found that it is best to copy the contents into a new Writer document than to try to convert. Libreoffice documents have much smaller file sizes than Microsoft documents.

We can export to PDF. The fonts are embedded. So, the PDF document should open in any application that reads PDF. 

When we install Ubuntu we get an option to also install third party software and that software will include an installer of Microsoft true type core fonts. We need to accept the licence for that action to complete. So, unless you are using Microsoft fonts outside of the core font set you should have no difficulty reading Word documents in Libreoffice.

It is also possible to install something called wine and with that we can run some Windows programs. May be you could run Word in this way. See, if it is in the database lists of Windows programs. See how well it works under wine.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Oh, also we can install different keyboard layouts. I have English and Greek and switching is just 2 clicks away. And there is a long list of different language keyboard layouts available. I see 10 Arabic layouts and 4 Hebrew layouts.

Regards.

---

### Post by 1clue on 2013-07-14
I never had much luck with wine and Microsoft Office, but reportedly crossover office (a commercial product based on wine with the addition of some commercial dll's) allows you to use Microsoft Office just fine.

I think that's not really what you want, because you still have to pay for Office and then you have to pay for the crossover license too.

Here's a database for Crossover Office, that might help you:
[http://www.codeweavers.com/compatibility/search?name=Microsoft+Office&search=app](http://www.codeweavers.com/compatibility/search?name=Microsoft+Office&search=app)

And the equivalent for wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10)

Note that I couldn't just search on Microsoft Office there, had to go specifically for Word.

As for the features of word working in Linux, or features of Libre products matching with what you want in Microsoft, that's a bigger question and I doubt anyone is going to answer it for you.  I've never even seen right-to-left except in a demo video, and most of the rating systems are based on user input for what the user submitting a rating uses.

I second grahammechanical's suggestion of loading Libre on your Windows box, and then after that maybe install a virtual machine with Ubuntu on it, add your languages and such, and then test it for yourself.  It's really not hard to do.

---

### Post by perspectoff on 2013-07-14
Libre Office is a fork of Open Office, and I had few problems going back and forth to/from MS Office documents. Having said that, there are sometimes subtle formatting differences that I had to tweak.

Of course, the same difference exists between different versions of MS Office, too!

I ran my office for years on MS Office, but finally made the switch to OpenOffice on all computers (both Windows and Linux). No worries after the mandatory tweaks. (There is virtually no difference between LibreOffice docs and OpenOffice docs).

I do LOTS of documents in PDF format, and there is (still) no PDF manipulator as good as Paperport 9 in Windows (not even later versions of Paperport). Still, there are a good number of PDF file manipulators for (K)Ubuntu Linux, and printing to a PDF document is installed BY DEFAULT in all versions of (K)Ubuntu Precise (12.04) or later.

I have a list of PDF (and other office) utilities at

[http://ubuntuguide.org/wiki/Ubuntu_Precise_Office](http://ubuntuguide.org/wiki/Ubuntu_Precise_Office)

and

[http://ubuntuguide.org/wiki/Kubuntu_Precise_Office](http://ubuntuguide.org/wiki/Kubuntu_Precise_Office)

PS I still maintain that Kubuntu is much easier for prior Windows users...

PPS The only thing I ever do in Wine is Netflix, and then in a modified version of Wine that comes as an integrated package (thanks Erich Hoover!). Though it sounds attractive, Wine is (otherwise) a waste of time and effort, IMO, and I have never been unable to find (apart from Netflix) an app in Linux that works equivalent to, if not often better than, the Windows app. 

Apple went to BSD (a variety of Linux) long ago and for years Windows has slowly been adopting (bit by bit in that elephantine MS way) the same OS structure. Google Android, of course, is Linux. Ubuntu/Debian servers account for > 57% of all Linux servers, and Linux servers are nearly 2/3 of all servers worldwide (the rest being Windows servers). Most (distributed-)supercomputers run Linux.

With that much of computing attention worldwide focused on Linux, why stick to a Windows-model, which is starting to look quaint and antiquated?

---

### Post by Williamwilson on 2013-07-14
Hi 

 thank you for your kindness.

I think that I will pick up the suggestion of Grahammechanical and test if the LibreOffice meets my needs.[B][COLOR=#000000]
Regards

WW[/COLOR][/B]

---

### Post by monkeybrain2012 on 2013-07-14
You can make LO start a lot faster with the following tweak. Open any LO component (say writer), go to Tools > Options. When a window opens, on the side pane choose Libreoffice > Memory and set 
number of steps = 30
graphics cache 
use for Libreoffice = 120MB
memory per object = 20.0MB
cache for inserted objects
number of objects=20

You can also enable the tray icon for quick start, but if you use Unity in Ubuntu 13.04 the tray icon may not show up on the top panel without changing some settings.

---

