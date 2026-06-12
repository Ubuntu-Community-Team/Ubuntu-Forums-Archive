---
title: "[SOLVED] Mesquite requests &amp;quot;please select a web browser&amp;quot;"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by roems on 2008-11-10
I am learning to use a evolutionary software called Mesquite and its running on Ubuntu 8.04. I installed it  and the software works fine in ubuntu. The problem is that when I request a help page or there is an hyperlink to a web address, it doesn't identify firefox automatically as my web browser.

The following message appears:

"Please select a web browser" and a file manager window in order I think to find the executable of the software. Could anybody please tell me the location of the binary file?

Thanks

Roberto

---

### Post by ohzopants on 2008-11-10
In the terminal type:
```
which firefox
```

That will give you the full path of the firefox executable and then just browse to that location in Mesquite.  (I'm pretty sure firefox is located in /usr/bin, but "which" will tell you for sure)

---

### Post by MasterSander on 2008-11-10
If you can edit the preferences in mesquite, look up what browser will be launched if it states mozilla $url, change it to firefox $url

---

### Post by roems on 2008-11-11
Thanks a lot! Now I can browse the help pages.

---

