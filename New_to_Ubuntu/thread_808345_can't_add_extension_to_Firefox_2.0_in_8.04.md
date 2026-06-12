---
title: "can't add extension to Firefox 2.0 in 8.04"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by johanus on 2008-05-26
Really missed some FF extensions so I removed 3.0 Beta5 and installed 2.0. Ran into a problem when I tried to install the Foxmarks extension; this is what I see in the error log:

> Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

Is this an Ubuntu problem or a Firefox problem, I wonder?

Thanks for any help!

---

### Post by Inxsible on 2008-05-26
When you removed Firefox 3, did you purge it ?

You need to remove all the user properties and then install FF2. That should fix it.

---

### Post by johanus on 2008-05-26
No, I didn't purge it, just "removed" it.  Thanks for the tip!

---

### Post by philinux on 2008-05-26
> **johanus said:**
> No, I didn't purge it, just "removed" it.  Thanks for the tip!

Backup your bookmarks too.

---

### Post by pranayama on 2008-05-26
This worked for me:

[http://ubuntuforums.org/showthread.php?t=806220](http://ubuntuforums.org/showthread.php?t=806220)

---

### Post by johanus on 2008-05-26
Pranayama, it was the hidden .mozilla file that was the key deletion.  Thanks very much to all!  :)  Now my extensions install fine.

---

