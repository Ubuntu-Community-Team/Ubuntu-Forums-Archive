---
title: "[Help]highlight php code with emacs23."
date: 2011-04-06
forum: Programming Talk
---

### Post by haidang001 on 2011-04-06
I have ubuntu 10.10 installed emacs (emacs23.1.1).
I found Emacs insteresting, but It cannot work with php-mode (may be that php-mode hasn't been installed). It doesn't highlight php code.

Help me, please. Thank you so much!

---

### Post by johnl on 2011-04-06
Hi,

You can download a php major mode from here: [http://sourceforge.net/projects/php-mode/](http://sourceforge.net/projects/php-mode/)


To install, this is how I would do it:

Extract the 'php-mode.el' to '~/emacs.d/site-lisp/php-mode.el' creating the folders if necessary.

Open your "~/.emacs" (or ~/.emacs.d/init.el) file and add the following:

```

;; tell emacs that we have some modules in this folder:
(add-to-list 'load-path "~/.emacs.d/site-lisp")
;; use php-mode
(require 'php-mode)
 ;; use php-mode for .php files
(add-to-list 'auto-mode-alist '("\\.php$" . php-mode))

```

Hope this helps.

---

### Post by haidang001 on 2011-04-07
> **johnl said:**
> Hi,

You can download a php major mode from here: [http://sourceforge.net/projects/php-mode/](http://sourceforge.net/projects/php-mode/)


To install, this is how I would do it:

Extract the 'php-mode.el' to** '~/emacs.d/site-lisp/php-mode.el'** creating the folders if necessary.



 I 've copied 'php-mode.el' to **'~/.emacs.d/site-lisp/php-mode.el'** (not **'~/emacs.d'**, I think so). And followed your suggestion, but when I start emacs, it shows this error:

```
Warning (initialization): An error occurred while loading `/root/.emacs':

error: `c-lang-defconst' must be used in a file

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

```So, I start Emacs with the '--debug-init' (by gnome-terminal). It says:
```
&#834;&#834;&#834;&#834;&#834;Debugger entered--Lisp error: (error "`c-lang-defconst' must be used in a file")
  signal(error ("`c-lang-defconst' must be used in a file"))
  error("`c-lang-defconst' must be used in a file")
  c-define-lang-constant(c-mode-menu ((t cons ["Comment Out Region" comment-region ...] (cons ["Uncomment Region" ... ...] ...))))
  require(cc-langs)
  eval-buffer(#<buffer  *load*<2>> nil "/root/.emacs.d/site-lisp/php-mode.el" nil t)  ; Reading at buffer position 4158
  load-with-code-conversion("/root/.emacs.d/site-lisp/php-mode.el" "/root/.emacs.d/site-lisp/php-mode.el" nil t)
  require(php-mode)
  eval-buffer(#<buffer  *load*> nil "/root/.emacs" nil t)  ; Reading at buffer position 624
  load-with-code-conversion("/root/.emacs" "/root/.emacs" t t)
  load("~/.emacs" t t)
  #[nil "^H\205\264^@ . . . etc (I cannot fully paste this line)
  command-line()
  normal-top-level()

```Could you help me with this bug :(.

---

### Post by haidang001 on 2011-04-15
Anyone can help me, please!

---

