---
title: "speedtest-cli Install - Unable to locate package (Windows 10)"
date: 2019-03-12
forum: New to Ubuntu
---

### Post by kimbertle on 2019-03-12
I'm running the Ubuntu (v18.04 "bionic") under Windows 10 (1809). Attempting to install the command line version of speedtest-cli fails.

Entering the command "speedtest-cli" reports speedtest is available using:
```
sudo apt install speedtest-cli
```

Entering the command "sudo apt install speedtest-cli" (and supplying the su password) results in:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package speedtest-cli

```


I searched the packages at packages.ubuntu.com, and the package supposedly exists.

Anyone have any ideas on how to fix this?

---

### Post by deadflowr on 2019-03-12
Make sure Ubuntu's community (universe) repository is enabled.
```
sudo add-apt-repository universe
sudo apt update
sudo apt install speedtest-cli
```

> I'm running the Ubuntu (v18.04 "bionic") under Windows 10 (1809)
My assumptions are this is WSL? (Windows subsystem for Linux)
or is this a virtual machine setup?

---

### Post by kimbertle on 2019-03-12
**Thank you** for your suggestions!

Again, "Ubuntu (v18.04 "bionic") under Windows 10 (1809)" so yes: WSL.

(Brief) Response Summary to your suggestions: 

* **add-apt-repository universe**: 'universe' distribution component is already enabled for all sources.
* **sudo apt update**: 167 packages can be upgraded.
* **install spreedtest-cli**: Unable to locate package spreedtest-cli

---

### Post by deadflowr on 2019-03-12
Sorry, I misspelled it.
It should be speedtest-cli
I spelled it spreedtest.](*,)

Fixed in post


Edit: You should install all updates.

---

### Post by kimbertle on 2019-03-12
DOH! And of course, I didn't actually double-check your spelling, now did I? <G>

Drum roll please... HOUSTON! We HAVE SPEED TEST!! [insert applause, here]

I have added the entry "*deadflowr*" to my *"Complete List of Known Gods and Other Awesome Entities*" compendium!

**THANK YOU!**

---

