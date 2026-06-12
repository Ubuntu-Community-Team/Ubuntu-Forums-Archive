---
title: "emacs .el file addon"
date: 2011-03-23
forum: Programming Talk
---

### Post by C0NFU53D2 on 2011-03-23
hello, i have just moved back to ubuntu after a long fast.
i have been useing unity on the school macs for some time now and i was trying to think of a way to begin coding at home with the unity API so i found this addon:

[http://blogs.unity3d.com/2010/01/15/emacs-mode-for-unity-javascript/](http://blogs.unity3d.com/2010/01/15/emacs-mode-for-unity-javascript/)

and i have sucessfully added it to my .emacs file:

(add-to-list 'load-path "~/.emacs.d")
;; UnityJS mode for emacs
(autoload 'unityjs-mode "unityjs-mode" "Major mode for editing Unity Javascript code." t)
(require 'unityjs-mode)

i get no errors when i start up emacs but i dont know how to make it work; i still get the regular screen in the editing part.  sorry i am new to emacs.

---

