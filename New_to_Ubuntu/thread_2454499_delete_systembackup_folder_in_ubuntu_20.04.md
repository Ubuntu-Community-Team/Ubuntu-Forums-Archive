---
title: "delete systembackup folder in ubuntu 20.04"
date: 2020-11-30
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-11-30
i have uninstalled systembackup using synaptic. however i cant delete the systemback folder which is in /.
i tried running the below in terminal
  cd /home
  ls
   rm -rf /Systemback

didnt work. any ideas/tks

---

### Post by CelticWarrior on 2020-11-30
Your user has no permissions in /. Knowing that, use 'sudo'.

---

### Post by rburkartjo on 2020-11-30
tks cel but didnt work
sudo rm -rf /Systemback

---

### Post by yancek on 2020-11-30
Didn't work doesn't help anyone to help you.  What is the result when you run the command you indicate, just go back to a prompt, get some error message?

---

### Post by tea for one on 2020-11-30
> **rburkartjo said:**
> tks cel but didnt work
sudo rm -rf /Systemback

```
cd /home
```
```
ls
```

Please post output of the last command in code tags

---

### Post by rbmorse on 2020-11-30
Directory names are case sensitive.

---

### Post by rburkartjo on 2020-11-30
tea
ay@ray-HP-Pavilion-Notebook:~$ cd /home
ray@ray-HP-Pavilion-Notebook:/home$ ls
ray  Systemback
ray@ray-HP-Pavilion-Notebook:/home$

---

### Post by rburkartjo on 2020-11-30
figured it out
ran this in terminal
sudo rm -r -f /home/Systemback

---

