---
title: "Upload files to transferbigfiles.com using a script language"
date: 2007-08-30
forum: Programming Talk
---

### Post by kentl on 2007-08-30
Hi!

How would you approach this problem? I want to upload files to [http://transferbigfiles.com](http://transferbigfiles.com) using a scripting language.

The reason is that I want to make the process of uploading files to them from Linux smoother.

Could I use wget or curl for this? How about a little code snippet? ;) Or just a little tip.

Thanks for reading!

---

### Post by nanotube on 2007-08-30
> **kentl said:**
> Hi!

How would you approach this problem? I want to upload files to [http://transferbigfiles.com](http://transferbigfiles.com) using a scripting language.

The reason is that I want to make the process of uploading files to them from Linux smoother.

Could I use wget or curl for this? How about a little code snippet? ;) Or just a little tip.

Thanks for reading!

i'd use python with the "browser" module. wget has no capability to submit web forms...

edit: it is actually the mechanize module, browser being one of the components. [http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

---

### Post by cwaldbieser on 2007-08-30
> **kentl said:**
> Hi!

How would you approach this problem? I want to upload files to [http://transferbigfiles.com](http://transferbigfiles.com) using a scripting language.

The reason is that I want to make the process of uploading files to them from Linux smoother.

Could I use wget or curl for this? How about a little code snippet? ;) Or just a little tip.

Thanks for reading!

You could probably use curl with the --data option, but it looks like the name of the file input on the page might change each time.  You might have to download the upload page and grep through it first for the input name.

Edit:
I looked more carefully at this, and you would actually need to use curl's -F option:
```

$ curl -F _ctl0:Content:ContentBox1:mcFile01=@localfilename

```
The weird name, "_ctl0:Content:ContentBox1:mcFile01" is the name of the file field.  "localfilename" is the name of the file.  The "@" is literal-- it indicates a local file to be uploaded.

However, it looks like an ASP.NET page, with a __VIEWSTATE form field and maybe some other stuff that will complicate what you need to POST to the page.

---

