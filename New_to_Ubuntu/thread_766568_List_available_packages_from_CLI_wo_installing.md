---
title: "List available packages from CLI w/o installing"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by jimbojones on 2008-04-25
Can anyone point me in the right direction on listing available packages through the cli w/o actually installign them.

I came up with  dpkg --get-selections pattern  to list all of my installed packages and would like to find something similar for available but uninstalled packages and have been unable to do so.  Thanks

---

### Post by spiderbatdad on 2008-04-25
There are more than 24,800 packages available in synaptic package manager. Do you really want that printed out in CLI?

---

### Post by PmDematagoda on 2008-04-25
I believe you should be able to use Aptitude in place of Synpatic for CLI package management.

---

### Post by pedro_orange on 2008-04-25
> **PmDematagoda said:**
> I believe you should be able to use Aptitude in place of Synpatic for CLI package management.

```
apt-cache search package-name
```

Is one way of doing it

---

### Post by jimbojones on 2008-04-25
> There are more than 24,800 packages available in synaptic package manager. Do you really want that printed out in CLI? 
No not all of them, I plan on using a pattern for particular packages



> **pedro_orange said:**
> ```
apt-cache search package-name
```

Is one way of doing it

Exactly what I was looking for, thank you very much.

---

