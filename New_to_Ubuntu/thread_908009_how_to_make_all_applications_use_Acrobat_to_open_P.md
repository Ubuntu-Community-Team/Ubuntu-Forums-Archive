---
title: "how to make all applications use Acrobat to open PDF files?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by legolas_w on 2008-09-02
Hi
Thank you for reading my post.
I installed acrobat reader and I tried to assign pdf extension to acrobat reader by the following procedure:

-right click on a PDF file
-select properties
-select open with tab
-choose acrobat reader instead of Document viewer

however, this works fine when I double click on a pdf file but when for example I download a file FireFox it does not open it using acrobat and instead it tries to open it using Document viewer. Also If i double click on a PDF file which is attached to an email, it tries to open the file using Document viewer and not Acrobat.

The bad thing is that there is no sign of acrobat reader in "open with" section of Firefox download window or Thunderbird open attachment window.
Is there any solution for it?

Thanks

---

### Post by OrangeCrate on 2008-09-02
Go to Synaptic, search for, and install "mozilla-acroread" which is the Firefox plugin for the Adobe Reader.

---

### Post by cpetercarter on 2008-09-02
In Firefox, Edit > Preferences > Applications

Find the line which says "PDF Document" and highlight it. In the dropdown menu, you may find Adobe Reader already shown, or you may have to click "other application" and find Adobe Reader in your file system.

---

