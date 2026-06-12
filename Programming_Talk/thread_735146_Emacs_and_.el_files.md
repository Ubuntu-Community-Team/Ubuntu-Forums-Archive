---
title: "Emacs and .el files"
date: 2008-03-25
forum: Programming Talk
---

### Post by gnp421 on 2008-03-25
Hi,

I have a c-style.el file from my professor to use for a project. I can't for the like of me get emacs to work with it. I googled it, bought the O'rielly emacs book and nothing tells me what to do to get it to load it.
I would like to finish the project and use emacs.

I appreciate any help I can get. Thanks.

---

### Post by supirman on 2008-03-25
Well, one way is to edit the .emacs file in your home directory.  Add a line like

[PHP](load "/path/to/c-style")[/PHP]

I don't know what you have in that file, so  I  can't really assist much further than that.  If there are functions in that .el file, then you should now be able to call them with Alt+X nameoffunction.  

Perhaps post the contents of the .el file and then I can help more.

---

