---
title: "[SOLVED] could not download all repository indexes"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by jim_in_dorris on 2008-06-06
ok, when i run update manager, i get "Could not download all repository indexes" as as error message.  I tryed the "apt-cdrom add" fix  with the install cd per the error message but that didn't do any good.  what am I supposed to do now, I get a repository out of date message telling me to run update manager but then I get that error?

---

### Post by iaculallad on 2008-06-06
Navigate to System->Administration->Software Sources, Under the "Ubuntu Software" tab, check if Main, Universe, Restricted, Multiverse enabled (checked). Uncheck the "Installable from CD-ROM/DVD" option. Click on close.

Goto your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Duck2006 on 2008-06-06
Are you doing your updates from a CD or net?

---

### Post by cariboo on 2008-06-06
Another thing to try, is open synaptic then click Settings-->Repositories, then click the download from dropdown, click other, then click the select server button choose the server it comes up with and you should be good to go.

Jim

---

