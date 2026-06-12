---
title: "fatal: could not create work tree dir 'metasploit-framework'.: Permission denied"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by jagadeesh3 on 2013-12-25
i am following this guide .
```
http://www.darkoperator.com/installing-metasploit-in-ubunt/
```

i am doing this .
```
cd /opt
git clone https://github.com/rapid7/metasploit-framework.git
cd metasploit-framework
```

when i am doing 
```
git clone https://github.com/rapid7/metasploit-framework.git 
```
i am getting the following error 
```
fatal: could not create work tree dir 'metasploit-framework'.: Permission denied
```


total log

```
quantum@quantum-desktop:/$ cd ..
quantum@quantum-desktop:/$ cd /opt
quantum@quantum-desktop:/opt$ git clone https://github.com/rapid7/metasploit-framework.git
fatal: could not create work tree dir 'metasploit-framework'.: Permission denied
```


please help :)

---

### Post by steeldriver on 2013-12-25
The /opt directory is a system directory - owned by root. You won't be able to clone a git repo into there as a regular user, it will require administrator privileges (i.e. sudo).

---

