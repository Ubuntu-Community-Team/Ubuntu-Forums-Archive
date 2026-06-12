---
title: "Emacs: Disabling auto-fill-mode with local file variables?"
date: 2011-03-02
forum: Programming Talk
---

### Post by jazzgossen on 2011-03-02
I normally have auto-fill-mode turned on for text files (from my .emacs). However, now I'm working on a text document together with another author, and the extra line breaks inserted by auto-fill-mode makes it ugly for him. So I want to use visual-line-mode and turn off auto-fill-mode for this file. I'm trying to do it with local variables like so:
%% Local variables:
%% mode: visual-line
%% eval: auto-fill-mode
%% mode: whitespace-newline
%% End:
I thought that eval-ing auto-fill-mode after loading the file would toggle it to turn it off, but that doesn't work.

Is there another way to do it?

---

### Post by jpkotta on 2011-03-02
```
eval: (auto-fill-mode -1)
```

In general, almost all minor modes are disabled this way, and enabled with ```
(auto-fill-mode 1)
``` and toggled with ```
(auto-fill-mode)
```

---

