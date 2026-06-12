---
title: "Emacs: set-background-color for ALL frames"
date: 2009-05-29
forum: Programming Talk
---

### Post by Markhor on 2009-05-29
Hello. I have (set-background-color #123456) set in my .emacs file. 

Unfortunately, when I C-x 5 2 to open a new frame,
 the new frame still has the default white background color.

 I have searched for this answer extensively, but have not found the solution. Does anyone know how to set the background color for ALL frames? Thanks.

---

### Post by johnl on 2009-05-29
I have the following in my .emacs  which I believe solves this issue -- set your colors appropriately.

```

(setq default-frame-alist
      (append default-frame-alist
       '((foreground-color . "Black")
 (background-color . "White")
 (cursor-color . "SkyBlue")
 )))

```

Hope this fixes the issue.

---

### Post by bajhn on 2011-04-08
JohnL, thanks! You helped me figure out how to solve my problem. Here are my embellishments. I put this in my .emacs file so that I can change the color of the current frame and all future frames in my session at the push of a button. The color may not be the best, but my color vision is not normal.

[FONT=Courier New](defun set-my-frame-options ()
  "Set frame color so I can distinguish between two sessions."
  (interactive)
  (setq my-bgcolor "LightCyan2")
  (setq default-frame-alist
    ; For a reason I do not understand, Lisp fusses about the parameter
    ; type in background-color below if I substitute (unquoted) my-bgcolor.
    (append default-frame-alist
        '((background-color . "LightCyan2")
        )
    )
  )
  (set-background-color my-bgcolor)

)

(global-set-key [f10] 'set-my-frame-options)
[/FONT]

---

