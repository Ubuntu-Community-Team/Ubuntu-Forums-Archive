---
title: "[SOLVED] zip file help needed"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by paker on 2008-07-31
I have a folder full of mp3 files that are somehow zipped. When I double click on the folder, Archive Manager lists pops and lists individual mp3 files. I cannot play individual files. Right click on file, I get these choices:
View file
Open With
Extract
Cut Delete, etc

I choose Extract. Error message pops up which reads:

need pk compat. v4.6 (can do v2.1)

Do I need to unzip in a Windows machine?
Thanks.

Little more info:

Right click on the folder > Property 
Type: Zip archive
MIMI type: application/zip

Right click on the folder > Extract Here

error message pops up, same as above: need pk  compat. v4.6 (can do v2.1)

---

### Post by ibutho on 2008-08-01
Install p7zip and see if that helps.

---

### Post by paker on 2008-08-01
installed p7zip and did

"p7zip filename.zip" and "p7zip -d filename.zip"

Neither worked. Am I missing something?

PS: I have a laptop with Windows Vista Home. I will try unzipping on the machine.

---

### Post by ibutho on 2008-08-01
Use the command 7z (or 7za) instead of p7zip (p7zip provides the 7z and 7za commands).

---

### Post by billgoldberg on 2008-08-01
Install the package "p7zip-full" (includes rar, ...)

```
sudo apt-get install p7zip-full
```

Right-click the file and choose "extract here".

Or open archive manager (command is "file-roller") and extract it somewhere else.

---

### Post by paker on 2008-08-02
Installed p7zip, p7zip-full, and p7zip-rar.
Right clicked and selected Extract Here. Error message: Archive Type Not Supported. Tried both on zip file and rar file.

Also used terminal command:
7z filename.zip
   and
7za filename.zip.

Archive manager opens up with bunch of .mp3 files. But these files cannot be played, opened, or extracted.

---

### Post by eightmillion on 2008-08-02
Try this...
> 7z x nameofarchive.zip

---

### Post by SunnyRabbiera on 2008-08-02
Hmm, well also try other zip applications.
Sometimes file roller has issues, one I use as an alternative is xarchive

---

### Post by paker on 2008-08-02
7z x filename.zip 
didn't do anything differently. File Roller pops up and lists a bunch of mp3 files, but they cannot be played, opend, or anything.

Even before installation of p7zip, p7zip-full, when I double clicked on filename.zip, File Roller popped up and listed mp3 files in the folder.

---

### Post by unutbu on 2008-08-02
Perhaps try
```
7z e -y filename.zip
```
(I'm getting this from [http://blog.carrion.ws/2005/12/](http://blog.carrion.ws/2005/12/), search for "Uncompressing files").

---

### Post by paker on 2008-08-03
7z commands didn't work (including 7z e -y)

Xarchive worked beautifully! Thanks. It handled both .zip and .rar. Now I have one more useful tool!

---

### Post by timtim885 on 2008-11-26
> **paker said:**
> Installed p7zip, p7zip-full, and p7zip-rar.
Right clicked and selected Extract Here. Error message: Archive Type Not Supported. Tried both on zip file and rar file.

Also used terminal command:
7z filename.zip
   and
7za filename.zip.

Archive manager opens up with bunch of .mp3 files. But these files cannot be played, opened, or extracted.

I also had this problem. and using '7z x filename.zip' worked.

Using '7z filename.zip' should give incorrect command line and '7z e filename.zip, should extract but ignores directory structure within the archive.

---

### Post by sandyeggoboy on 2010-02-04
Hi, I noticed this thread, and I downloaded and installed p7zip-full package, then used from command line, 

p7zip x <filename.zipx>

and it worked fine!!


THANKS@!

---

### Post by Lonco on 2010-03-10
it worked perfectly. thanks a lot

---

### Post by PGScooter on 2011-07-05
> **sandyeggoboy said:**
> Hi, I noticed this thread, and I downloaded and installed p7zip-full package, then used from command line, 

p7zip x <filename.zipx>

and it worked fine!!


THANKS@!

Thank you, this solved my zipx problem. I just did sudo apt-get install p7zip-full
and then I right-clicked on the file in Nautilus and "extract files".

Thank you

---

