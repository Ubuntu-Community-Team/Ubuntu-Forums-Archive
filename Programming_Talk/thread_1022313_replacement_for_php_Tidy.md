---
title: "replacement for php Tidy?"
date: 2008-12-26
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-12-26
Hey guys 

I was wondering if anyone has any recommendations for a replacement for the PHP Tidy library?

I dont have access to a root ssh to install the modules myself but I need the same kind of functionality 

Any suggestions?

Thanks in advance!

Mike

---

### Post by drubin on 2008-12-26
I have never used Tidy php but if you explain what it is we might be able to find alternatives that do the same thing.

EDIT: 
I miss read your post and was looking up tiny.. Here is the correct [link]("http://www.php.net/tidy") but I have never used it.

---

### Post by drubin on 2008-12-26
I am interested to know reasoning for cleaning up your html files and increasing the output/processing to make your html neater?

---

### Post by michaelzap on 2008-12-26
You can use HTML Tidy via various client-side IDE programs, or you can use a WYSIWYG package like Tiny MCE that runs as Javascript within web forms (integrated into many CMS programs). If you really need to tidy up code as PHP output on the server, there are probably ways to include the Tidy libraries manually in a script and use them even if your PHP installation doesn't have those modules. I'd check out the HTML Tidy site for tips on doing that.

---

