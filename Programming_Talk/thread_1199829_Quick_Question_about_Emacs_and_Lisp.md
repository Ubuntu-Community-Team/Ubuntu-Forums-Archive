---
title: "Quick Question about Emacs and Lisp"
date: 2009-06-29
forum: Programming Talk
---

### Post by unknownPoster on 2009-06-29
Hello,

I'm interested in learning Lisp. I've been following various tutorials on the internet and they recommend the following .emacs configuration:

```

;; Setup
(add-to-list 'load-path "/usr/share/common-lisp/source/slime/")
(setq inferior-lisp-program "/usr/bin/sbcl")
(require 'slime)
(slime-setup)

;; Use syntax highlighting
(global-font-lock-mode t)

;; Highlight open/close parens
(show-paren-mode 1)
;; Properly indent line when "enter/return" key is pressed.
(add-hook 'lisp-mode-hook '(lambda ()
      (local-set-key (kbd "RET") 'newline-and-indent)))
```The comments are mine. I have SLIME installed as well. My question is about the First two lines in the setup section. I have read in this forum that many people prefer SBCL as opposed to CLISP. 

Am I missing something terribly significant by using CLISP rather than SBCL?

If so what would I need to change in my configuration file to use  SBCL rather than CLISP?

Thanks!

EDIT: I found how to change lisp implementations, but I still am not sure about SBCL compared to CLISP.

I've read that CLISP is compiled to the bytecode interpreter while SBCL is compiled to machine code, so SBCL is arguably faster than CLISP...but I'm sure there is more to it than that.

---

### Post by soltanis on 2009-06-29
Well they have slight variations between their semantics. Its just preference to me, when I was learning CL, the book I was using worked perfectly with SBCL but not at all with CLISP (things would just...not work or not be there). I also don't think CLISP comes with asdf, and has some odd problems with asdf module compatibility sometimes.

---

### Post by unknownPoster on 2009-06-30
> **soltanis said:**
> Well they have slight variations between their semantics. Its just preference to me, when I was learning CL, the book I was using worked perfectly with SBCL but not at all with CLISP (things would just...not work or not be there). I also don't think CLISP comes with asdf, and has some odd problems with asdf module compatibility sometimes.

I assume you are referring to [http://en.wikipedia.org/wiki/Another_System_Definition_Facility](http://en.wikipedia.org/wiki/Another_System_Definition_Facility) ?

---

### Post by soltanis on 2009-06-30
Yes, I am.

[www.cliki.net](www.cliki.net)

---

### Post by hessiess on 2009-06-30
Personally of the two, I prefer Clisp as it has a better REPL thanks to GNU readline. Its much nicer for just quickly trying stuff out. Though as of the past few days I have bean more interested in clojure thanks to its native java lib support, One of the problems I found with Common Lisp was a lack of available libraries, and a lack of standards for network access, threading etc.

---

### Post by unknownPoster on 2009-06-30
> **soltanis said:**
> Yes, I am.

[www.cliki.net]("http://www.cliki.net")


Thanks for the link. It will be useful as I hack my way through some tutorials and such. :)

---

