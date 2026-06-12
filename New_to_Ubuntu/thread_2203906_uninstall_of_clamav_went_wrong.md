---
title: "uninstall of clamav went wrong"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by Mark_Enna on 2014-02-05
UBUNTU 13.10
i could not get clamtk to update so I uninstalled clamav using package manager.
When I try to update my system or install new packages I get this error message

installArchives() failed:Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg: unrecoverable fatal error,aborting: 
 syntax error: unknown user 'clamav' instatoverride file

---

### Post by Gone fishing on 2014-02-06
I think if you edit the /var/lib/dpkg/statoverride file and remove reference to clamav 

```
sudo nano /var/lib/dpkg/statoverride
``` or use gedit if you prefer. However to get clamav to update open a terminal and run ```
sudo freshclam
```

---

### Post by Mark_Enna on 2014-02-06
This worked like a charm, thank you

---

### Post by Gone fishing on 2014-02-06
Thanks could you mark as solved?

---

