---
title: "Customizing emacs"
date: 2008-09-24
forum: Programming Talk
---

### Post by Freiddie on 2008-09-24
Hello, I'm trying to customize emacs so it does what I usually expect from a programming editor. I tried to set it to "Save sessions on quit" but it didn't work (I don't even know what I was doing):
[http://www.gnu.org/software/emacs/manual/html_node/emacs/Saving-Emacs-Sessions.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/Saving-Emacs-Sessions.html)
Could someone please explain what the article is talking about?

Thank you very much,
Freiddie

---

### Post by ankursethi on 2008-09-25
Add this to your .emacs file : (desktop-save-mode 1)

It does what you expect. The next time you open Emacs, it will open all the buffers you were editing when your quit it, along with window positions etc. It's right there in the article you linked to.

BTW, a very nice resource for Emacs wisdom is the Emacs wiki : [http://emacswiki.org/](http://emacswiki.org/)

Also, try learning about Emacs Lisp if you want to get down and dirty with hacks and customizations. It's a bit advanced, but useful. It's on my "To Learn - URGENT" list right now.

---

### Post by Freiddie on 2008-09-25
Thanks!

I don't mind learning another language, but I just don't have enough time to play around with emacs all day with all that homework...

Freiddie

---

