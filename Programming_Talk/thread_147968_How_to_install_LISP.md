---
title: "How to install LISP??"
date: 2006-03-21
forum: Programming Talk
---

### Post by kiubuntu on 2006-03-21
Dear friends,
I read another thread here about the same topic and I was going to ask these question in that (very new) thread only. But then I thought of making a new a thread coz I am a 'real' newbie int programming field. Sorry moderators. 
1. What compiler/interpreter needs to be installed to start running LISP programs on Windows XP, Ubuntu and mac os X?
2. If i install emacs and thats it? No need to install any LISP compiler/interpreter?
3. I have downloaded 'Practical Common Lisp, and this book suggests 'Lisp in a box'. I do not understand what it is. Esp. what is SLIME? Also is it available for Ubuntu and mac os x?
Please guide so that everything starts working on my ubuntu and mac.
Thanx.

---

### Post by 4dz0 on 2006-03-21
Heres some info I found regarding slime:

[http://ww.telent.net/lisp/according_to/slime.html](http://ww.telent.net/lisp/according_to/slime.html)

and heres some i found regarding 'LISP in a box':

[http://common-lisp.net/project/lispbox/](http://common-lisp.net/project/lispbox/)

---

### Post by Adrian on 2006-03-21
I'm using **drscheme**:
[http://www.drscheme.org/](http://www.drscheme.org/)

It's an integrated development enviroment and can be found in the *universe* repository.

---

### Post by kosac on 2006-03-21
Install emacs, install cmucl, download the slime pack. After that you just need to add some lines to your .emas file. 

The following site [http://common-lisp.net/project/slime/](http://common-lisp.net/project/slime/) explains everything, including the installation process that is in the manual section. It has also the slime pack for download.

And that's everything you need to get started with Common LISP.

Good luck


PS: to use slime on emacs, open emacs, then press M-x (Alt+x), type slime and then enter. That will start the CL-USER interface. (SLIME = Superior Lisp Interaction Mode for Emacs)

---

