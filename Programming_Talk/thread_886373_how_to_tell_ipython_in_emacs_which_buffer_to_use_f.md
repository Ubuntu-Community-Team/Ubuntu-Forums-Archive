---
title: "how to tell ipython in emacs which buffer to use for completion?"
date: 2008-08-11
forum: Programming Talk
---

### Post by phillies on 2008-08-11
Hi,

I'm quite new to emacs and like to use it as IDE for python. I use 3 buffers in emacs, the first split horizontally and the second vertically in the lower buffer. In the upper buffer there is the source code, in the lower left buffer is the ipython console (via M-x py-shell) and the lower right buffer is supposed to show the completion for the ipython shell and the code completion in the source code. But I don't know how to tell emacs that it should use this buffer. When I hit TAB in the ipython shell it always changes the upper buffer what really sucks cos there is my source code. 
The code completion in the source code buffer opens a new buffer on the bottom which would be acceptable for ipython as well, but changing my upper buffer is not an option. I looked for a "lock buffer" option but did not find any.

Does someone know how to handle this? Just to remind you - I have no clue about emacs, I use it for ~24hs now.

---

### Post by shifty2 on 2008-08-11
You could use "dedicated mode" for this. The code is available here: [http://groups.google.com/group/gnu.emacs.sources/msg/2efa106a0374df43](http://groups.google.com/group/gnu.emacs.sources/msg/2efa106a0374df43).


It means that a certain frame will become dedicated, so other buffers won't go into it. For example, if you do M-x dedicate in your shell buffer and your source code buffer, the only place for the completion buffer to go is in the place you want it to.

To use the code add this to your .emacs:
(load-file "/path/to/dedicated.el")

---

### Post by phillies on 2008-08-11
thx, this is exactly what I needed

---

