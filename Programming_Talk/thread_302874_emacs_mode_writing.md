---
title: "emacs mode writing"
date: 2006-11-19
forum: Programming Talk
---

### Post by macsaint on 2006-11-19
Hello

I am writing an emacs mode for a house-made software at my company.

It seems to work, but the comment highlighting is not working.
/* blah blah */ or C in the first column need to be recognized
as comments.

Pls.. help me.

JW

;;; flex.el -- Major mode for editing flex input
;;(defvar flex-mode-syntax-table
;; (let ((st (make-syntax-table)))
;; (modify-syntax-entry ?* "" st)
;; st)
;; "Syntax table for `flex-mode'.")

(defvar flex-font-lock-keywords
`((,(concat "\\") (0 font-lock-keyword-face))
(,(concat "\\") (0 font-lock-function-name-face))
(,(concat "\\") (0 font-lock-string-face))
("\\s *@\\w+" (0 font-lock-function-name-face))
("\\b\\(left\\$\\)\\s *(" (1 font-lock-string-face))
("\\b\\(right\\$\\)\\s *(" (1 font-lock-string-face))
)
"Keyword highlighting specification for `flex-mode'.")

(define-derived-mode flex-mode fundamental-mode "FLEX"
"A major mode for editing .flex files."
(make-local-variable 'comment-start)
(setq comment-start "/* ")
(make-local-variable 'comment-end)
(setq comment-end " */")
(set (make-local-variable 'font-lock-defaults)
'(flex-font-lock-keywords))
)

(setq major-mode 'flex-mode)
(setq mode-name "FLEX")
(local-set-key "\t" " ") ;; define tab key
(run-hooks 'flex-mode-hook)

(provide 'flex-mode)

---

