---
title: "[SOLVED] how to remove old user home folder"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-21
hi
I have removed a user under admin ==> user and groups but their home folder is still there

I have tried:
sudo rm /home/<user name>
but got the following error message
rm: cannot remove `/home/<user name>': Is a directory

so then I tried:
sudo rmdir /home/<user name>
which gave me
rmdir: failed to remove `/home/<user name>': Directory not empty

what command do I need to force removal of this directory?

---

### Post by iaculallad on 2008-08-21
> **LTFC2020 said:**
> hi
I have removed a user under admin ==> user and groups but their home folder is still there

I have tried:
sudo rm /home/<user name>
but got the following error message
rm: cannot remove `/home/<user name>': Is a directory

so then I tried:
sudo rmdir /home/<user name>
which gave me
rmdir: failed to remove `/home/<user name>': Directory not empty

what command do I need to force removal of this directory?

That would be:

```
sudo rm -rf /home/<user name>
```

---

### Post by mcduck on 2008-08-21
I'd actually recommend "rm -r" instead of "rm -rf". You shouldn't *force* things just out of habit..

---

### Post by Joeb454 on 2008-08-21
I think missing the -f flag wouldn't do much in this case

---

### Post by LTFC2020 on 2008-08-21
thanks
in the end I did sudo nautilus and deleted from that

---

