---
title: "problem with abiword"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by the duude on 2013-08-27
My mom was working on a document in abiword and she saved and closed (something like that) and when it was opened up again it had a bunch of weird code (im assuming it's code), i think it's html.  How can I reconvert to the document.

---

### Post by sudodus on 2013-08-27
If it is html, you can try to open it with a web browser, Firefox or Chromium-Browser. If it looks good, you can save it or 'print to a pdf file' from there.

---

### Post by the duude on 2013-08-27
doesn't work.  it says xml (first word).  been trying to send it to my email but it won't for some reason so ican't post it here.

---

### Post by Impavidus on 2013-08-27
Abiword saves files in xml format. It seems that for some reason it doesn't recognise the file as abiword xml when reopening it. It may be damaged. Also, this may sound silly, but have you doublechecked it was saved and reopened both in abiword? Tried at least?

---

### Post by Dennis N on 2013-08-27
Abiword by default makes backups every 5 minutes as you work (Edit > Preferences > Documents > AutoSave). Maybe you can locate a backup of your problem file that is still good.

---

### Post by the duude on 2013-08-27
none of this worked.

[http://pastebin.com/bdUQPiCx](http://pastebin.com/bdUQPiCx)  thats what it looks like

---

### Post by Impavidus on 2013-08-28
It is an abiword file, but after line 61 (when opened in gedit or some other text editor) some lines are missing, turning it into invalid xml code. The easiest solution would be if your mom had a backup. Alternatively, open the file in a text editor (like gedit), switch on line numbers, copy lines 112-113 and paste them between lines 61 and 62, and then save the file. This makes the file readable in abiword, but still a piece is missing. If there's no backup, she'll have to write that piece again.

Things like this may happen when killing an application whilst saving a file and things like that. It shouldn't happen, but sometimes it does.

---

### Post by the duude on 2013-08-28
well, shes okay with losing the document, just has to do extra work now.  Thanks for your help now.

PS:  moved the computer to libreoffice

---

