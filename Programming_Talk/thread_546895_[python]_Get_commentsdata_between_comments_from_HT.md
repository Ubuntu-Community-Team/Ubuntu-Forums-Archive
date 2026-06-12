---
title: "[python] Get comments/data between comments from HTML"
date: 2007-09-09
forum: Programming Talk
---

### Post by Nekiruhs on 2007-09-09
I'm in a bit of a pickle here. I've gotten the HTML code for a webiste in Python. Now my only remaining step that I need to accomplish is extracting the content that I want. The trouble is, the content is only delimited from the ads by comments, for example:
```
ADS
<!-- Begin Content -->
Multiple lines of content that I want to extract
<!-- End Content -->
ADS
```
I don't think that the HTMLParser.HTMLParser, even when specially subclassed and the handle_starttag() function is overridden can handle comments. Unless I'm mistaken. Is the only way to do this with RegExes? I don't have to worry about improper formatting, as I am dealing with only one site with standard procedures for content. Any help for me?

---

### Post by pmasiar on 2007-09-09
[php]
# python code: keep it simple!
trash, keep = fultext.split('<!-- Begin Content -->')
keep, trash = keep.split('<!-- End Content -->')
[/php]

---

### Post by Nekiruhs on 2007-09-09
> **pmasiar said:**
> [php]
# python code
trash, keep = fultext.split('<!-- Begin Content -->')
keep, trash = keep.split('<!-- End Content -->')
[/php]
/jawdrop
... I knew about the split function but wow, that didn't even occur to me.
:guitar:

EDIT: It returns the error  ```
Value error: Need more than one value to unpack
```

---

### Post by pmasiar on 2007-09-09
yup, tricky part is that you can assign to multiple variables (a tuple) in one statement. Neat!

You also need to be careful you have **exactly one instance** of the split substring.

---

### Post by ansi on 2007-09-09
Hello,

> **Nekiruhs said:**
> 
I don't think that the HTMLParser.HTMLParser, even when specially subclassed and the handle_starttag() function is overridden can handle comments. 
...
 Any help for me?


According to the output of "*pydoc HTMLParser*", class **HTMLParser** has a special method for comments handling:
```
     |  handle_comment(self, data)
     |      # Overridable -- handle comment
```


Regards,

---

