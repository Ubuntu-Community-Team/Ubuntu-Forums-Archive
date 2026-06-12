---
title: "Emacs lisp ?"
date: 2009-12-03
forum: Programming Talk
---

### Post by Barriehie on 2009-12-03
So I've got tramp up and working and was wondering if there's a way to change the face-background for the ssh buffer.  I've googled and searched to no avail.  I'm thinking there's perhaps a variable that can be tested to change the face???

TIA,
Barrie

Edit: Still digging, something like this, which doesn't work...

```

(if ($USER-LOGIN '<root@localhost>)
    (mode-line ((t (:background "Red")))))

```

---

### Post by Barriehie on 2009-12-05
Gottit!  This is in my .emacs-custom.el file and it works.

```

(defun my-tramp-header-line-function ()
    (when (string-match "^/ssh.*$" default-directory)
    (setq header-line-format
	  (format-mode-line "----- THIS BUFFER IS VISITED WITH ROOT  
PRIVILEGES -----"
			    'font-lock-warning-face)))
                            '(mode-line ((t (:background "Red")))))

```

Alternatively this will open a new frame when F5 is pressed.

```

;; F5 Opens a new frame for SSH login.
(global-set-key [(f5)] (lambda() 
     (interactive)(find-file-other-frame "/ssh:root@localhost:")))

```

Barrie

---

### Post by jpkotta on 2009-12-05
Wouldn't you want "root" in that regexp?  It's going to tell you that any ssh tramp buffer has root permissions.

I have a similar thing for editing files with sudo+tramp:
```

(defface find-file-root-header-face
  '((t (:foreground "white" :background "red3")))
  "*Face use to display header-lines for files opened as root.")

(defun find-file-root-header-warning ()
  "*Display a warning in header line of the current buffer.
   This function is suitable to add to `find-file-hook'."
  (require 'tramp)
  (when (and (tramp-tramp-file-p (or buffer-file-name
                                     dired-directory))
             (string= tramp-current-user "root"))
    (let* ((warning "WARNING: EDITING FILE AS ROOT!")
           (space (+ 6 (- (window-width) (length warning))))
           (bracket (make-string (/ space 2) ?-))
           (warning (concat bracket warning bracket)))
      (setq header-line-format
            (propertize  warning 'face 'find-file-root-header-face)))))

(defun find-alternative-file-with-sudo ()
  (interactive)
  (let* ((bname (or buffer-file-name
                    dired-directory))
         (prefix "/sudo:root@localhost:")
         (prefix-re (concat "^" prefix))
         (pt (point)))
    (when bname
      (if (string-match prefix-re bname)
          (setq bname (replace-regexp-in-string prefix-re "" bname))
        (setq bname (concat prefix bname)))
      (find-alternate-file bname)
      (goto-char pt))))

;; normally this is bound to find-file-read-only
;; use M-x toggle-read-only instead
(global-set-key (kbd "C-x C-r") 'find-alternative-file-with-sudo)

(add-hook 'find-file-hook 'find-file-root-header-warning)
(add-hook 'dired-mode-hook 'find-file-root-header-warning)


```

---

### Post by Barriehie on 2009-12-05
> **jpkotta said:**
> Wouldn't you want "root" in that regexp?  It's going to tell you that any ssh tramp buffer has root permissions.

I have a similar thing for editing files with sudo+tramp:
```

(defface find-file-root-header-face
  '((t (:foreground "white" :background "red3")))
  "*Face use to display header-lines for files opened as root.")

(defun find-file-root-header-warning ()
  "*Display a warning in header line of the current buffer.
   This function is suitable to add to `find-file-hook'."
  (require 'tramp)
  (when (and (tramp-tramp-file-p (or buffer-file-name
                                     dired-directory))
             (string= tramp-current-user "root"))
    (let* ((warning "WARNING: EDITING FILE AS ROOT!")
           (space (+ 6 (- (window-width) (length warning))))
           (bracket (make-string (/ space 2) ?-))
           (warning (concat bracket warning bracket)))
      (setq header-line-format
            (propertize  warning 'face 'find-file-root-header-face)))))

(defun find-alternative-file-with-sudo ()
  (interactive)
  (let* ((bname (or buffer-file-name
                    dired-directory))
         (prefix "/sudo:root@localhost:")
         (prefix-re (concat "^" prefix))
         (pt (point)))
    (when bname
      (if (string-match prefix-re bname)
          (setq bname (replace-regexp-in-string prefix-re "" bname))
        (setq bname (concat prefix bname)))
      (find-alternate-file bname)
      (goto-char pt))))

;; normally this is bound to find-file-read-only
;; use M-x toggle-read-only instead
(global-set-key (kbd "C-x C-r") 'find-alternative-file-with-sudo)

(add-hook 'find-file-hook 'find-file-root-header-warning)
(add-hook 'dired-mode-hook 'find-file-root-header-warning)


```

Probably, I've been at this for days and when I started I could only spell lisp... :)  That's a quick and dirty to minimize any affects of me having no clue!  I tried via sudo and su, telnet, scp, and finally got ssh to work!  So far the only thing involved with ssh on this machine is tramp so a minimal regexp was all I was looking for.  I've since changed it to **"^/ssh:root.localhost.*$"**

In the last week or so I've discovered needs for gawk, regexp, lisp, side effects of slow work!  Once again ubuntu has provided me with more reading material... :)

Barrie

---

