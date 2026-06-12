---
title: "[SOLVED] Lisp + Slime problem"
date: 2008-05-25
forum: Programming Talk
---

### Post by maximinus_uk on 2008-05-25
Just installed Emacs + SBCL + Slime, but it not's working properly.

Running Emacs and then doing M-x slime gives me 

"package 'CLC' not found"

I know this is something to do with the debian common-lisp-controller by beyond this I'm at a loss. Any help anyone?

BTW, I'm using Ubuntu 8.04 and Emacs, SBCL and Slime are from apt-get

---

### Post by Lau_of_DK on 2008-05-25
> **maximinus_uk said:**
> Just installed Emacs + SBCL + Slime, but it not's working properly.

Running Emacs and then doing M-x slime gives me 

"package 'CLC' not found"

I know this is something to do with the debian common-lisp-controller by beyond this I'm at a loss. Any help anyone?

BTW, I'm using Ubuntu 8.04 and Emacs, SBCL and Slime are from apt-get

Been there, done that :)

Remove everything you installed and follow this 100%: [Install guide]("http://common-lisp.net/~lnostdal/writings/sbcl.html")

It works.

/Lau

---

### Post by xlinuks on 2008-05-25
Hi, looks like the link you provided doesn't work.

---

### Post by Lau_of_DK on 2008-05-25
> **xlinuks said:**
> Hi, looks like the link you provided doesn't work.

So sorry, I seemed to have been a bit trigger happy.

Here is the working link for the working guide: [Install guide]("http://common-lisp.net/~lnostdal/writings/sbcl.html")

/Lau ):P

---

### Post by maximinus_uk on 2008-05-26
Finally, it works now. For any other users that come across this problem, note that:

You have to fully remove slime, emacs and sbcl from your system first (including config files)

You need to follow the guide 100%

You'll probably want to manually edit your .emacs file afterwards, as I'm not so keen on the choice of colour scheme it gives you.

Pity it doesn't 'just work' with apt-get :(

---

### Post by Lau_of_DK on 2008-05-26
> **maximinus_uk said:**
> Finally, it works now. For any other users that come across this problem, note that:

You have to fully remove slime, emacs and sbcl from your system first (including config files)

You need to follow the guide 100%

You'll probably want to manually edit your .emacs file afterwards, as I'm not so keen on the choice of colour scheme it gives you.

Pity it doesn't 'just work' with apt-get :(

Its Lisp, its not supposed to 'just-work', then it wouldn't be 1337 :)

I'm glad you sorted it out. In the top of this window under "Thread tools" you can now choose "Mark thread as solved".

/Lau

---

### Post by Harry+9 on 2010-08-29
I could not get the .emacs shown in the "Install Guide":
  wget [http://common-lisp.net/~lnostdal/.emacs]("http://common-lisp.net/%7Elnostdal/.emacs")

 I used the one from Slime site and it seems to work ok:

(setq inferior-lisp-program "/home/hpm/programming/sbcl/bin/sbcl") ; your Lisp system
(add-to-list 'load-path "/home/hpm/programming/lisp/slime/")  ; your SLIME directory
(require 'slime)
(slime-setup '(slime-repl))

After starting emacs, use M-x slime.  You should end up in a lisp listener.

---

