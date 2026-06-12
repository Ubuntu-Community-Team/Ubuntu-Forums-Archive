---
title: "How to view contents of a corrupted .odt file (Libre-Office)?"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-12
One of my Libre-Office files has been corrupted. I'm wondering how I can view the contents as text. I've tried executing "less" and "cat" and "od -c" on the file, but each of them returns a series of special characters (non readable). 

Basically, I'm trying to recover the contents of the file (or find out if that's possible). Any advice on programs/commands to use would be appreciated. 

I'm on Libre 3.4.4 on Ubuntu 11.10.

---

### Post by jps2012 on 2012-04-12
Note: If I try to open the .odt file via "open" in LibreOffice, I get a message saying it doesn't exist. The icon for the file is sitting on my desktop. 

If I use Nautilus to view it's properties, I'm told the file type is "OpenDocument Text (application/vnd.oasis.opendocument.text) 

The file size is 98.8 kB (not small, but still large for something that "doesn't exist")

The permissions on it are set to "read and write"

---

### Post by Vaphell on 2012-04-12
Odt is just a zip file with document contents, check if you can unzip it.

---

### Post by Linux_junkie on 2012-04-12
> **jps2012 said:**
> One of my Libre-Office files has been corrupted. I'm wondering how I can view the contents as text. I've tried executing "less" and "cat" and "od -c" on the file, but each of them returns a series of special characters (non readable). 

Basically, I'm trying to recover the contents of the file (or find out if that's possible). Any advice on programs/commands to use would be appreciated. 

I'm on Libre 3.4.4 on Ubuntu 11.10.

try and open it using a text editor such as gedit.  you might be able to copy & paste the text you want into a new writer document.

---

### Post by jps2012 on 2012-04-12
I did try opening it in gedit on my Ubuntu machine (11.10). I get junk, such as, "\00\00\AD7\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\92\00styles.xmlPK" 

Which goes on for 40 or so pages. 

BUT I did just discover an awesome workaround. I copied the corrupted file to a thumb drive. I opened on a Mac (10.5) by dragging the file over the TextEdit icon in the side panel. Voila! There it is. Resaved. It now opens in LibreOffice. 

A note to users who've had similar problems with LO: I think it's wise to go into your preferences and set an autosave function for creating backups. Unlike most Ubuntu aps, the preferences panel isn't under the EDIT tab in the ap menu. To set preferences in LO, you go to Tools > Options > Load/Save > General

Check the box for "Always save backup copy" (I didn't have this checked prior to having my file corrupt, therefore I was ASKING for trouble.)

Choose a time interval (the box is on the right-hand side; see link for screenshot referenced below). I set mine (given how much I now trust LibreOffice) to one minute. I'd choose 0.00001 nanoseconds, but that option isn't available (and I want to be reasonable). 

Here's the path for where backups are stored in LO: {user}\user\backup 

More info on backups is here: [http://help.libreoffice.org/Common/Paths](http://help.libreoffice.org/Common/Paths)

The screenshot of the LO options panel (selected for backups) is here:

[http://s1071.photobucket.com/albums/u503/2012jps2012/](http://s1071.photobucket.com/albums/u503/2012jps2012/)

Good luck, anyone who's corrupted.

---

### Post by jps2012 on 2012-04-12
Per the quote "odt is a zip file." 

Really? A zip file? Wouldn't it list a zip extension if it were a zip file? 

Wouldn't I have to unzip it before it would open? That's not how it's behaving. But I know little about LO files, so (if you have time) please let me know how it can be a zip file but not appear to behave like a zip file. 

It could be a roasted virtual coconut, for all I care. I just want it to open, so I can consume the contents (and I did find a way to crack it, which is what matters most).

---

### Post by Vaphell on 2012-04-13
if i name a shell script flower.jpg it doesn't mean it becomes a picture. Extension is used to indicate the filetype but in no way it guarantees the file is what it claims it is.

Odt is a bunch of files zipped together. Make a copy, change its extension to zip and try to open it.
Open/Libre Office 'knows' it has to unzip the file internally to load contents and zip them when saving.

---

### Post by haqking on 2012-04-13
> **Vaphell said:**
> if i name a shell script flower.jpg it doesn't mean it becomes a picture. Extension is used to indicate the filetype but in no way it guarantees the file is what it claims it is.

Odt is a bunch of files zipped together. Make a copy, change its extension to zip and try to open it.
Open/Libre Office 'knows' it has to unzip the file internally to load contents and zip them when saving.

+1

[http://en.wikipedia.org/wiki/OpenDocument#Specifications](http://en.wikipedia.org/wiki/OpenDocument#Specifications)

---

### Post by jps2012 on 2012-04-13
Haqking and vaphell: I OBVIOUSLY didn't understand the meaning of file extensions. Thank you. I won't trust the file to be what it appears to say it is (particularly when it's a script). 

I had another file corruption on an ODT file yesterday--two out of four ODT files in LibreOffice. I've started using gedit instead. I really have NO faith in LO now.

---

### Post by Vaphell on 2012-04-14
when you need to take quick notes, create todo lists and rough drafts of whatever etc, full blown documents are an overkill for sure. You can't go wrong with plain text, there is next to no risk of corruption and producing formatted document out of it when needed is trivial, just copy/paste into word processor :)

---

### Post by jps2012 on 2012-04-14
vaphell: You're absolutely right. That's what I've been doing--drafting in a simple text editor, and doing the final formatting in LibreOffice (only when something HAS to be formatted).

---

