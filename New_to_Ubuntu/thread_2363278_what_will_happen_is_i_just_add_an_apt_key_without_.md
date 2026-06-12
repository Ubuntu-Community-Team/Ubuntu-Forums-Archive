---
title: "what will happen is i just add an apt key without add apt repos first?"
date: 2017-06-08
forum: New to Ubuntu
---

### Post by 243750496 on 2017-06-08
i try to add the key using 
wget -qO - [http://dlang.org/d-keyring.gpg](http://dlang.org/d-keyring.gpg) | sudo apt-key add -



the quesiton happened when i delete the apt repository but added the key by mistake again , so i check whether the key is added?
then i typed several times to get it easily discovered .
but i see nothing added in apt-key am i wrong? or the key can't live with single add , unless the apt repository added at the same time?

---

### Post by howefield on 2017-06-08
What command are you using to list your keys ?

```
apt-key list
```

The key being there won't cause you any problems even without the repository information.

---

### Post by 243750496 on 2017-06-08
> **howefield said:**
> What command are you using to list your keys ?

```
apt-key list
```

The key being there won't cause you any problems even without the repository information.
sudo wget [http://master.dl.sourceforge.net/project/d-apt/files/d-apt.list](http://master.dl.sourceforge.net/project/d-apt/files/d-apt.list) -O /etc/apt/sources.list.d/d-apt.list
wget -qO - [http://dlang.org/d-keyring.gpg](http://dlang.org/d-keyring.gpg) | sudo apt-key add -

will the second command working if it is the only command i run.??
i mean will the apt-key add can working in single or must type together with the first one or it will not add the key???

---

