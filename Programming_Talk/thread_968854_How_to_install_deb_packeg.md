---
title: "How to install deb packeg"
date: 2008-11-03
forum: Programming Talk
---

### Post by Jayadheer on 2008-11-03
Hello all,
  
  I am beginner to Ubuntu. I have just downloaded code:blocks IDE (C++ ) compiler it is in .deb package I have extraccted them. Now how install this IDE. can any one please help 



Thanks in advance!!

---

### Post by Circus-Killer on 2008-11-03
firstly, in case this package has unmet dependencies, you will need to have a working internet connection to do the install.

all you to do is go to your terminal and use:
```
sudo dpkg -i filename.deb
```

it will either tell you that it installed successfully, or display a bunch of errors. if it does display errors, then type in the terminal:
```
sudo apt-get -f install
```

that should be it.

---

### Post by Jayadheer on 2008-11-03
> **Circus-Killer said:**
> firstly, in case this package has unmet dependencies, you will need to have a working internet connection to do the install.

all you to do is go to your terminal and use:
```
sudo dpkg -i filename.deb
```

it will either tell you that it installed successfully, or display a bunch of errors. if it does display errors, then type in the terminal:
```
sudo apt-get -f install
```

that should be it.

Thanks alot

---

