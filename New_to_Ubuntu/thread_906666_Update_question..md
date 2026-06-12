---
title: "Update question."
date: 2008-08-31
forum: New to Ubuntu
---

### Post by BertOlton on 2008-08-31
As an absolute beginner not only to Ubuntu, but with Linux, I have a question.  This past week some software updates became available.  One was "Linux-image-2.6.24-19-generic".  The last paragraph of the description for that one reads,

 "You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

Evidently I shouldn't allow this download from the update utility. How do I go about finding the meta package to download?

Thank you for your time and patience,

Bert

---

### Post by Oldsoldier2003 on 2008-08-31
That "warning" applies if you are installing the package manually. It's just there to let the curious fiddlers know that they probably don't need to install the package manually (using synaptic, for example). The fiddlers with more experience need not worry since they generally understand what they are doing :)


 Let the updater do its job and all will be fine, unless of course you have a reason that you don't want that particualr kernel update.

---

### Post by BertOlton on 2008-08-31
> **Oldsoldier2003 said:**
> That "warning" applies if you are installing the package manually. It's just there to let the curious fiddlers know that they probably don't need to install the package manually (using synaptic, for example). The fiddlers with more experience need not worry since they generally understand what they are doing :)


 Let the updater do its job and all will be fine, unless of course you have a reason that you don't want that particualr kernel update.

Ah, makes sense.  Thank you, sir!

Best regards,
Bert

---

### Post by lbriner on 2008-08-31
A little more info for your info. The idea of a meta-package is to allow the automatic selection of a specific set of other libraries/executables depending on a number of factors, for instance what the latest specific kernel is. By installing the meta-package rather than a specific kernel, when a new one comes available, the updater will select it and offer it for upgrade, if you had manually selected a kernel and did NOT have the meta package installed, you would stick with that version. As you learn more about Linux and want to start installing more programs, you will see lots of meta-packages available, most of which will say that they will provide you with the latest version of something as they become available.

---

