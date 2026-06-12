---
title: "Emacs Syntax Highlight"
date: 2006-01-16
forum: Programming Talk
---

### Post by wizzkid on 2006-01-16
I tried to use emacs and I find it good but kinda confusing, guess i have to get used to it.   one thing is I open a .py file, but the sytax is not highlighted, even .php..

In option. Syntax highlighting, active global highlighting,  parent match highlighting iare ticked

thnks

---

### Post by toojays on 2006-01-16
Perhaps the correct mode is not being loaded. What modes does the mode-line say you are using? Do you get syntax highlighting if you edit a C file?

For Python files, you should install python-mode. There would be a mode for PHP somewhere, but I don't know if it's in synaptic.

---

### Post by wizzkid on 2006-01-16
Yes In C its working. okay I will check on synaptics :) thanks a lot.

---

### Post by Wallakoala on 2006-01-16
You need to install python-mode for emacs via synaptic. Then it should work.

---

### Post by wizzkid on 2006-02-05
HI, I re-install my Kubuntu together with all the applications. 

Then Emacs was re-install.. now the syntax highlight does not work. I already installed the python-mode and php-mode, but doesnt help.. any clue on this?

---

### Post by beewer on 2006-05-28
Hi. 

I have also same problem. Emacs doesn't show any syntax highlight for python code. I have installed python-mode but it didn't help.

Any ideas what would help? Should I put some options to my ~/.emacs?

-b

---

### Post by lucnoc on 2006-06-03
You need to enable syntax highlighting: 

* from the menu bar: Options->Syntax Highlighting (Global Font Lock Mode).
* or M-x global-font-lock-mode

You may want also to save this setting in the .emacs or using Options->Save Options.

Hope that helps.
Cheers
l
--

---

### Post by kiwibird on 2006-06-13
I believe you need to put this into your .emacs:

```
(require 'php-mode)
(require 'python-mode)
```

And of course, save the settings after turning on global font lock mode (which'll put a customize-section into your .emacs).

---

