---
title: "Do images with embedded shells exist or are they theoretical constructs?"
date: 2008-08-14
forum: Programming Talk
---

### Post by rianjs on 2008-08-14
I'm looking to find a GIF file with an embedded backdoor. I've written some PHP code that uses GD and Imagick, and I need to make sure that any image that a user might upload has been sanitized before being moved to its permanent storage location.

I *think* the code I have does what is necessary, but I need to be sure.

I've [seen references](http://www.scanit.be/uploads/php-file-upload.pdf) (PDF) to malformed GIFs with embedded shells, but I've never been able to actually *find* one. (Which is probably a good thing.) Do such things actually exist, or are they just theoretical constructs/proof of concept ideas?

---

### Post by rianjs on 2008-08-14
Blargh. Nevermind. The PDF I linked has a link to such an example. :rolleyes:

GG reading comprehension.

---

### Post by damis648 on 2008-08-14
Hmm... not exactly in all situations but image loading programs can be exploited to execute code, ie a DOC file can be malformed to exploit code in Word, for example. Of course, such exploits are usually patched immediately. Also, TIFF files are commonly used as exploits on PS3's and the original installed for jailbreaking an iPhone was just a TIFF image used to exploit safari.

---

