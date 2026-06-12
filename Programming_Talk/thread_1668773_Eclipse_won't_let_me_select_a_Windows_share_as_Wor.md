---
title: "Eclipse won't let me select a Windows share as Workspace"
date: 2011-01-16
forum: Programming Talk
---

### Post by android-eve on 2011-01-16
Environment: Ubuntu 10.04 (64-bit), Eclipse Helios 3.6 (64-bit), Android 2.3 SDK + ADT.

All works great, but I can only select a workspace that's on the **local** system. Eclipse won't let me select shared folder on a Samba server.

Ubuntu's URI for this share is of the form:

    ```
    smb://userid@192.168.0.2/sandbox/workspace 

```Even when I type this manually into the edit box, Eclipse won't accept it.

Other applications (e.g. gedit) don't exhibit this restriction.

Is there a workaround to solve this, **without installing the smbfs package** and **without permanently mounting the share**?

---

