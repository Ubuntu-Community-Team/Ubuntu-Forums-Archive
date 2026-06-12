---
title: "command line update help"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-12-02
i forgot the command for requesting a safe update from the terminal and then installing it
i thought it was this

sudo aptitude update && sudo aptitude safe-upgrade

however the above is wrong . 

i want to check for safe updates and then install them all from one command/tks

note i dont want to check for or install any new distr grades

---

### Post by LowSky on 2011-12-02
```
sudo apt-get update && sudo apt-get upgrade
```

---

