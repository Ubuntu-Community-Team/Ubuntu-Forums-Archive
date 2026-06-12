---
title: "Common Lisp syntax highlighting for Gedit"
date: 2014-11-21
forum: Programming Talk
---

### Post by veddox on 2014-11-21
Having recently learnt Common Lisp, I was rather disappointed that Gedit  (my most-used text editor) did not provide any syntax highlighting for  it. I also could not find any extensions for it on the Internet. However, I discovered the folder where Ubuntu keeps all the XML-files for language syntax. It does include a file for Scheme, so I modified this to fit Common Lisp. In case it interests anybody else, I have uploaded it in the attachments.

To add it to your system, save the file as /usr/share/gtksourceview-3.0/language-specs/lisp.lang. When you restart Gedit, it should be available.

Please note that this is *not* a finished product. Like I said, I am still very much a Lisp newbie, so it is likely that I missed out some keyword or another. Also, because I was modifying the Scheme file, there is very probably still a lot of Scheme syntax left in there. Nonetheless, it is better than nothing. Feel free to modify it - if you do, I would appreciate it if you would post the adapted version back to here.

P.S. Please refrain from starting any editor flamewars here - this post is targeted at Gedit-users, not Emacs-, Vi- or any other activists...

---

### Post by Aubrey_Robertson on 2015-01-24
Thanks for this!

---

### Post by Aubrey_Robertson on 2015-01-24
Found this one guy!  4 times the size of yours!  Thanks though!

[https://gist.github.com/shamansir/1164574](https://gist.github.com/shamansir/1164574)

---

### Post by veddox on 2015-01-26
Thanks for the link - looks good!

---

