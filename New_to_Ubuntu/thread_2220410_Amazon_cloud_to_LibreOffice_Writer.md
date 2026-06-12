---
title: "Amazon cloud to LibreOffice Writer"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by Ron_Callison on 2014-04-27
OK guys, I'm trying to figure Linux out.  I really like the speed and Internet access but I've hit a wall on word processing.  

I have used WordPerfect under Windows for the past 30 years.  In my readings around here it looks like I can't continue with WordPerfect.  Rats!  I would rather continue to use all of my WordPerfect documents as is but I have resigned myself to starting over again and re-creating the ones I use all the time in LibreOffice Writer.  If anyone can suggest a way to use my WordPerfect docs under Linux I would appreciate that.  However, if not, then how can I access my Amazon Cloud Drive (where the docs are located) from LibreOffice Writer and open them in LibreOffice.  I did open one document but the format was all wrong and I had to fix it.  I'm prepared to do this to the docs I use all the time but it was awkward getting the doc into LibreOffice Writer.  I would really like a quick link to the cloud to access my docs from LibreOffice so I can fix them and then save them in LibreOffice.  Help!

Ron

---

### Post by pfeiffep on 2014-04-27
Maybe stating the obvious here - export the documents from Word Perfect to a compatible format [or open them in LO]("http://ask.libreoffice.org/en/question/17246/wordperfect-and-current-libreoffice/"). 
Can you not simply download the files to a local storage medium and then open them?

---

### Post by amanchesterman on 2014-04-28
I think you may be asking two questions here. One is how to open and edit WordPerfect documents with LibreOffice Writer. I've never tried it (I haven't used WP for many years) but pfeiffep has suggested two ways to do it in the previous post. As you have found, Writer doesn't always reproduce formatting faithfully when documents have been created by other programs. To avoid that problem in the future, make sure that you save the new versions of your documents in Writer's 'native' open document format.

The other question is how to set up a quick link so that when you click the 'open document' dialog in Writer your Amazon Cloud shows up as a folder or directory that you can access directly. Frankly, I don't know if you can. I had a quick look at the Amazon website and they don't offer support for Linux, so it looks like you have chosen to use a cloud storage service that isn't compatible. There may be a work-around but I don't know what it is. However there are several cloud storage services that are compatible and they will integrate with the Ubuntu file manager. But if you want to stick with Amazon, you may have to download the documents to your machine before you can edit them, as pfeiffep says.

---

### Post by Ron_Callison on 2014-04-28
Excellent reply.  Thanks.  Can you recommend a Linux-compatible cloud service?

---

### Post by pfeiffep on 2014-04-28
Not certain if Google Drive qualifies as "Cloud Service" but it's served my needs just great!

---

### Post by Ron_Callison on 2014-04-28
OK, I already have Google Drive.  Now how do I "integrate with the Ubuntu file manager"?

---

### Post by pfeiffep on 2014-04-28
I don't - but your question prompted me to explore a bit ...[INDENT][http://www.omgubuntu.co.uk/2012/08/insync-brings-google-drive-to-ubuntu](http://www.omgubuntu.co.uk/2012/08/insync-brings-google-drive-to-ubuntu)

[http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools](http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools)
[URL="https://apps.ubuntu.com/cat/applications/raring/unity-scope-gdrive/"]
https://apps.ubuntu.com/cat/applications/raring/unity-scope-gdrive/[/URL][/INDENT]

---

### Post by pfeiffep on 2014-04-28
I decided to try [grive]("http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools") - installs ok, appears to be a one way operation - pc to google drive....I haven't seen the document that I created with Google Docs pulled down to my pc.

from the sync log 
```
document "Grive on web" is a google document, ignored
```

---

### Post by Ron_Callison on 2014-04-28
I tried Insync and the folders show up in LibreOffice but because the files are .wpd it won't recognize them (I think).  Rats again!  I'm just going to open the individual files I use all the time and fix them for LibreOffice and save them as LibreOffice docs and move on.  After another 30 years all of my files that I use will be in LibreOffice format and I'll have forgotten all about WordPerfect.  Thanks for you help Pete.  Ron

---

### Post by Ron_Callison on 2014-04-29
Pete, it works this morning!  I opened LibreOffice this morning and tried to open the WordPerfect files again and they were all there!  Insync did the job.  I think it just needed to sleep on it.  Now I can make the changes to save the files in LibreOffice format and move on.  You solved the problem!  Thanks.  Ron

---

### Post by pfeiffep on 2014-04-29
@Ron_Callison Glad this worked for you. One caveat is Insync might not be free in the future
Please mark the thread as closed ... **[COLOR=#000080]You can mark your threads as [SOLVED] using the 'Thread Tools' drop down menu.[/COLOR]**

---

