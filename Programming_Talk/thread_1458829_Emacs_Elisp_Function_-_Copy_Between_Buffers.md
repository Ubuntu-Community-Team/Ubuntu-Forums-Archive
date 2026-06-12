---
title: "Emacs Elisp Function - Copy Between Buffers"
date: 2010-04-20
forum: Programming Talk
---

### Post by covertcj on 2010-04-20
Hi,
I have been trying to rewrite an emacs macro given to me by my college professor. Essentially, the macro copies all text from the current parenthesis to it's matching parenthesis and copies the text to a scheme language buffer; however, it requires a specific emacs window setup: two buffers, one with source code and one running scheme. I am looking to increase the functionality to allow the code to switch directly to the buffer labeled *scheme* and switch back to the buffer that the cursor started in.

I know that I might be able to use "C-x b" to switch the buffer to *scheme*, but do not know how to implement that into the following line of code. I also do not know where to begin for switching back to the start window.

```
(fset 'send-to-scheme
   [?\C-  escape ?\C-f escape ?w ?\C-x ?o ?\C-y return ?\C-x ?o ?\C-e right])

(global-set-key "^Xx" 'send-to-scheme)
```

?\C- : Start Marking
escape ?\C-f: Move to the matching parenthesis
escape ?w: copy the marked text
?\C-x ?o: switch to the next frame
?\C-y: paste the text
return: add in a new line
?\C-x ?o: switch to the next window (ideally the original window)
?\C-e: move to the end of the line
right: move to the next line

Could someone help me expand this functionality?

Thanks,
Chris

---

