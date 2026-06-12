---
title: "[SOLVED] manually run dpkg --configure -a ?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-12
Hello, 
 I just did a reinstall and I am currently trying to get everything set back up by using reassuringlyoffensives' guide here...[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).
  
 The problem is when I try to get updates, or open synaptic package manager, I get this error.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

How do you run it manually?

---

### Post by aysiu on 2008-06-12
Close Synaptic and then paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo dpkg --configure -a
```

---

### Post by MmmmJoel on 2008-06-12
You are reading the message in a different way. It merely means you must run 'dpkg --configure -a' in a Terminal.

---

### Post by Dutch70 on 2008-06-12
Thanks a bunch!

 I had done that, but it didn't look like it done anything, guess it did cause I went into synaptic and enabled java after trying it again. 

Just to make sure, this is what you use to get updates....

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Right?

---

### Post by aysiu on 2008-06-12
You can leave out the middle bit. ```
sudo apt-get update && sudo apt-get dist-upgrade
``` Read more [here](http://ubuntuforums.org/showpost.php?p=4552683&postcount=3).

---

### Post by Dutch70 on 2008-06-12
Oh, nevermind, I'm being too cautious after a reinstall!!!

Thanks again!:)

---

### Post by Dutch70 on 2008-06-12
Ok, great, thanks for the info. I'll go check it out!

---

