---
title: "Downloading updates error"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Sbaloga96 on 2008-06-04
I am extremely new to this.  I had an old laptop that I was sick of re-imaging with windows so I threw Unbuntu on it, now I am getting an error message when I try to download and install updates:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so I opened terminal and tried to do it manually only I got this error:

dpkg: requested operation requires superuser privilege

So I tried to upgrade to the superuser version of terminal through the add/remove applications but I keep getting the 1st error listed above. I feel like I'm in an infinite loop.

Any suggesstions would be greatly appreciated.

Thanks,

-Steve
:confused:

---

### Post by django0909 on 2008-06-04
You should run it like this in the terminal:

```
sudo dpkg --configure -a
```

and enter your password when it asks for it.

---

### Post by Sbaloga96 on 2008-06-04
Worked perfectly...Thanks!

---

### Post by django0909 on 2008-06-04
No problem :)

---

