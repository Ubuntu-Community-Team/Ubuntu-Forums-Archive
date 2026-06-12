---
title: "Can't install VLC through software center"
date: 2021-03-02
forum: New to Ubuntu
---

### Post by rosyjag on 2021-03-02
Installed LTS20,04. Wanted to install VLC. Clicked on Ubuntu software  center and searched for VLC. It spins and hangs. The network connection  is OK. Please guide me.

---

### Post by wildmanne39 on 2021-03-02
Thread moved to the New to Ubuntu sub-forum.

---

### Post by CelticWarrior on 2021-03-03
Make sure the system is fully updated before installing additional software:
```
sudo apt update
sudo apt full-upgrade
```

Ubuntu Software should work fine after that and, of course, you can always install VLC with a command: ```
sudo apt install vlc
```

---

### Post by ActionParsnip on 2021-03-03
> **CelticWarrior said:**
> Make sure the system is fully updated before installing additional software:
```
sudo apt update
sudo apt full-upgrade
```

Ubuntu Software should work fine after that and, of course, you can always install VLC with a command: ```
sudo apt install vlc
```
Beat me to it. The CLI is usually better and gives useful output as to WHY it didn't install whereas the GUI offering may as well just give a picture of Elmo shrugging

---

