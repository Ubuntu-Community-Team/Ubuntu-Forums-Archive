---
title: "html2text for .htm files?"
date: 2010-03-08
forum: Programming Talk
---

### Post by bradley002 on 2010-03-08
Hi, is there no way to use html2text for .htm files? I tested html2text with an html file and it worked, but it does not work with an htm. I tried renaming to no avail. Is there any way I can convert bulk htm to html or directly to text?

---

### Post by Hellkeepa on 2010-03-08
HELLo!

The "html" and "htm" extensions are just two extensions for HTML files, the latter one came about on early Windows version due to the 8.3 filename limit on FAT. So, the script should work on both files without issues, if it doesn't then it is most likely due to the fact that the "htm" file doesn't validate. Make sure it uses valid HTML, and that it actually has some content (and not just images).

Happy codin'!

---

### Post by bradley002 on 2010-03-08
Thanks. Actually, this is weird. I systematically deleted various parts of the html to see if there was a specific thing preventing it, and I've found that deleting the tag, <table width=95%> always lets me successfully convert it to text. Never before, but always after the deletion. Make any sense?

---

### Post by Hellkeepa on 2010-03-09
HELLo!

Probably the missing quotes that causes the RegExp to fail.

Happy syncin'!

---

### Post by myrtle1908 on 2010-03-09
Consider using HTMLTidy to fix up your HTML before parsing.

---

