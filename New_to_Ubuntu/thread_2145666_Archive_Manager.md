---
title: "Archive Manager"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by supajason on 2013-05-16
Hi Everyone,

I'm looking for a for a Archive manager that can extract all files if the file extension is .html
I've been looking around but can't find one.

Thank you
Jason

---

### Post by mastablasta on 2013-05-16
.html is not packaged format (not an archive) so there is nothing to extract there.

if t's actualyl another format (eg. tar.gz., zip...) then just use default manager.

---

### Post by supajason on 2013-05-16
Hi Mastablasta,

Thank you for your reply.

Sorry what I mean is if I have a zip file that contains:

/my-zip-file.zip
-/images
-/images/logo.png
-index.html

In the default manager if I open index.html it just opens that one file.
I want it to extract the whole archive because the other folder and logo.png are required for the index.html to be displayed correctly.

So I need a manger that can look at file extensions in the archive and if they match a list(.htm;.html) then extract the whole archive.

Thanks for your help
Jason

---

### Post by d0006 on 2013-05-16
I don't think you can do what you want.  The index.html file is probably looking for relative paths to the other files but those paths don't exist because the files are still zipped. I don't think there are any Unarchivers that are smart enough to parse filesystem paths from within an archive.   Just extract all the files in the zip archive to a new folder and hope everything works.  If there is stuff you don't want just delete it.

---

### Post by zombifier25 on 2013-05-16
It is possible, but you'll need to write a bash script.

I can't script, so maybe someone else can help you.

---

