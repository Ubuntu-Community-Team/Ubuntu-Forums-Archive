---
title: "cannot open load file for bashdb in emacs"
date: 2009-03-04
forum: Programming Talk
---

### Post by flylehe on 2009-03-04
Hi, 

I just installed bash debugger bashdb under ${HOME}/bin/bashdb-4.0-0.2/bin. Now I want to use it in emacs. 

As bashdb.el indicates, I add into .emacs "(autoload 'bashdb "bashdb" "BASH Debugger mode via GUD and bashdb" t)". However I got this "cannot open load file: bashdb" error when "M-x bashdb". The error remains when I add this to ".emacs": 
(setq load-path 
      (append (list nil "${HOME}/bin/bashdb-4.0-0.2/bin/" 
                    "/user/bil/emacs" 
                    "/usr/local/lisplib" 
                    "~/emacs") 
              load-path)) 
I am not sure if PATH also has effect, but I include bashdb path into it. 


Thanks in advance!

---

### Post by ppotoplyak on 2009-05-18
Using the absolute path to bashdb.el worked for me.

In summary, add something similar to your .emacs file :

(autoload 'bashdb "/usr/share/emacs/site-lisp/bashdb/bashdb.el" "BASH Debugger mode via GUD and bashdb" t)

---

