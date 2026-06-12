---
title: "Emacs C++ code completion"
date: 2007-05-23
forum: Programming Talk
---

### Post by Redscare on 2007-05-23
Hey all, I have done research on this, and used google and everything, and can't find a definitive solution: effective C++ code completion for free. Xrefactory seems to do a good job but it costs $300:). The requirements are that the code completion can parse included header files and the file that is being worked on. Thanks in advance.

---

### Post by WW on 2007-05-23
Does the thread title "Emacs C++ code completion" imply that you are looking specifically for an emacs extension that implements code completion, and you are not interested in any other editor or IDE?

---

### Post by Redscare on 2007-05-23
Yes, as I have already sampled many IDE's. My current IDE is Eclipse with CDT, which is great, but emacs is better at certain things. Kdevelop's code completion unfortunatly doesn't parse headers if I understand correctly, and the databases don't work for the standard library.

---

### Post by kknd on 2007-05-25
Look at the project "icomplete" (sourceforge). It has a plugin for Vim, but is easy to convert it to Emacs.

By the way: Vim rocks.

---

### Post by Redscare on 2007-06-05
Thanks for the info. How would I convert it to Emacs?

---

### Post by wobster on 2007-06-06
Key-combintion M-/ is not exactly a smart auto-completion, but it serves its purpose. It simply iterates through known names. 
There's also the speedbar add-on which offers symbol/name overviews, etc. 
Maybe also worth a look is SLIME for emacs.

---

### Post by rickardg on 2007-06-06
Perhaps [CEDET]("http://cedet.sourceforge.net/") would work for you, in particular [Semantics 'IntelliSense' support]("http://cedet.sourceforge.net/intellisense.shtml").

It was a bit flaky when I used it for java, but that was years ago and C++ seems to be better supported. Anyway, it can't hurt to check it out.

---

### Post by Redscare on 2007-06-06
Thank you for the replies, but it appears that none of these complete standard library functions. Is that possible in emacs without Xrefactory?

---

### Post by rickardg on 2007-06-07
I haven't used CEDET for quite some time now, so I'm probably barking up the wrong tree here, but have you added the header files for the standard library to the list of files that Semantic parses?

You'll probably get better answers by asking in the [help-gnu-emacs mailing list]("http://lists.gnu.org/mailman/listinfo/help-gnu-emacs") or specific semantic questions in the [semantic mailing list]("https://lists.sourceforge.net/lists/listinfo/cedet-semantic").

BTW there seems to have been a new (pre)release of cedet a couple of days ago.

---

