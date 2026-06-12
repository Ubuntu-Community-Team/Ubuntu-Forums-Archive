---
title: "Download &amp; Install Cinelerra in V12.04"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by methomas on 2012-05-21
Greetings,

I am new to Linux & Ubuntu. 
I tried to make a go of it last  Nov. and gave up.

I tried again today, installed V12.04 without any trouble.

But, I have spent the last 2 hours trying to install Cinelerra and have failed.

Bear with me as I have been a senior citizen for a long time.

Please give me a list (1, 2, 3, etc.) of how to install Cinelerra. 

I am a beginner and know nothing about Linux or Ubuntu, so I need instructions in Plain English.

Thanks,

M E

---

### Post by cariboo on 2012-05-22
The easiest way to install Cinelerra is via the ppa located here:

[https://launchpad.net/~cinelerra-ppa/+archive/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ppa)

To add the ppa, open a terminal and  copy & paste the following command:

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
```

Once the ppa has been added, type the following command:

```
sudo apt-get update
```

After the update has finished, you should be able to search for Cinelerra in the Software Centre and install it from there..

---

