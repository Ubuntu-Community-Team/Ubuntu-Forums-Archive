---
title: "emacs fullscreen woes"
date: 2008-12-23
forum: Programming Talk
---

### Post by stairwayoflight on 2008-12-23
Hello,

I am using emacs-snapshot-gtk with Intrepid. I used to be able to get emacs to open fullscreen. At times it would fail to show the minibuffer.

After I did (desktop-save-mode 1) in my .emacs, ever since I can't get fullscreen anymore. I have used a few of the procedures from the wiki, including wmctrl, and even the gnome version which just uses gnome's keyboard shortcuts to get emacs into fullscreen.

Basically my .emacs used to invoke a fullscreen emacs. Now it tries, and gives me fullscreen with a missing minibuffer (I think its "below" the visible screen somewhere). If I hit F11, fullscreen is toggled off. If I hit F11 a second time, emacs appears to be displaying correctly in fullscreen.

This behavior was consistent through the various procedures I tried in my .emacs from [http://www.emacswiki.org/emacs/FullScreen]("http://www.emacswiki.org/emacs/FullScreen").

The missing minibuffer problem only occured after I had added (desktop-save-mode 1) to my .emacs. Now that I have commented that line, and deleted the .emacs.desktop files it created, I am still left with a non-fullscreen emacs.

I am running a fresh install of Intrepid on my core duo laptop with a 1280x800 display. I can post my unmodified xorg.conf if necessary. For completeness, here is my .emacs:

```
;;;; My humble .emacs

;;; Some stuff

;; Get rid of the startup screen
(setq inhibit-startup-message t)

;; Get back font antialiasing
(push '(font-backend xft x) default-frame-alist)

;; Get rid of toolbar, scrollbar, menubar
(progn
  (tool-bar-mode)
  (menu-bar-mode)
  (scroll-bar-mode))

;; Get fullscreen with F11, set it by default
;(defun switch-full-screen ()
;  (interactive)
;  (shell-command "wmctrl -r :ACTIVE: -btoggle,fullscreen"))

(global-set-key [f11] 'switch-full-screen)
    (defun fullscreen ()
      (interactive)
      (set-frame-parameter nil 'fullscreen
                           (if (frame-parameter nil 'fullscreen) nil 'fullboth)))

    (global-set-key [f11] 'fullscreen)
(fullscreen)

;; Save the desktop on a per-directory basis
;(desktop-save-mode 1)
```

Any help would be appreciated, thank you.

Stairwayoflight

---

### Post by Cracauer on 2008-12-26
I think that Debian and hence Ubuntu managed to break the signals for the resizing. I have seen this for a few weeks now, on multiple machines, with Debian and ubuntu. Resizing xterms makes emacs and possibly other applications sometimes get the right geometry, sometimes it doesn. Just resizing a couple times in a row eventually sees emacs with the right window size.

The breakage could be in a number of places.

Are other curses applications such as mutt broken?

What does "resize" in the terminal window say, does it report correctly?

---

### Post by unutbu on 2008-12-26
Have you tried moving the full screen code to the top of your .emacs file? I tried your .emacs file on an Intrepid system with emacs-snapshot, and this seemed to fix the problem -- at least for me. (Without the change, emacs-snapshot opened with a slightly wrong size. But unlike you, I could see the minibuffer.)

PS: I also use fvwm and devilspie as my window manager / window placer. If you find the above does not fix the problem for you, then tell us which window manager you use, since this might also be affecting the behavior.

---

### Post by Cracauer on 2008-12-26
I don't have any special emacs code for fullscreen. It just broke from some OS upgrades.

I also noticed that things are broken when re-assiging screen sessions from one terminal to another of a different size. So it is not the window manager that is b0rked.

---

### Post by stairwayoflight on 2008-12-29
I am simply using Gnome, with Intrepid Desktop.

I have placed the code everywhere. Suddenly I find I am unable to reproduce the problem. I have been fussing with a second display though, so it may have changed some settings somewhere.

---

