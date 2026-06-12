---
title: "how do peple use emacs for c/c++ dev"
date: 2007-12-24
forum: Programming Talk
---

### Post by monkeyking on 2007-12-24
I've been using emacs for quite a few years programming in c and c++.

And I was just wondering how ppl use emacs, and what tools they like.

I like small fonts so I've got the following in my .emacs
```

(setq default-frame-alist '(
       (font . "6x10")
       (cursor-color . "gray25")
       (background-color . "white")
       (foreground-color . "black")
       (vertical-scroll-bars . left)
       (top . 0) (left . 0)
       (width . 98) (height . 90)
       )
)

```

Other than that, I've gotten used the the keyboardshorts. with the buffers.
c-x b, c-x c-b, c-x 1/2/3.

I haven't really bothered, using the debugger, since I never really used a debugger. I Just use gdb for tracking down sigsegv and sigfaults.
I use valgrind when I think my program is finished.

But occasionly I use the speedbar, but not so much.
I'm really missing the  folding feature of vim.

---

### Post by wolfbone on 2007-12-24
> **monkeyking said:**
> 
I'm really missing the  folding feature of vim.

Why? 

[http://www.emacswiki.org/cgi-bin/emacs-en/CategoryOutline](http://www.emacswiki.org/cgi-bin/emacs-en/CategoryOutline)

---

