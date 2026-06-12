---
title: "can't install extensions on gnome shell 11.10"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by mikhaell on 2011-10-01
Hi, i'm using 11.10 beta and love gnome shell. I would really love to install some extensions but can't- the tweak tool doesn't install extensions (it gives the option, tells me to restart, but nothing), and when I transfer the extension files in to the .local/share folder nothing happens either. Any thoughts?

---

### Post by mikhaell on 2011-10-01
?

---

### Post by mErchamion on 2011-10-02
Seems that there is an issue with metadata.json files. There is a field for gnome version in those files, and you have to be sure that this field equals the output of gnome-shell --version command. I have edited the files and got gnome-tweak-tool to show the extensions. However, it seems that this file-editing brakes the extension and it is not possible to run extensions. Any ideas?

---

### Post by mikhaell on 2011-10-04
The same thing happens to me.

---

### Post by mErchamion on 2011-10-04
I havent seen any bug report in launchpad. Is it correct to file one? Have any of you seen a bug report about this?

---

