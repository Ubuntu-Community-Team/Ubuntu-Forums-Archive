---
title: "Openoffice corrupt in hardy?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by LearningPerson on 2008-09-09
Hello, I have used Hardy Heron for awhile now but this AM while logging in an error appeared (Notification....).  I deleted, then the system checked itself and after fsck died with exit status 4, I had to do fsck manually in root.  I just said yes to everything and now in OpenOffice Writer, all bold words and many documents are gone.  

Tried reinstalling from Synaptic Mgr but I do think OpenOffice is corrupted.  

Is there a way I can just reinstall the office suite?

Please help.  Thanks,

Sharon

---

### Post by wolfen69 on 2008-09-09
after completely removing openoffice in synaptic, you need to do ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
```then reinstall. it worked for me.

---

### Post by LearningPerson on 2008-09-09
> **wolfen69 said:**
> after completely removing openoffice in synaptic, you need to do ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
```then reinstall. it worked for me.

Hi Wolfen,

The problem is where do I get a new install of OpenOffice.org or Writer for Hardy Heron?  I can't find a "new" installation.

Would it appear on Synaptic?

Thanks,
Sharon

---

### Post by LearningPerson on 2008-09-09
This has been resolved.

---

