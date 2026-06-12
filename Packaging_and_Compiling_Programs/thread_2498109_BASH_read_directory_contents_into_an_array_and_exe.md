---
title: "BASH read directory contents into an array and execute command"
date: 2024-05-30
forum: Packaging and Compiling Programs
---

### Post by rolfbruge on 2024-05-30
I ran this simple bash script through shellcheck.net and no errors but does not function.  

The objective is to read downloaded *.deb packages stored within the directory into an array and install each element of the array with dpkg:

running the ls line lists the pacakages, but output is "no such file or directory" or "permission denied" even though cli is executed using sudo.


```
#!/bin/bash

FILES=$( ls "/home/linuxuser/pkgs" )
 
for element in "${FILES[@]}"
  do
      sudo dpkg -i "$element" 
  done
```

Being relatively new to this issue can someone give me specific pointers?

---

### Post by currentshaft on 2024-05-30
Don't use ls to populate variable names, use find.

for element in $(find /home/linuxuser/pkgs -type f -name "*.deb") ; do sudo dpkg -i "$element" ; done

---

### Post by rolfbruge on 2024-06-02
Thank you currentshaft for the pointer, it worked nicely.

---

