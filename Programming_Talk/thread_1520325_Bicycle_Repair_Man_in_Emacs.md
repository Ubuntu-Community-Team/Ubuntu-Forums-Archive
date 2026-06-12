---
title: "Bicycle Repair Man in Emacs"
date: 2010-06-29
forum: Programming Talk
---

### Post by lykwydchykyn on 2010-06-29
Has anyone got Bicycle repair man working in Emacs?  I followed the directions in the README.emacs file that comes with it, but this line:
```

(pymacs-load "bikeemacs" "brm-")

```

is causing an error when I eval my .emacs file:
```

Python:  Emacs:  "(void-variable python-mode-map)"

```

Has anyone got this working?  If so, can I see the relevant commands in your config?

BTW, I tried this both with the snapshot and the stable v23 from the repos.

---

### Post by jpkotta on 2010-07-02
You need pymacs, which is in the repos.

You need python-mode.el in your load-path.  python-mode.el is not included in Emacs, but a different, incompatible python mode, python.el, is.  So you need to make sure that Emacs uses python-mode.el instead.

```

(autoload 'python-mode "python-mode.el")
(add-to-list 'auto-mode-alist '("\\.py\\'" . python-mode))

```

Apparently, BRM is confused about what python-mode calls the keymap.

```

(defvaralias 'py-mode-map 'python-mode-map)

```

Then of course the code from the BRM README.

---

### Post by lykwydchykyn on 2010-07-02
Thanks for the help!
> **jpkotta said:**
> You need pymacs, which is in the repos.

Got it; I have ropemacs working with it successfully
> 
You need python-mode.el in your load-path.  python-mode.el is not included in Emacs, but a different, incompatible python mode, python.el, is.  So you need to make sure that Emacs uses python-mode.el instead.

```

(autoload 'python-mode "python-mode.el")
(add-to-list 'auto-mode-alist '("\\.py\\'" . python-mode))

```

Is this found in the python-mode package in the repos?  If so, I have that. 

I have these lines in my .emacs, which I found in some tutorial or other, but I don't know if they effectively do what I need:
```

(setq auto-mode-alist (cons '("\\.py$" . python-mode) auto-mode-alist))
(autoload 'python-mode "python-mode" "Python editing mode." t)
(setq interpreter-mode-alist(cons '("python" . python-mode)
                             interpreter-mode-alist))

```


> 
Apparently, BRM is confused about what python-mode calls the keymap.

```

(defvaralias 'py-mode-map 'python-mode-map)

```

Then of course the code from the BRM README.

If you have this working, would you be so kind as to post the relevant segment of your .emacs file?

---

