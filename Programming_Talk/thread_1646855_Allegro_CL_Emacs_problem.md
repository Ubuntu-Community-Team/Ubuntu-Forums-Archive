---
title: "Allegro CL Emacs problem"
date: 2010-12-16
forum: Programming Talk
---

### Post by Kaangaas on 2010-12-16
Hey :)

I've resently gone over to using Ubuntu after a life time in Windows. I'm used to Emacs and Allegro CL for lisp and I want to do the same now on ubuntu.

I've installed Allegro CL without a problem and it works fine in the terminal. But with emacs it doesen't work as I want it to.

I followed this guide [http://www.franz.com/emacs/](http://www.franz.com/emacs/) to get it to work with emacs.

If I typ this: (load "/usr/local/acl82express/eli/fi-site-init.el") and press C-j ACL adn Emacs works fine. 

But since I don't want to do that every singel time I'm going to use ACL and Emacs I tried to use the .emacs file.

I took the code from the guide I linked earlier and put it in the .emacs file:

> ; This is sample code for starting and specifying defaults to the

; Emacs-Lisp interface. 

  (push "usr/local/acl82express/eli" load-path)

  (load "fi-site-init.el")

  (setq fi:common-lisp-image-name "usr/local/acl82express/alisp")

  (setq fi:common-lisp-image-file "usr/local/acl82express/alisp.dxl")

  (setq fi:common-lisp-directory "usr/local/acl82express")

Now however, I cet an error on start that says: 

> "Warning (initialization): An error occurred while loading '/home/kangas/.emacs':

File error: Cannot open load file, fi-site-init.el"

And of course ACL havent been loaded into emacs.

I've checked all the paths and privileges and I see nothing wrong.

Any one who can help?

//Kaangaas

---

### Post by Arndt on 2010-12-16
> **Kaangaas said:**
> Hey :)

I've resently gone over to using Ubuntu after a life time in Windows. I'm used to Emacs and Allegro CL for lisp and I want to do the same now on ubuntu.

I've installed Allegro CL without a problem and it works fine in the terminal. But with emacs it doesen't work as I want it to.

I followed this guide [http://www.franz.com/emacs/](http://www.franz.com/emacs/) to get it to work with emacs.

If I typ this: (load "/usr/local/acl82express/eli/fi-site-init.el") and press C-j ACL adn Emacs works fine. 

But since I don't want to do that every singel time I'm going to use ACL and Emacs I tried to use the .emacs file.

I took the code from the guide I linked earlier and put it in the .emacs file:



Now however, I cet an error on start that says: 



And of course ACL havent been loaded into emacs.

I've checked all the paths and privileges and I see nothing wrong.

Any one who can help?

//Kaangaas

I think the error is that you want this

(push "usr/local/acl82express/eli" load-path)

to be

(push "/usr/local/acl82express/eli" load-path)

---

### Post by Kaangaas on 2010-12-16
Thx, that did it :)

---

