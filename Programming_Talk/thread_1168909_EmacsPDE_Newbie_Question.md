---
title: "Emacs::PDE Newbie Question"
date: 2009-05-24
forum: Programming Talk
---

### Post by perlsyntax on 2009-05-24
How do i get all the commands in my emacs file so all the tool for my emacs::PDE work?

[http://cpansearch.perl.org/src/YEWENBIN/Emacs-PDE-0.2.16/lisp/doc/QuickStartEn.html](http://cpansearch.perl.org/src/YEWENBIN/Emacs-PDE-0.2.16/lisp/doc/QuickStartEn.html)

---

### Post by perlsyntax on 2009-05-24
Here my .emacs file

add-to-list 'load-path "/home/perlsyntax/.emacs.d/pde")
(load "pde-load")



(ido-mode 1)
(require 'template-simple)

;; M-SPC not available, window manager take it away
(global-set-key (kbd "M-'") 'just-one-space)
(global-set-key (kbd "C-M-=") 'pde-indent-dwim)
;; nearest key to dabbrev-expand
(global-set-key (kbd "M-;") 'hippie-expand)
(global-set-key (kbd "C-;") 'comment-dwim)
(global-set-key (kbd "C-c f") 'comint-dynamic-complete)

(setq hippie-expand-try-functions-list
          '(try-expand-line
            try-expand-dabbrev
            try-expand-line-all-buffers
            try-expand-list
            try-expand-list-all-buffers
            try-expand-dabbrev-visible
            try-expand-dabbrev-all-buffers
            try-expand-dabbrev-from-kill
            try-complete-file-name
            try-complete-file-name-partially
            try-complete-lisp-symbol
            try-complete-lisp-symbol-partially
            try-expand-whole-kill))
(autoload 'comint-dynamic-complete "comint" "Complete for file name" t)
(setq comint-completion-addsuffix '("/" . ""))
(setq-default indent-tabs-mode nil)

(defalias 'perl-mode 'cperl-mode)
(defun pde-perl-mode-hook ()
  (abbrev-mode t)
  (add-to-list 'cperl-style-alist
               '("PDE"
                 (cperl-auto-newline                         . t)
                 (cperl-brace-offset                         . 0)
                 (cperl-close-paren-offset                   . -4)
                 (cperl-continued-brace-offset               . 0)
                 (cperl-continued-statement-offset           . 4)
                 (cperl-extra-newline-before-brace           . nil)
                 (cperl-extra-newline-before-brace-multiline . nil)
                 (cperl-indent-level                         . 4)
                 (cperl-indent-parens-as-block               . t)
                 (cperl-label-offset                         . -4)
                 (cperl-merge-trailing-else                  . t)
                 (cperl-tab-always-indent                    . t)))
  (cperl-set-style "PDE"))

(global-set-key (kbd "C-c s") 'compile-dwim-compile)
(global-set-key (kbd "C-c r") 'compile-dwim-run)
(setq compilation-buffer-name-function 'pde-compilation-buffer-name)
(autoload 'compile-dwim-run "compile-dwim" "Build and run" t)
(autoload 'compile-dwim-compile "compile-dwim" "Compile or check syntax" t)
(autoload 'executable-chmod "executable"
          "Make sure the file is executable.")

(defun pde-perl-mode-hook ()
   ;; chmod when saving
  (when (and buffer-file-name
        (not (string-match "\\.\\(pm\\|pod\\)$" (buffer-file-name))))
      (add-hook 'after-save-hook 'executable-chmod nil t))
  (set (make-local-variable 'compile-dwim-check-tools) nil))
(global-set-key (kbd "C-c s") 'compile-dwim-compile)
(global-set-key (kbd "C-c r") 'compile-dwim-run)
(setq compilation-buffer-name-function 'pde-compilation-buffer-name)
(autoload 'compile-dwim-run "compile-dwim" "Build and run" t)
(autoload 'compile-dwim-compile "compile-dwim" "Compile or check syntax" t)
(autoload 'executable-chmod "executable"
          "Make sure the file is executable.")

(defun pde-perl-mode-hook ()
   ;; chmod when saving
  (when (and buffer-file-name
        (not (string-match "\\.\\(pm\\|pod\\)$" (buffer-file-name))))
      (add-hook 'after-save-hook 'executable-chmod nil t))
  (set (make-local-variable 'compile-dwim-check-tools) nil))
(global-set-key (kbd "C-c i") 'imenu)
(global-set-key (kbd "C-c v") 'imenu-tree)
(global-set-key (kbd "C-c j") 'ffap)
(setq tags-table-list '("./TAGS" "../TAGS" "../../TAGS"))
(autoload 'imenu-tree "imenu-tree" "Show imenu tree" t)
(setq imenu-tree-auto-update t)
(eval-after-load "imenu"
 '(defalias 'imenu--completion-buffer 'pde-ido-imenu-completion))
(autoload 'tags-tree "tags-tree" "Show TAGS tree" t)
;; A wonderful minibuffer completion mode
(partial-completion-mode 1)
(setq PC-include-file-path
      (delete-dups (append PC-include-file-path pde-perl-inc)))
(setq ffap-url-regexp
      (concat
       "\\`\\("
       "news\\(post\\)?:\\|mailto:\\|file:" ; no host ok
       "\\|"
       "\\(ftp\\|https?\\|telnet\\|gopher\\|www\\|wais\\)://" ; needs host
       "\\)[^:]" ; fix for perl module, require one more character that not ":"
       ))
(add-to-list 'ffap-alist  '(cperl-mode . pde-ffap-locate))

;; Rebinding keys for hideshow
(require 'hideshow)
(define-key hs-minor-mode-map "\C-c\C-o"
  (let ((map (lookup-key hs-minor-mode-map "\C-c@")))
    ;; C-h is help to remind me key binding
    (define-key map "\C-h" 'describe-prefix-bindings)
    (define-key map "\C-q" 'hs-toggle-hiding)
    ;; compatible with outline
    (define-key map "\C-c" 'hs-hide-block)
    (define-key map "\C-e" 'hs-show-block)
    map))
(global-set-key (kbd "C-c h") 'help-dwim)
(setq cperl-lazy-help-time 2)
(defun pde-perl-mode-hook ()
   (cperl-lazy-install))
(autoload 'run-perl "inf-perl" "Start perl interactive shell" t)
(autoload 'perldb-ui "perldb-ui" "perl debugger" t)

---

