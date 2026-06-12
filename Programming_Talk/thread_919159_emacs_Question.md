---
title: "emacs Question"
date: 2008-09-13
forum: Programming Talk
---

### Post by perlsyntax on 2008-09-13
How do i install this and here the links and i am very new with emacs



[http://search.cpan.org/~yewenbin/Emacs-PDE-0.2.16/lib/Emacs/PDE.pm](http://search.cpan.org/~yewenbin/Emacs-PDE-0.2.16/lib/Emacs/PDE.pm)

---

### Post by shifty2 on 2008-09-13
Emacs is based around packages such as the one you linked to and the way of installing them is almost always the same - as the link suggests, add the following to you .emacs
```

     (add-to-list 'load-path "/path/to/pde/")
     (load "pde-load")
```
If you are new to emacs I would strongly suggest going through the tutorial (Type C-h t) and looking through the emacs wiki ([www.emacswiki.org](www.emacswiki.org)) both contain invaluable information.

---

### Post by perlsyntax on 2008-09-20
Do i have to make a .emacs file if i am right?:(

---

### Post by nvteighen on 2008-09-20
> **perlsyntax said:**
> Do i have to make a .emacs file if i am right?:(
It depends. If you already have customized something, it surely exists... If not, just create a text file in you home directory with the contents shifty2 told you.

---

### Post by perlsyntax on 2008-09-20
I just lost on how to make a file with my emacs in my home dir.

---

### Post by nvteighen on 2008-09-20
> **perlsyntax said:**
> I just lost on how to make a file with my emacs in my home dir.
Do you know how to use Emacs? It's not that difficult if you read the tutorial (C-h t).

For you to know, to create a file do C-x C-f, type the filename (opening and creating a file in Emacs is the same thing) and then save using C-x C-s.

---

### Post by perlsyntax on 2008-09-20
that all i do and where do i find the perl tools?

---

### Post by monkeyking on 2008-09-21
You should download and unpack the pde file
[http://search.cpan.org/CPAN/authors/id/Y/YE/YEWENBIN/Emacs-PDE-0.2.16.tar.gz](http://search.cpan.org/CPAN/authors/id/Y/YE/YEWENBIN/Emacs-PDE-0.2.16.tar.gz)

then create a .emacs file
and put your 2 lines in it.

I haven't coded much perl in last year, but I still have these in my .emacs.

```

;; Use cperl-mode instead of the default perl-mode
(add-to-list 'auto-mode-alist '("\\.\\([pP][Llm]\\|al\\)\\'" . cperl-mode))
(add-to-list 'interpreter-mode-alist '("perl" . cperl-mode))
(add-to-list 'interpreter-mode-alist '("perl5" . cperl-mode))
(add-to-list 'interpreter-mode-alist '("miniperl" . cperl-mode))



(add-hook 'cperl-mode-hook 'n-cperl-mode-hook t)
(defun n-cperl-mode-hook ()
  (setq cperl-indent-level 2)
  (setq cperl-continued-statement-offset 0)
  (setq cperl-extra-newline-before-brace t)
  (set-face-background 'cperl-array-face "wheat")
  (set-face-background 'cperl-hash-face "wheat")
  )

(setq default-frame-alist '(
       (font . "6x10")
       (cursor-color . "gray25")
       (background-color . "white")
       (foreground-color . "black")
       (vertical-scroll-bars . left)
       (top . 0) (left . 0)
       (width . 98) (height . 60)
       )
)

```

emacs is a nice editor,
but you should set it up.
matching paranthesis, funky syntax, block mode and so on.

Find some long .emacs file somewhere on the net.
and play around with it.

I can give you mine if you want.

good luck

---

