---
title: "Openoffice wont start."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-06-02
When i start openoffice i get this message.

Missing vcl source.This means that files vital to localisation are missing.You may have a corrupt installation.

On pressing OK i get this message.
The Program could not be started.iso resource sould not be loaded bu the Sfx application.

I then tried to remove open office using Add/Remove but then i was supposed  to remove some dependant application like openoffice.org-writer.

Removed that and i get the same problem.

---

### Post by ad_267 on 2008-06-02
Try going to System - Administration - Synaptic Package Manager, search for packages installed with openoffice in their name and reinstall these by right clicking on them and selecting mark for reinstallation then hit apply.

---

### Post by Xiong Chiamiov on 2008-06-02
> **ad_267 said:**
> Try going to System - Administration - Synaptic Package Manager, search for packages installed with openoffice in their name and reinstall these by right clicking on them and selecting mark for reinstallation then hit apply.
or
```

sudo aptitude reinstall ~nopenoffice

```
which will reinstall all packages with openoffice in their name.

---

