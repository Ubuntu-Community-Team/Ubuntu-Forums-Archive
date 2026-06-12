---
title: "Problem running Floola from an iPod."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Dapilot1 on 2008-04-28
So if you have Floola on your iPod you cant run it because you need to change it to run as an executable. But you can't and even after going through nautilus as root you cant seem to change it to an executable. Is there a way to get this working? I think it has something to do with the whole policy kit because it works fine on 7.10.

---

### Post by joshrobinson on 2008-04-28
> **Dapilot1 said:**
> So if you have Floola on your iPod you cant run it because you need to change it to run as an executable. But you can't and even after going through nautilus as root you cant seem to change it to an executable. Is there a way to get this working? I think it has something to do with the whole policy kit because it works fine on 7.10.

have you tried to use ```
chmod +x filename
``` from a terminal?
if that doesnt work try throwing a sudo on it
```
sudo chmod +x filename
``` make sure you are in the directory of the file, and replace "filename" with the name of the floola executable file

---

