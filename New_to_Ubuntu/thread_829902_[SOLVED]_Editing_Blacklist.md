---
title: "[SOLVED] Editing Blacklist"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by deaddudehangin on 2008-06-15
Well I accidentaly put a driver into the blacklist document that I wasn't suppose to and it caused my wireless card to not work at all. So when I try to edit out the line in the blacklist document it gives an error saying
"Unable to write to disk" or something like that.
How would I fix this issue?

---

### Post by Vadi on 2008-06-15
Try starting the editor with "gksudo" in front, does that help?

---

### Post by drs305 on 2008-06-15
> **deaddudehangin said:**
> Well I accidentaly put a driver into the blacklist document that I wasn't suppose to and it caused my wireless card to not work at all. So when I try to edit out the line in the blacklist document it gives an error saying
"Unable to write to disk" or something like that.
How would I fix this issue?


If it was made to /etc/modprobe.d/blacklist or another system file, you can edit it by opening the file with administrative powers (substitute your text editor for "gedit"):
```
gksudo gedit /path/filename
```

---

### Post by Joeb454 on 2008-06-15
From a terminal run ```
gksudo mouse /path/to/blacklist/file
```

I believe "mouse" is the default text editor in Xubuntu :) And obviously you need to change the path to the correct one :)

---

### Post by deaddudehangin on 2008-06-15
thanks, it worked\\:D/
thank you all for such quick responses

---

### Post by Joeb454 on 2008-06-15
No problem :) You can mark your thread solved from "Thread Tools" at the top of this page too :)

---

