---
title: "[SOLVED] Line numbers in emacs"
date: 2008-05-19
forum: Programming Talk
---

### Post by SteveNorman on 2008-05-19
I dont know why I cant figure this out,,

how do you use line numbering in emacs for writing scrips and programs?
As in 
#!/bin/sh
1 some code
2 some more code 
3 done

Can this be done in emacs?

---

### Post by gug@fnal.gov on 2008-05-19
I don't know about prefixing each line in emacs, but there is line numbering mode available which will tell you what line your cursor is on. It is <meta-x> line-number-mode. To activate it hit "alt" and "x" keys at the same time, then type "line-number-mode" followed by return.

---

### Post by LaRoza on 2008-05-19
[http://blogs.vislab.usyd.edu.au/index.php/Steve/2005/08/31/visible_line_numbers_in_emacs](http://blogs.vislab.usyd.edu.au/index.php/Steve/2005/08/31/visible_line_numbers_in_emacs)

Just googled "line numbers in emacs"

---

### Post by SteveNorman on 2008-05-19
I saw that one,,you have to add the lisp code to do it right? I am new to emacs and programming in general. I was hoping there was something already built into emacs.

---

### Post by SteveNorman on 2008-05-22
In still to noob to figure out the emacs, hack. But in vim its just :set nu

so I guess Im a vi man for now,

---

### Post by a9bejo on 2008-05-23
> **SteveNorman said:**
> I saw that one,,you have to add the lisp code to do it right? I am new to emacs and programming in general. I was hoping there was something already built into emacs.

Patching Emacs (with your own code or with code taken from the community)  is the whole point about using emacs in the first place. With Emacs, there is no difference between something added by its core developers and something you added yourself. After you added the new code to your configuration, it becomes a full part of the Editor, just as if it was a buildin feature.  

So the natural way to use Emacs is to first build a taylor-made configuration that makes Emacs exactly the Editor you want, and then backup that configuration somewhere, updating it as your requirements change. If you just want a editor that works out of the box and does most of the things that you want to do, Vim is probably a better option.

Read [An Introduction to all these articles](http://blog.bookworm.at/2007/03/introduction-to-all-these-emacs.html) for a more detailed explanation of how Emacs is fundamentally different from texteditors like Kate or Vim.

---

### Post by SteveNorman on 2008-05-23
Thanks,,I get lost trying to patch emacs. Im sure as I get more experience I will be able to. I was hoping someone would walk me through it. I just need more time. I have bookmarked your blog for future study, Thank you for writing that, it is thorough and well thought out! After my head clears a little from introductory c++ I will come back to emacs and dig into it.


Right now I am learning c++, basic unix commands, and shell scripting purely from tutorials, so having to learn how to patch emacs has been slowing me down. I have read quit a bit about the emacs/vi camps and the benefits of each. Learning linux and some programming is proving to be a mouthful; my time is stretched thin as it is, so any additional subjects to me right now are starting to feel overwhelming.

Thank you for your help!

---

### Post by Alasdair on 2008-05-23
M-x linum-mode is what you want. I'm not sure if Emacs 22 has it built in (I'm using Emacs 23 from CVS), but if you don't have it you can get it [here]("http://stud4.tuwien.ac.at/~e0225855/linum/linum.html")

Also see: [http://www.emacswiki.org/cgi-bin/wiki/LineNumbers]("http://www.emacswiki.org/cgi-bin/wiki/LineNumbers")

---

### Post by SteveNorman on 2008-05-23
I dont know how to do:


Copy the appropriate linum.el to your load-path and add to your .emacs:

      (require 'linum)
    

thats the thing Im having a hard time with. Your dealing with a noob here,,sorry

---

### Post by Alasdair on 2008-05-23
The load-path is simply a list of directories that Emacs will search for files in when you try to load an elisp file (like linum.el). Your .emacs file is the file in your home directory that Emacs loads on startup (if you don't have one make it!:)).

So say you downloaded linum.el to your home directory, you could add the following to your .emacs file:
```

(add-to-list 'load-path "/home/your-user-name/")
(require 'linum)

```
And then you can start linum-mode in a buffer via M-x linum-mode, or turn it on for all buffers by adding (global-linum-mode 1) to your .emacs.

---

### Post by LaRoza on 2008-05-23
> **SteveNorman said:**
> I have read quit a bit about the emacs/vi camps and the benefits of each. 

Vim is the better editor (arguably, the only editor of those two).

---

### Post by a9bejo on 2008-05-23
If you got the emacs-snapshot-gtk package installed, you already have linum-mode installed. Simply start emacs and type Alt-x SPACE linum-mode RETURN. If you always want line numbers in your code, you can open a file in your hme directory called .emacs and put the following line there:

```

(linum-mode)

```


As for  "Copy BLABLA.el to your load-path and add (require xxx) to your .emacs": This basically means that you will need to add 2 lines of code to a file in your home directory called .emacs : One to tell emacs to load the file at startup, and the other to say that you will actually need the stuff in the file in your editing session.

```

(add-to-list 'load-path "/path/to/linum.el")
(require 'linum)

```

Personally, I wrote myself a function that automatically loads every file in a directory into the load path.  Everytime I find a new piece of lisp code, I simply copy the file to that directory and add the require line to the .emacs file.


Here is the code that does this: You can put it in your .emacs, and it will load everything in the folder "site-lisp":
```

(defun cc-add-to-load-path-recursive (root-dir)
  "add each file in root-dir and its subdirectories to the load-path"
  (let* ((dir (expand-file-name root-dir))
         (default-directory dir))
    (when (file-directory-p dir)
      (add-to-list 'load-path dir)
      (if (fboundp 'normal-top-level-add-subdirs-to-load-path)
          (normal-top-level-add-subdirs-to-load-path)))) )

(cc-add-to-load-path-recursive "~/emacs.d/site-lisp") ; third-party stuff

```

However, if you stay with Emacs, it will definitely require some of your time in the next weeks if not months. So maybe it is better to do what you wrote earlier, and [learn Emacs](http://www.gnu.org/software/emacs/emacs-lisp-intro/) at a later time.


Oh, and do not listen to what La Roza says. He [will be punished for his blasphemy ](http://www.dina.kvl.dk/~abraham/religion/prophesy.html) when the time is right ;)

---

### Post by LaRoza on 2008-05-23
> **a9bejo said:**
> 
Oh, and do not listen to what La Roza says. He [will be punished for his blasphemy ](http://www.dina.kvl.dk/~abraham/religion/prophesy.html) when the time is right ;)

Will He now? ;)

---

### Post by SteveNorman on 2008-05-23
lol,,

thanks guys!

---

### Post by Wybiral on 2008-05-24
> **LaRoza said:**
> Vim is the better editor (arguably, the only editor of those two).

The only people who like vim better than emacs are the people who don't know how to use emacs :P

---

### Post by LaRoza on 2008-05-24
> **Wybiral said:**
> The only people who like vim better than emacs are the people who don't know how to use emacs :P

The only people who believe that are those that haven't met all of those that like Vim better than Emacs.

---

### Post by Lau_of_DK on 2008-05-24
> **Wybiral said:**
> The only people who like vim better than emacs are the people who don't know how to use emacs :P

I haven't tried Vim, but I'll take this as an oppertunity to do so. 

I tried a combination of Emacs+Slime for coding Lisp and its got to be the least assistive editors I've ever tried. For formatting, you get no help, for debugging, no help. The Lisp diehards will be quick to point out "oh, but you get an ASM print out of your code", ok, so what? You think I want to spend 2½ hours understanding my own code in Asm to find an extra comma somewhere? :)


Any recommended starting points for vim? Plugins, integrations with certain languages, something?

/Lau

---

### Post by a9bejo on 2008-05-24
> **Lau_of_DK said:**
> 
For formatting, you get no help.

Hmm, Emacs formats lisp code just fine. 


I don't use slime, but Emacs and Vim are not IDEs, but text editors.
Since they are also software platforms,  they can be extended by applications like SLIME to act like an IDE in many ways, and do stuff like integrating debuggers into the System. But how good this works depends on the quality of the IDE-extension and not necessarily on the software platform.  It is like blaming Eclipse if Flexbuilder or the JBoss IDE are missing something, or GTK+ if Pidgin lacks a feature you need.

> **Lau_of_DK said:**
> 
Any recommended starting points for vim? Plugins, integrations with certain languages, something?


[http://vim.sourceforge.net/](http://vim.sourceforge.net/)

As for common lisp plugins for vim, visit the common lisp wiki:

[http://www.cliki.net/development](http://www.cliki.net/development)

---

### Post by LaRoza on 2008-05-24
> **Lau_of_DK said:**
> I haven't tried Vim, but I'll take this as an oppertunity to do so. 

I tried a combination of Emacs+Slime for coding Lisp and its got to be the least assistive editors I've ever tried. For formatting, you get no help, for debugging, no help. The Lisp diehards will be quick to point out "oh, but you get an ASM print out of your code", ok, so what? You think I want to spend 2½ hours understanding my own code in Asm to find an extra comma somewhere? :)

Any recommended starting points for vim? Plugins, integrations with certain languages, something?

/Lau

I can't believe I am saying this, but I think you missed something with Emacs. It can do everything even beyond text editing.

My wiki has a section for Vim. For Ubuntu, use "sudo aptitude install vim" first.

---

### Post by bonfire89 on 2010-03-25
> **Alasdair said:**
> The load-path is simply a list of directories that Emacs will search for files in when you try to load an elisp file (like linum.el). Your .emacs file is the file in your home directory that Emacs loads on startup (if you don't have one make it!:)).

So say you downloaded linum.el to your home directory, you could add the following to your .emacs file:
```

(add-to-list 'load-path "/home/your-user-name/")
(require 'linum)

```
And then you can start linum-mode in a buffer via M-x linum-mode, or turn it on for all buffers by adding (global-linum-mode 1) to your .emacs.

Thank You!!! :D

---

### Post by Barriehie on 2010-03-28
Here's my .emacs-custom.el loaded from ~/.emacs.  F2 will toggle the line numbers.  Have to look; it's specific to my dir. structure.

.emacs
```

(setq custom-file1 "/home/barrie/emacs/barrie-start/.emacs-custom.el")
(load custom-file1)
```


.emacs-custom.el
```

;;
;; .emacs-custom.el
;;

;; Start the server
(server-start)

;; filename in the title bar, buffer name if no filename
(setq frame-title-format '(buffer-file-name "%f" ("%b")))

;; Add to the load path
(add-to-list 'load-path (expand-file-name "~/emacs/barrie-start"))
(require 'multi-scratch)
(autoload 'awk-mode "cc-mode" nil t)

;; Line number(s) M-x lineno-minor-mode <RET>
(add-to-list 'load-path (expand-file-name "~/emacs/barrie-start"))
(require 'lineno)

;; Templates
(require 'autoinsert)
    (auto-insert-mode)  ;;; Adds hook to find-files-hook
    (setq auto-insert-directory "~/emacs/.templates/") ;;; Or use custom, *NOTE* Trailing slash important
    (setq auto-insert-query nil) ;;; If you don't want to be prompted before insertion
    (define-auto-insert "\.sh" "shell-template.sh")
    (define-auto-insert "\.gawk" "gawk-template.gawk")

;; Force shell to ansi colors / clean shell displays!
(autoload 'ansi-color-for-comint-mode-on "ansi-color" nil t)
(add-hook 'shell-mode-hook 'ansi-color-for-comint-mode-on)

;; Alias' via environment vars.
(setenv "myfile" "~/emacs/barrie-start/.emacs-custom.el")
(setenv "baseinit" "~/.emacs")

;; Use a color theme
(require 'color-theme)
(color-theme-clarity)
;;(color-theme-blue-sea)
(setq color-theme-is-global t)

;; Load Path Additions
(normal-top-level-add-to-load-path
     '("~/emacs" "~/emacs/el"))

;; Setup TRAMP mode
(setq tramp-default-method "ssh")
(setq tramp-default-user "root")
(setq tramp-default-host "localhost")
(setq tramp-shell-prompt-pattern "^.*>$")
(setq tramp-chunksize 500)

(defun my-tramp-header-line-function ()
;;    (when (string-match "^/ssh.*$" default-directory)
    (when (string-match "^/ssh:root.localhost.*$" default-directory)
    (setq header-line-format
	  (format-mode-line ">>-----> THIS BUFFER IS VISITED WITH ROOT PRIVILEGES <-----<<"
			    'font-lock-warning-face)))
                            '(mode-line ((t (:background "Red")))))

(add-hook 'find-file-hooks 'my-tramp-header-line-function)
(add-hook 'dired-mode-hook 'my-tramp-header-line-function)

;; TRAMP beep when done downloading files
(defadvice tramp-handle-write-region
            (after tramp-write-beep-advice activate)
           " make tramp beep after writing a file."
           (interactive)
           (beep))
          (defadvice tramp-handle-do-copy-or-rename-file
            (after tramp-copy-beep-advice activate)
           " make tramp beep after copying a file."
           (interactive)
           (beep))
          (defadvice tramp-handle-insert-file-contents
            (after tramp-copy-beep-advice activate)
           " make tramp beep after copying a file."
           (interactive)
           (beep))

;; F5 Opens a new frame for SSH login.
(global-set-key [(f5)] (lambda() 
     (interactive)(find-file-other-frame "/ssh:root@localhost:")))

;; Set ALL files to UNIX line endings
(add-hook 'find-file-hook 'find-file-check-line-endings)
(defun dos-file-endings-p ()
  (string-match "dos" (symbol-name buffer-file-coding-system)))
(defun find-file-check-line-endings ()
  (when (dos-file-endings-p)
    (set-buffer-file-coding-system 'iso-latin-1-unix t)
    (set-buffer-modified-p nil)))

;; To use manually: M-x doc-mode
;; a mode designed for editing text file documents that contain a lot
;; of text to spell check, etc.
(defun doc-mode ()
  (interactive)
  (text-mode)       ;; use regular text mode
  (auto-fill-mode))  ;; wrap lines
  ;; (refill-mode)  ;; wrap lines (more aggressive)
  ;;(flyspell-mode))  ;; underline misspelled words
                    ;; run M-x flyspell-buffer for it to underline all
                    ;; words in the file instead of the words your
                    ;; cursor moves over.

;; Modeline settings
;; Show 24-hour time and date on status bar
(setq display-time-24hr-format t)
(setq display-time-day-and-date t)
(display-time)

;; Turn on garbage collection messaging
(setq garbage-collection-messages t)

;; Highlight the current line
(global-hl-line-mode 1)

;; Show line and column number
(line-number-mode 1)
(column-number-mode 1)

;; Typing "yes" or "no" takes too long---use "y" or "n"
(fset 'yes-or-no-p 'y-or-n-p)

;; Don't beep at me
(setq visible-bell t)

;; default coding
(prefer-coding-system 'utf-8)

;; Goto column function
(defun goto-column-number (number)
"Untabify, and go to a column number within the current line (1 is beginning
of the line)."
(interactive "nColumn number ( - 1 == C) ? ")
(beginning-of-line)
(untabify (point-min) (point-max))
(while (> number 1)
 (if (eolp)
     (insert ? )
   (forward-char))
 (setq number (1- number))))

;; column numbers
(setq column-number-mode t)

;; Resize window on load
(setq initial-frame-alist
      `((left . 70) (top . 30)
;;        (width . 110) (height . 44)))
        (width . 109) (height . 47)))

;; for emacs to insert spaces instead of tab chars
(setq-default indent-tabs-mode nil);

;; Set the font
(set-default-font "-adobe-courier-bold-r-normal--14-100-100-100-m-90-iso8859-1")

;; Turn on the menu bar
(menu-bar-mode 1)

;; Turn off the tool bar
(tool-bar-mode 0)

;; disable splash screen and startup message
(setq inhibit-startup-message t)

;;  Global font lock mode ON
(global-font-lock-mode t)

;; No zoning!!!
;;(zone-when-idle 0)

;; Make the cursor blink
(blink-cursor-mode 1)

;; Line numbering macro
(fset 'linenumbers
   (lambda (&optional arg) "Keyboard macro." (interactive "p") (kmacro-exec-ring-item (quote ([134217848 115 101 116 110 117 45 109 111 100 101 return] 0 "%d")) arg)))

;; Bind to key F2
(global-set-key [f2] 'lineno-minor-mode)

;; save the editor state
;;(desktop-save-mode 1)
(desktop-save-mode 0)

;; Make emacs use the clipboard
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)

;; Use the Printing Package
(require 'printing)
(pr-update-menus)

;; set the PDF printer as default
;;(setq printer-name "CUPS-PDF")
;;(setq printer-name t)
(setq ps-printer-name "CUPS-PDF")
(setq ps-printer-name t)

(defun print-to-pdf ()
  (interactive)
  (ps-spool-buffer-with-faces)
  (switch-to-buffer "*PostScript*")
  (write-file "/tmp/tmp.ps")
  (kill-buffer "tmp.ps")
  (setq cmd (concat "ps2pdf14 /tmp/tmp.ps " (buffer-name) ".pdf"))
  (shell-command cmd)
  (shell-command "rm /tmp/tmp.ps")
  (message (concat "Saved to:  " (buffer-name) ".pdf"))
  )

;; Numbered Backups
(setq version-control t)
(setq backup-directory-alist '(("." . "/home/barrie/emacs/backups")))

(put 'upcase-region 'disabled nil)

;; Setup bookmarks file
(setq bookmark-default-file "~/.emacs.d/bookmarks" bookmark-save-flag 1)

(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(column-number-mode t)
 '(display-time-mode t)
 ;; '(fringe-mode 0 nil (fringe))
 '(fringe-mode 5 t (fringe))
 '(scroll-bar-mode (quote right))
 '(show-paren-mode t)
 '(size-indication-mode t)
 '(speedbar-frame-parameters (quote ((minibuffer) (width . 20) (border-width . 0) (menu-bar-lines . 0) (tool-bar-lines . 0) (unsplittable . t) (set-background-color "black"))))
 '(transient-mark-mode t))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(background "blue")
 '(font-lock-builtin-face ((((class color) (background dark)) (:foreground "Turquoise"))))
 '(font-lock-comment-face ((t (:foreground "MediumAquamarine"))))
 '(font-lock-constant-face ((((class color) (background dark)) (:bold t :foreground "DarkOrchid"))))
 '(font-lock-doc-string-face ((t (:foreground "green2"))))
 '(font-lock-function-name-face ((t (:foreground "SkyBlue"))))
 '(font-lock-keyword-face ((t (:bold t :foreground "CornflowerBlue"))))
 '(font-lock-preprocessor-face ((t (:italic nil :foreground "CornFlowerBlue"))))
 '(font-lock-reference-face ((t (:foreground "DodgerBlue"))))
 '(font-lock-string-face ((t (:foreground "LimeGreen"))))
 '(font-lock-type-face ((t (:foreground "#9290ff"))))
 '(font-lock-variable-name-face ((t (:foreground "PaleGreen"))))
 '(font-lock-warning-face ((((class color) (background dark)) (:foreground "yellow" :background "red"))))
 '(highlight ((t (:background "grey20"))))
 '(list-mode-item-selected ((t (:background "gold"))))
 '(makefile-space-face ((t (:background "wheat"))))
 '(mode-line ((t (:background "Navy"))))
 '(paren-match ((t (:background "darkseagreen4"))))
 '(region ((t (:background "DarkSlateBlue"))))
 '(show-paren-match ((t (:foreground "black" :background "wheat"))))
 '(show-paren-mismatch ((((class color)) (:foreground "white" :background "red"))))
 '(speedbar-button-face ((((class color) (background dark)) (:foreground "green4"))))
 '(speedbar-directory-face ((((class color) (background dark)) (:foreground "khaki"))))
 '(speedbar-file-face ((((class color) (background dark)) (:foreground "cyan"))))
 '(speedbar-tag-face ((((class color) (background dark)) (:foreground "Springgreen"))))
 '(vhdl-speedbar-architecture-selected-face ((((class color) (background dark)) (:underline t :foreground "Blue"))))
 '(vhdl-speedbar-entity-face ((((class color) (background dark)) (:foreground "darkGreen"))))
 '(vhdl-speedbar-entity-selected-face ((((class color) (background dark)) (:underline t :foreground "darkGreen"))))
 '(vhdl-speedbar-package-face ((((class color) (background dark)) (:foreground "black"))))
 '(vhdl-speedbar-package-selected-face ((((class color) (background dark)) (:underline t :foreground "black"))))
 '(widget-field ((((class grayscale color) (background light)) (:background "DarkBlue")))))

```

HTH

---

### Post by kevomac12 on 2010-04-02
I thank you all for your input on the line number display in Emacs.
I'd like to ask a follow on question... what if I've enabled the line-number-mode!
But I still cannot see the line number?

I found this info., but it's of no use as I don't know which 'Face' to go to!
[COLOR=Blue]If the buffer is very large (larger than the value of line-number-display-limit), then the line number doesn't appear. Emacs doesn't compute the line number when the buffer is large, because that would be too slow. Set it to nil to remove the limit. 
Line-number computation can also be slow if the lines in the buffer are too long. For this reason, Emacs normally doesn't display line numbers if the average width, in characters, of lines near point is larger than the value of the variable line-number-display-limit-width. The default value is 200 characters.

[COLOR=Black]Can I get some specific info. on where in emacs to change things so I get line numbers?

Kevin :redface:
[/COLOR][/COLOR]

---

### Post by jpkotta on 2010-04-05
> **kevomac12 said:**
> I thank you all for your input on the line number display in Emacs.
I'd like to ask a follow on question... what if I've enabled the line-number-mode!
But I still cannot see the line number?


line-number-mode just displays what line the point (the cursor) is on.  You want linum-mode (as explained earlier in the thread).

---

### Post by pootzko on 2010-04-05
for me (global-linum-mode 1) does nothing (and neither does (linum-mode) or (global-linum-mode) )... in fact if I issue M+x global-linum-mode after starting emacs it says "Global-linum-mode disabled." while it never actually was enabled (or at least didn't show any results?!)... and then when I issue the same command again, then the line numbers finaly show up..

but I want to emacs to automaticaly show the line numbers when it starts... 
what am I doing wrong? 

thank you

---

### Post by kevomac12 on 2010-04-05
M-x linum-mode [no match]

---

### Post by kevomac12 on 2010-04-05
linum-mode [no match]
Thanks but I don't seem to have this funcionality installed.

---

### Post by weezerBo on 2010-04-05
It's only included in emacs23 afaik.

---

### Post by jpkotta on 2010-04-06
It comes with Emacs 23, but still works with Emacs 22.  Just copy linum.el to somewhere in your load-path (I add ~/.emacs.d/ to my load-path and keep everything there).  Then 
```

(require 'linum nil 'noerror)
(when (featurep 'linum)
  (global-linum-mode 1))

```

(I like to use this more complicated require code because it doesn't cause errors when loading ~/.emacs.)

[http://www.emacswiki.org/emacs/LineNumbers#toc4](http://www.emacswiki.org/emacs/LineNumbers#toc4)
[http://stud4.tuwien.ac.at/~e0225855/linum/linum.html](http://stud4.tuwien.ac.at/~e0225855/linum/linum.html)

---

