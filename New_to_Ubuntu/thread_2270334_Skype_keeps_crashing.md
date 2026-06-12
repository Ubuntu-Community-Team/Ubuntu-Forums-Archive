---
title: "Skype keeps crashing?"
date: 2015-03-22
forum: New to Ubuntu
---

### Post by whitefox3 on 2015-03-22
Hello eveyone. I have just started to use Ubuntu Mate 14.04.1-final-desktop-amd64 and i'm still trying to find my way around lol. I tried to install Skype but it keeps on crashing and thats when i am still trying to configure it. Does anyone know how i might install Skype without it crashing? 

Plus anything to do with configuring Ubuntu Mate would also be appreciated. Thanks

---

### Post by fantab on 2015-03-22
How and from where did you install Skype? Did you use official Ubuntu software repositories?

---

### Post by whitefox3 on 2015-03-22
Hello fantab
The first time i tried i downloaded and installed Ubuntu-12.04 (multiarch) and that kept on crashing. So i went back to [www.skype.com](www.skype.com) and downloaded + installed
 Ubuntu-10.04-32bit and its working fine now.

Big thanks for the reply.

---

### Post by Vladlenin5000 on 2015-03-22
Next time you need to install Skype just make sure you enable the Partners repository and then:
```
sudo apt-get update
sudo apt-get install skype
```

---

### Post by fantab on 2015-03-24
Partners repository can be enabled from Software Center -> Edit -> Sources, then enable Partners repository. Thats it... allow software center to reload and then search and install Skype.
When you use Ubuntu repositories to install any software all the necessary dependecies and libraries will be also installed, which we miss when installing any other source.

---

