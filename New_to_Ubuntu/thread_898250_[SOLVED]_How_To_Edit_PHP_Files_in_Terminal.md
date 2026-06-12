---
title: "[SOLVED] How To Edit PHP Files in Terminal?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2008-08-23
Hi!

I want to edit a PHP file in Terminal. Only problem is that I got this error, and I don't know how to add a mailcap rule. Does anyone know?
```

Error: no "edit" mailcap rules found for type "application/x-httpd-php"

```
I tried reading this post ([http://ubuntuforums.org/showthread.php?t=832194](http://ubuntuforums.org/showthread.php?t=832194)) but don't understand his fix. What to do?

Thanks a lot!!

---

### Post by Ryadt on 2008-08-23
What command did you type in?

---

### Post by iaskedalice09 on 2008-08-23
To edit?

edit <filename>

BTW, I love your avatar!

---

### Post by eightmillion on 2008-08-23
Try nano <filename>
It's an easy to use command line text editor.

---

### Post by livestockPimp on 2008-08-23
try gedit <filename>
or nano <filename>

---

### Post by Ryadt on 2008-08-23
> **iaskedalice09 said:**
> To edit?

edit <filename>

BTW, I love your avatar!

Thx...:lolflag:

Try nano<filename> - to edit in terminal
or 
   gedit<filename> - to edit in text editor.

---

### Post by aloshbennett on 2008-08-23
When using edit, you have to sepcify the mime type explicity, or it should be set up in ~/.mailcap and ~/.mime.types.

Try 'edit text/php:test.php'

More info: man edit :)

---

### Post by iaskedalice09 on 2008-08-23
Thanks all! Thought I had to install nano after reading about it and getting excited, but then disappointed when I couldn't find it! Lawl. Thanks so much! SOLVED.

---

### Post by houiostesmoiras on 2012-08-28
I realize this was marked as solved, but it looks to me like there's one small issue yet. I'm guessing if you were just using 'edit <filename>' that you were (and were used to using) vi(m). Now, while 'edit' will pull up known mime filetypes in vi, you can also just open *anything* in vi by typing 'vi <filename>'. If you've set emacs as your command line editor, I assume you can do something similar with that. Also, if you decide to try nano anyway, it appears to come with Ubuntu currently.

---

