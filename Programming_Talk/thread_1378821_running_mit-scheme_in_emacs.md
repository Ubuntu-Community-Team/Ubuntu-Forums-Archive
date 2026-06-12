---
title: "running mit-scheme in emacs"
date: 2010-01-11
forum: Programming Talk
---

### Post by badperson on 2010-01-11
Hi,
I downloaded the code for mit-scheme and installed it no problem. I was able to run it by opening emacs and typing ```
M-x run-scheme
```

Then I'm able to do some simple stuff like
```
(+ 2 2)
```
which returns 
```

;Value: 4

1 ]=> 
```

how do i save code in a file and run it in emacs? I'm looking at the [online docs ]("http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-user/GNU-Emacs-Interface.html#GNU-Emacs-Interface")and I don't see instructions for that. I'll probably come across it at some point, but was wondering if anyone could point me in the right direction. 
bp

---

### Post by cyberslayer on 2010-01-12
In scheme-mode, C-h b should give you the full list of keybindings (search for scheme in the buffer that comes up).

---

### Post by nvteighen on 2010-01-12
Just create a new file, code and when you want to test it, save it and use C-c C-l (or the "Load File" option in menu) to load it into the Scheme interpreter. Moreover, if the Scheme interpreter isn't running, the C-c C-l command will ask you to start it or not.

---

