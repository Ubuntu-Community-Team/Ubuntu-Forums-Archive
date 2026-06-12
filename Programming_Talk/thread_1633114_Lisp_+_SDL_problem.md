---
title: "Lisp + SDL problem"
date: 2010-11-28
forum: Programming Talk
---

### Post by maximinus_uk on 2010-11-28
Here's a change from the usual Java / C++ / Python questions: a Lisp issue.

Currently I'm working with Lisp and SDL using the Lispbuilder-SDL library. However, I'm having 2 issues, namely:

1: sdl:render-string-blended ALWAYS returns nil, and not a new surface :( draw-string-blended works just fine though, so the ttf font and everything else is fine.

OK, so not to be outdone, I quickly wrote a new function that does what render-string-blended does:

```
(defun draw-blended-string (string colour)
  ;; a work-around for the buggy version of render-string-blended
  (let ((image (sdl:create-surface 
                 (sdl:get-font-size string :size :w :font (main-font *gfx*) :alpha 0)
	         (sdl:get-font-size string :size :h :font (main-font *gfx*)))))
    (sdl:draw-string-blended-* string 0 0 :surface image :font (main-font *gfx*) :color colour)
    image))
```

2: Which gives problem 2 - this returns an image with nothing on it! And it seems that all the settings of :alpha, :pixel-alpha that I use to get on sdl:create-surface seem to make no difference! However, when I draw a regular texture on the new image, it works just fine - only the blended string fails :(

Has anybody got any idea as to what to try next?

---

### Post by worseisworser on 2010-11-29
I'd try asking in #lispgames on the Freenode IRC network; I know some of the people there use LispbuilderSDL.

---

