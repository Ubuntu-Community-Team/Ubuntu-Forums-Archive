---
title: "Problem Configuring Apps"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by newby1980 on 2008-05-28
Whenever i try to configure an app (don't matter which one) I get the following message 

hpadmin@hpadmin-desktop:~/xawtv-3.95$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
hpadmin@hpadmin-desktop:~/xawtv-3.95$

---

### Post by Maestro23 on 2008-05-28
Compiling Software: [https://help.ubuntu.com/community/CompilingSoftware?highlight=(compiling](https://help.ubuntu.com/community/CompilingSoftware?highlight=(compiling))

*Not recommended for people new to Linux.  Just FYI.

---

### Post by HotShotDJ on 2008-05-28
> **newby1980 said:**
> Whenever i try to configure an app (don't matter which one) I get the following message 

hpadmin@hpadmin-desktop:~/xawtv-3.95$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
hpadmin@hpadmin-desktop:~/xawtv-3.95$Have you installed the necessary packages required for compiling applications?  Is there a reason that you are compiling applications rather than using System --> Administration --> Synaptic Package Manager?  (xawtv version 3.95 is in the repository, you don't need to compile it from source).

---

### Post by iaculallad on 2008-05-28
To get development tools run the command below on your terminal

Code:

```
sudo apt-get install build-essential
```

---

### Post by newby1980 on 2008-05-28
> **iaculallad said:**
> To get development tools run the command below on your terminal

Code:

```
sudo apt-get install build-essential
```

Thank You

---

### Post by iaculallad on 2008-05-28
> **newby1980 said:**
> Thank You

You're welcome. Go Ubuntu

---

