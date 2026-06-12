---
title: "File types causing issue with link creation?"
date: 2021-01-29
forum: New to Ubuntu
---

### Post by curtisquark on 2021-01-29
I have a folder containing several images, and I'm trying to perform a bulk upload to a web service which creates URLs for each image in a zip archive.

However, when I create the zip archive and upload it to this web service (I've tried iLinks.io and Imgbb), it says that the archive contains 0 image files.

It seems like the fact that Linux handles file types differently than Windows is screwing up these services, since all they receive is a list of files without any file type extensions that would be needed for a Windows system to recognize the file types.

What's the easiest way around this?

---

### Post by TheFu on 2021-01-29
Bad thread title.  This has nothing to do with either symbolic links or hardlinks, which are standard features of all Unix file systems.

I'd guess this is very specific to some web service and perhaps mime-types?  Mime-types are usually controlled by the web browser, with a fallback to the OS.

Try a different compressed file format.  Try .tgz .bz or any non-ZIP format.  Linux uses InfoZip, but you can change that to some other ZIP if you like. The zip manpage may have a way to force pkzip versioning.

Part of manpage:
```
       Note that PKUNZIP 1.10  can-
       not extract files produced by PKZIP 2.04 or zip 3.0. You must use PKUN-
       ZIP 2.04g or unzip 5.0p1 (or later versions) to extract them.
```

---

