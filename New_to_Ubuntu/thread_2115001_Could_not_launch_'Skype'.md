---
title: "Could not launch 'Skype'"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by mlnease on 2013-02-11
Hello,

I've just finished a clean install of Lucid, which went fine except that I can't get Skype to work.  I installed it from Synaptic but when I try to start it, I receive the error message:

Could not launch 'Skype'
Failed to execute child process "skype" (No such file or directory)

Any suggestions?  

Thanks in advance.

---

### Post by sanderj on 2013-02-11
Did you Google "Failed to execute child process "skype" (No such file or directory)"?

Is your Ubuntu 64-bit?

---

### Post by mlnease on 2013-02-11
> **sanderj said:**
> Did you Google "Failed to execute child process "skype" (No such file or directory)"?
Yes, I did and
> Is your Ubuntu 64-bit?Yes, it is.

I also tried 

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```and
```
sudo apt-get update && sudo apt-get install skype
```after completely removing Skype in Synaptic--same result.

---

### Post by sanderj on 2013-02-11
So what did the first hits of the Google search suggest?

I would say:


```
sudo apt-get install ia32-libs 

```
Then try to start Skype again.

If you do NOT get the error, continue

```
sudo apt-get install ia32-libs lib32asound2 libasound2-plugins

```

---

### Post by sanderj on 2013-02-12
No news is good news?

---

### Post by mlnease on 2013-02-12
> **sanderj said:**
> No news is good news?
Sorry, didn't receive your second response, probably because I was re-reinstalling, which solved the problem.  Thanks for your time.

---

### Post by sanderj on 2013-02-12
> **mlnease said:**
> Sorry, didn't receive your second response, probably because I was re-reinstalling, which solved the problem.  Thanks for your time.


re-installing Skype, or your whole Ubuntu?

---

### Post by mlnease on 2013-02-12
> **sanderj said:**
> re-installing Skype, or your whole Ubuntu?
Ubuntu.

Thanks again.

---

