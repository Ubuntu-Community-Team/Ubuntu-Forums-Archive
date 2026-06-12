---
title: "JDEE + EMACS Integration."
date: 2006-07-04
forum: Programming Talk
---

### Post by elvin on 2006-07-04
Hi all


I am new to linux and trying to integrate the emacs with JDEE .However i cannot seee the JDE item. Please have a look at my .emacs file and see if u can find some bug..
Thankz


;; .emacs

;;; uncomment this line to disable loading of "default.el" at startup
 (setq inhibit-default-init t)

;;; My location for external packages.
(add-to-list 'load-path "~/.emacs.d/site-lisp/jde")
(add-to-list 'load-path "~/.emacs.d/site-lisp/cedet")
(add-to-list 'load-path "~/.emacs.d/site-lisp/elib")

;; Initialize CEDET
 (load-file "~/.emacs.d/site-lisp/cedet/common/cedet.el")

;; turn on font-lock mode
(when (fboundp 'global-font-lock-mode)
  (global-font-lock-mode t))

;; enable visual feedback on selections
;(setq transient-mark-mode t)

;; default to better frame titles
(setq frame-title-format
      (concat  "%b - emacs@" (system-name)))

;; default to unified diffs
(setq diff-switches "-u")

;; always end a file with a newline
;(setq require-final-newline 'query)

;;; Setup initial emacs frames (windows) location and size

(setq default-frame-alist
      '((wait-for-wm . nil)
	(top . 0) (left . 0)
	(width . 85) (height . 40)
	(background-color . "lightyellow")
	(foreground-color . "limegreen")
	(cursor-color . "red")
	(mouse-color . "black")
        ))
(setq initial-frame-alist
      '((top . 55) (left . 184)
        (width . 100) (height . 40)
        )
      )

;;; It is always better to know current line and column number
(column-number-mode t)
;;(line-number-mode t)

;; Sets the basic indentation for Java source files
;; to two spaces.
(defun my-jde-mode-hook ()
  (setq c-basic-offset 2))

(add-hook 'jde-mode-hook 'my-jde-mode-hook)

;; Set the debug option to enable a backtrace when a
;; problem occurs.
;;(setq debug-on-error t)

;;; Load all JDEE related libraries
;;; JDEE, documentation and file are located at:
;;; [http://jdee.sunsite.dk/](http://jdee.sunsite.dk/)
;;; To speed-up installation for JDEE beginners use:
;;(add-to-list 'load-path "~/.emacs.d/site-lisp/elib")
;;(add-to-list 'load-path "~/.emacs.d/site-lisp/eieio")
;;(add-to-list 'load-path "~/.emacs.d/site-lisp/semantic")
;;(add-to-list 'load-path "~/.emacs.d/site-lisp/speedbar")
;;(add-to-list 'load-path "~/.emacs.d/site-lisp/jde")

;;; I need support for my language "special" characters
;; (set-language-environment 'Polish)
;; (set-input-method 'latin-2-prefix)


;; Add current time to every new line
;;(erc-timestamp-mode t)

;;(setq load-path (cons "~/home/elisp" load-path))
;; If you want Emacs to defer loading the JDE until you open a 
;; Java file, edit the following line
;;(setq defer-loading-jde nil)
;; to read:
;;
;; (setq defer-loading-jde t)
;;
;;(autoload 'awk-mode "cc-mode" nil t)
;; Sets the basic indentation for Java source files
;; to two spaces.
;;(defun my-jde-mode-hook ()
 ;; (setq c-basic-offset 2))
;;(add-hook 'jde-mode-hook 'my-jde-mode-hook)

---

