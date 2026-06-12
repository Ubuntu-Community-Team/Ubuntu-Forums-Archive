---
title: "emacs file saving very slow"
date: 2011-11-10
forum: Programming Talk
---

### Post by stuque on 2011-11-10
Sometimes, after using Emacs for a while, saving becomes extremely slow, e.g. 30 seconds to save a file that was saved instantly a few moments ago.

Logging out and back in usually solves the problem for a while, but it always seems to come back.

I can see no other processes that are swamping the CPU, or other obvious problems (e.g. closing all other applications doesn't seem to help).

Suggestions about how I can go about debugging this problem would be appreciated.

Thanks.

---

### Post by 11jmb on 2011-11-10
Does that include processes that may be using lots of memory?

---

### Post by stuque on 2011-11-10
Yes, I've checked memory and CPU usage via top while emacs is running slowly, and there is no obvious culprit.

---

### Post by NovaAesa on 2011-11-10
I know this is an obvious question, but is the file being saved locally or on a network?

---

### Post by stuque on 2011-11-11
Its local storage.

---

### Post by nvteighen on 2011-11-11
0. Why has this been posted here? I think this should be moved to General Help, even though the "offending" application is a programming-related one.

1. Which OS are you using? No, this is not an obvious question: some people on these forums don't use Ubuntu. Even if it's Ubuntu, what version do you use? Have you checked for related bug reports?

2. Is it just emacs or other programs are also showing some lag? We should first prove that it is just emacs and something else what's having problems.

---

### Post by stuque on 2011-11-11
I assume that mostly programmers use emacs, so it is more likely that programmers would either have experienced the problems I am having, or have ideas about how to go about debugging it.

I'm using Ubuntu 10.04 with XFCE (upgrading to a newer version is not an option for me right now).

No other programs seem to show any related problems: it's just emacs.

---

### Post by cgroza on 2011-11-12
Did you do any modifications to your .emacs file before this problem appeared?

---

### Post by Arndt on 2011-11-12
Some random thoughts to understand the problem better:

When it takes 30 seconds to save a file, is it the case that the runtime for the Emacs process increases with 30 seconds?

If you run without .emacs, does the same phenomenon occur?

You may prepare a debugger and attach to the Emacs process, and then interrupt it when a saving takes really long, but I don't know if that will show anything at all.

You could start Emacs with strace, and look at the system calls done during such a long save.

---

### Post by HappyCrow on 2013-01-15
Put this in your ~/.emacs:

;; fix for slow emacs when saving files
(setq vc-handled-backends nil)

That worked for me.

---

