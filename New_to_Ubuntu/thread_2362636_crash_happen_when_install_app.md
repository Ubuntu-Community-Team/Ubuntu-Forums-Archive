---
title: "crash happen when install app"
date: 2017-05-31
forum: New to Ubuntu
---

### Post by ahmed43 on 2017-05-31
when I download app from net with (deb) extension & install it via ubuntu software, it hang & installing icon appear without action, so I restart the PC to solve it everytime.

---

### Post by howefield on 2017-05-31
What is the file/application that you are trying to install ?

---

### Post by oldos2er on 2017-05-31
Ubuntu version? Why aren't you installing from the repositories?

---

### Post by sp40140 on 2017-05-31
> **ahmed43 said:**
> when I download app from net with (deb) extension & install it via ubuntu software, it hang & installing icon appear without action, so I restart the PC to solve it everytime.
Ubuntu "software" application doesn't like third party deb files.
If you download deb files from internet, you should use following command from command line to install :
```

sudo apt install <filename>.deb
sudo dpkg -i <filename>.deb

```

---

### Post by cariboo on 2017-06-02
To make sure all dependencies are installed, I'd suggest gdebi, it's available in the repositories.

---

