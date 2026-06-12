---
title: "Problem with Add/Romove"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by TrH89 on 2008-11-11
This is the first time I have ever used an OS other then windows, and I have seem to run in to a problem. When I tried to add firestarter it froze up and then when I tried to run the program I get the error thats shown in the attachment. I cant remove the program as well because of a different error which is the second attachment. 

On a side note how do you put images on the thread?

---

### Post by kostkon on 2008-11-11
> **TrH89 said:**
> This is the first time I have ever used an OS other then windows, and I have seem to run in to a problem. When I tried to add firestarter it froze up and then when I tried to run the program I get the error thats shown in the attachment. I cant remove the program as well because of a different error which is the second attachment. 

On a side note how do you put images on the thread?
Open a terminal (*Applications -> Accessories -> Terminal*) and give the following
```
sudo dpkg --configure -a
```
it will ask you for a password, give yours.

Afterwards, try to run *Add/Remove* again, it should be working now.

---

### Post by TrH89 on 2008-11-11
Thanks that was simple thanks for the help.

---

