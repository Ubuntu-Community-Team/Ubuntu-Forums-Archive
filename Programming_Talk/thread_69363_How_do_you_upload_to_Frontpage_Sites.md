---
title: "How do you upload to Frontpage Sites?"
date: 2005-09-26
forum: Programming Talk
---

### Post by vayu on 2005-09-26
You are not supposed to upload using FTP on a Frontpage Extension site.  It breaks the extensions.  (if you don't know what I'm talking about, do a google search on Frontpage, ftp)    I have to upload to sites that have Frontpage Extensions enabled.  Are there any programs I can run on Ubuntu that will let me upload and delete files without breaking the Extensions?

---

### Post by toojays on 2005-09-27
My googling didn't quite make it clear, but can you use webdav? Nautilus and Konqueror both support webdav.

---

### Post by Mujaheiden on 2005-11-13
Mmm... My login is refused, don't know why, when I try to connect to [http://www.studver.unimaas.nl](http://www.studver.unimaas.nl) with the gnome connect to server procedure.

---

### Post by the_it on 2005-11-15
That's a very strange error.  I'm thinking it has something to do with your unix/windows text coding differences.  A GUI ftp client, say gftp, has an easy checkbox to enable/disable ascii transfer (normally, I think you use binary transfer to files, this copies your files bit-per-bit, including the different line return codes from w32 to unix).  Try enabling ascii (text) transfer and trying again?

---

### Post by Mujaheiden on 2006-02-11
[QUOTE=the_it]A GUI ftp client, say gftp[/QUOTE]

Thanks for your reply - I've picked up the same issue again, and unfortunately stumbled over my own unresolved posts... however, I'm not allowed to use FTP to my universities' server.
And in de network connect to WEbDAV is no option to connect with ASCII or binary, so I guess we were not communicating clearly enough with each other?

---

