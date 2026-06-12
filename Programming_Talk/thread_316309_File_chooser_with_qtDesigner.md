---
title: "File chooser with qtDesigner"
date: 2006-12-10
forum: Programming Talk
---

### Post by diego_sza on 2006-12-10
Hello! How can I have a "FileChooser" qt widget? I'm trying to create an application and I want to click on a button and browse the filesystem in order to choose one file.
Thanks.

---

### Post by nuku_da2 on 2008-08-31
> **diego_sza said:**
> Hello! How can I have a "FileChooser" qt widget? I'm trying to create an application and I want to click on a button and browse the filesystem in order to choose one file.
Thanks.

Hello, have you solved your question? I'm developing my final project of my degree and I'm very interesting in doing the same you want (to click on a button and browse the filesystem in order to choose one file). So, if you want how to create it, please send me an email (nuku_da2@hotmail.com), I'll do the same for you ;)

Thanks, greetings.

---

### Post by scourge on 2008-08-31
That's not something that should be done with Qt Designer. You can use QFileDialog::getOpenFileName to get what you need: [http://doc.trolltech.com/4.4/qfiledialog.html#getOpenFileName](http://doc.trolltech.com/4.4/qfiledialog.html#getOpenFileName)

I assume that you know enough about signals and slots to summon the dialog via a button.

EDIT: Just noticed the age of this thread, wow. Surprising that such a simple question went unanswered.

---

