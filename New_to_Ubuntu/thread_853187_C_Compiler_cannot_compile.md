---
title: "C Compiler cannot compile?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by dnil82 on 2008-07-08
Everytime i've executed ./configure on terminal to install packages, i always get this error message. What does it mean?:confused:

---

### Post by Sef on 2008-07-08
Have you installed build-essential?  If not, then copy paste this code:

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by dnil82 on 2008-07-08
Can i do it offline??

---

### Post by ChameleonDave on 2008-07-08
> **dnil82 said:**
> Can i do it offline??

No!  You need to download and install some essential software for compiling.

---

### Post by dnil82 on 2008-07-08
sorry, i mean can i just downloaded the packages, and do the installation manually? ([http://packages.ubuntu.com/dapper/i386/build-essential/download](http://packages.ubuntu.com/dapper/i386/build-essential/download)),  I know the secured way is to get online, but i don't have internet connection in home. :)

---

### Post by fluteflute on 2008-07-08
You could but it would be alot of effort as you would also have to download all the dependenices ([http://packages.ubuntu.com/dapper/i386/build-essential](http://packages.ubuntu.com/dapper/i386/build-essential)) and then those packages dependencies and so on.

---

### Post by zvacet on 2008-07-08
@ **dnil82**

Yes,you can do it.If you don´t have internet at home you can use [nonetdebs.]("http://ubuntuforums.org/showthread.php?t=572819")

---

### Post by WW on 2008-07-08
Do you have your installation CD?  I'm pretty sure the C compiler and libraries  are on the CD.

---

### Post by dnil82 on 2008-07-08
Wew, sound it would be complicated if i do it manually, so the best way is online. Thanks all for the responses.

---

### Post by dnil82 on 2008-07-08
> **WW said:**
> Do you have your installation CD?  I'm pretty sure the C compiler and libraries  are on the CD.

Yes, I have the CD, then what should I do?

---

### Post by dnil82 on 2008-07-08
> **zvacet said:**
> @ **dnil82**

Yes,you can do it.If you don´t have internet at home you can use [nonetdebs.]("http://ubuntuforums.org/showthread.php?t=572819")

Now that's worth a try.. Thanks :)

---

### Post by WW on 2008-07-08
Take a look [here](https://help.ubuntu.com/8.04/add-applications/C/offline.html).

---

