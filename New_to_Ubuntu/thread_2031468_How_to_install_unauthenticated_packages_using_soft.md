---
title: "How to install unauthenticated packages using software-center"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by mr.akik on 2012-07-22
Hi,
I'm using ubuntu 12.04. I have created a local repository. When I install any package from terminal, I have to use this command:
```
sudo apt-get --allow-unauthenticated install packagename
```
To install unauthenticated packages , I start synaptic using this command:
```
gksudo "synaptic -o APT::Get::AllowUnauthenticated=true"
```

Is there any command that will help me to start software-center the way I start synaptic?
Thanks in advance.

---

### Post by cwsnyder on 2012-07-22
Software Center would not list packages from your local repository, even if you could get it to 'Allow Unauthenticated.' The listings are not local to your installation.

---

