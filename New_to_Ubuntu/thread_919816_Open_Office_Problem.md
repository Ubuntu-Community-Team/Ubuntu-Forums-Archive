---
title: "Open Office Problem"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Archie69 on 2008-09-14
Hey Guy n Gals

I'm having an issue with Open Office. 1. For some strange reason the spell check doesn't work. IS there a fix for that? and 2. Upon completion of a document, I try to send it to others (I'm a student) who obviously use Windows or OSX and they can't open the ODT file. I then tried to change it to a .doc file, but the same problem for the receiving end.

Are there any fixes to these problems? Please Help

---

### Post by pyromanic123boom on 2008-09-14
For the spell checker, you might possibly need a plugin or extension. Mine works fine and all I did was install OpenOffice from the terminal.

The file extension - don't just change the file to a .doc, when you save it in Open Office, make sure you select MS Word Document File from the file options. Then it will save into the .doc format.

---

### Post by kk0sse54 on 2008-09-14
Try not to post twice in two different sub forums mate. But as for your problem can you specify what exactly isn't working with spell check or is just all out refusing to start? As for sending a document it depends on what version Microsoft Office they are running since Microsoft office 2007 uses a different format than previous versions.

---

### Post by howefield on 2008-09-14
Open /usr/share/myspell/dicts/DicOOo.sxw in writer, scroll down to your language, and follow the instructions.

As for the doc, there are a few different doc formats you can save in depending on the version of office your friends have, you need to save in one compatible with their version.

---

### Post by R_T_H on 2008-09-14
> **C!oud said:**
> Try not to post twice in two different sub forums mate. But as for your problem can you specify what exactly isn't working with spell check or is just all out refusing to start? As for sending a document it depends on what version Microsoft Office they are running since Microsoft office 2007 uses a different format than previous versions.

No, an old style .doc would be okay. Word 2007 can run in "Compatability mode"

---

### Post by kk0sse54 on 2008-09-14
> **R_T_H said:**
> No, an old style .doc would be okay. Word 2007 can run in "Compatability mode"
The same goes for the old word I believe or at least you have to install something to make it work but this is still a huge problem especially in my school because it still just doesn't always work and all the sudden your 1000 word essay becomes a day late and you get a zero.

---

### Post by Archie69 on 2008-09-14
Just saving the document as a word file seems to work fine.  Thanks.  As for the spell check still no dice.  I tried adding Dictionaries but nothing.  Maybe re-installing Open office would work? Or is there an easier solution?  Like the first reply said, maybe a plugin?

---

### Post by R_T_H on 2008-09-14
> **Archie69 said:**
> Just saving the document as a word file seems to work fine.  Thanks.  As for the spell check still no dice.  I tried adding Dictionaries but nothing.  Maybe re-installing Open office would work? Or is there an easier solution?  Like the first reply said, maybe a plugin?

In synaptics are there not language support packs? I think it is by installing these that one gets dictionaries. I'm sorry, but I can't remember much more than that.

---

### Post by Miljet on 2008-09-14
Just a thought, but have you went to tools->options->language settings->writing aids to see if spell check is turned off? It should be on by default when installed, but who knows.

---

### Post by fballem on 2008-09-14
> **R_T_H said:**
> In synaptics are there not language support packs? I think it is by installing these that one gets dictionaries. I'm sorry, but I can't remember much more than that.

It's a little more complicated than that, unfortunately. I am attaching a screenshot. To get here, please open OpenOffice Writer to a blank document. Select Tools | Options. Then open up the panel as shown in the screenshot.

You will see in the screenshot that there are some languages with a checkmark and 'ABC' beside them. These languages have a dictionary. If you select one of these, then the dictionary should work. If you select a language, such as English Canada, then there will not be a spell check, since there is no dictionary.

Thanks for your question, by the way. Now I need to find out how to make a dictionary for Canadian English.

---

### Post by Sef on 2008-09-14
> 1. For some strange reason the spell check doesn't work. IS there a fix for that? and 2. Upon completion of a document, I try to send it to others (I'm a student) who obviously use Windows or OSX and they can't open the ODT file. I then tried to change it to a .doc file, but the same problem for the receiving end.

1. Check with [Open Office]("http://openoffice.org") site too.

2.  Sun has [plugin]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=ODF-WIN-G-F@CDS-CDS_SMI") which will open ODT documents in msword. (It is posted somewhere here.  

3) Do not post a problem in more than one forum.  Thank you.

---

### Post by fballem on 2008-09-14
It would be helpful if the Original Poster would identify the language that is associated with the document. When you open a new document in Writer, could you please tell us what language is shown in the status bar at the bottom of the document

Thanks,

---

