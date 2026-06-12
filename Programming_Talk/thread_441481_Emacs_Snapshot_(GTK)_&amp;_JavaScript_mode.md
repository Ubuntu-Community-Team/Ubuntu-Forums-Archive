---
title: "Emacs Snapshot (GTK) &amp; JavaScript mode"
date: 2007-05-12
forum: Programming Talk
---

### Post by Ferio on 2007-05-12
Hi, I'm using Emacs Snapshot (GTK) (the one in Edgy's repos) and I wanted it to have a JavaScript mode, so I downloaded it from [Karl Landström's page]("http://web.comhem.se/%7Eu34308910/emacs.html#javascript") (because it seems to be the best JavaScript mode out there) and moved it to [FONT=Courier New]/etc/emacs/site-start.d[/FONT] as [FONT=Courier New]50javascript.el[FONT=Arial] because I suppose the number is its precedence when loading, and I've set it to 50 because it's the number on the rest of my language modes in there (html-helper & css).

So, after doing this and checking that I can do [FONT=Courier New]M-x javascript-mode RET[/FONT], I try to add these lines that I've found at [Emacsen.org]("http://emacsen.org/2005/09/26-javascript") to my [FONT=Courier New].emacs[/FONT] for it to load JavaScript mode when I open a .js:
[/FONT][/FONT]```
[FONT=Courier New](autoload 'javascript-mode "javascript" nil t)[/FONT][FONT=Arial][FONT=Courier New]
(add-to-list ‘auto-mode-alist ‘("\\.js\\’" . javascript-mode))[/FONT][/FONT]
```But it fails! It loads my .js files in Java/l Abbrev modes; I can still switch to JavaScript mode after loading, but it would be nice to automate it, and since I don't know any ELisp, any help will be very appreciated.[FONT=Arial]
[/FONT]

---

